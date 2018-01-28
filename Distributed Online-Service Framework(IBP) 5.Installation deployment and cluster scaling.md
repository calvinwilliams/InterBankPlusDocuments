分布式联机服务技术框架(IBP)设计与实战（五、安装部署与集群伸缩）
=========================================

| 版本号 | 修订日期 | 修订人 | 内容 |
| --- | --- | --- | --- |
| 0.0.1.0 | 2018-01-28 | 厉华 | 创建 |

<!-- TOC -->

- [1. 安装部署](#1-安装部署)
    - [1.1. 初次部署](#11-初次部署)
        - [1.1.1. 部署日志归集节点](#111-部署日志归集节点)
            - [1.1.1.1. 初始化环境](#1111-初始化环境)
            - [1.1.1.2. 安装日志归集端](#1112-安装日志归集端)
        - [1.1.2. 部署注册节点](#112-部署注册节点)
            - [1.1.2.1. 初始化环境](#1121-初始化环境)
            - [1.1.2.2. 安装日志采集端](#1122-安装日志采集端)
            - [1.1.2.3. 安装注册中心](#1123-安装注册中心)
        - [1.1.3. 部署通讯节点](#113-部署通讯节点)
            - [1.1.3.1. 初始化环境](#1131-初始化环境)
            - [1.1.3.2. 安装日志采集端](#1132-安装日志采集端)
            - [1.1.3.3. 安装注册代理](#1133-安装注册代理)
            - [1.1.3.4. 安装通讯服务端平台（如果需要的话）](#1134-安装通讯服务端平台如果需要的话)
    - [1.2. 部署应用](#12-部署应用)
        - [1.2.1. 新增应用](#121-新增应用)
        - [1.2.2. 更新应用（立即自动推导下发模式）](#122-更新应用立即自动推导下发模式)
        - [1.2.3. 更新应用（批量自动推导下发模式）](#123-更新应用批量自动推导下发模式)
        - [1.2.4. 删除应用](#124-删除应用)
    - [1.3. 注册节点其它管理](#13-注册节点其它管理)
        - [1.3.1. 注册中心](#131-注册中心)
        - [1.3.2. 通讯节点集群管理](#132-通讯节点集群管理)
    - [1.4. 编译配置文件](#14-编译配置文件)
    - [1.5. 用户自定义KV配置](#15-用户自定义kv配置)
- [2. 可执行程序参考](#2-可执行程序参考)
    - [2.1. 注册中心主程序](#21-注册中心主程序)
    - [2.2. 注册代理主程序](#22-注册代理主程序)
    - [2.3. 通讯服务端平台主程序](#23-通讯服务端平台主程序)
    - [2.4. 远程命令代理主程序](#24-远程命令代理主程序)
    - [2.5. 日志收集器](#25-日志收集器)
    - [2.6. 模拟发起IBP交易测试程序](#26-模拟发起ibp交易测试程序)
- [3. 脚本参考](#3-脚本参考)
    - [3.1. 注册中心管理脚本](#31-注册中心管理脚本)
    - [3.2. 注册代理管理脚本](#32-注册代理管理脚本)
    - [3.3. 注册代理集群管理脚本](#33-注册代理集群管理脚本)
    - [3.4. 通讯服务端平台管理脚本](#34-通讯服务端平台管理脚本)
    - [3.5. 通讯服务端平台集群管理脚本](#35-通讯服务端平台集群管理脚本)
    - [3.6. 版本打包脚本](#36-版本打包脚本)
    - [3.7. 集群分发脚本](#37-集群分发脚本)
    - [3.8. 版本解包脚本](#38-版本解包脚本)
    - [3.9. TM函数耗时日志解释脚本](#39-tm函数耗时日志解释脚本)
    - [3.10. 日志清理脚本](#310-日志清理脚本)
    - [3.11. 日志归档脚本](#311-日志归档脚本)
    - [3.12. 删除日志归档脚本](#312-删除日志归档脚本)
    - [3.13. 日志解包脚本](#313-日志解包脚本)

<!-- /TOC -->

# 1. 安装部署

IBP集群配置对象实例层次如下：

* 多个通讯节点主机组成一个通讯节点，多个通讯节点组成IBP节点集群。通讯节点主机是最小运行实例，通讯节点是自动推导下发配置和应用包、交易负载均衡的最小单位。通讯节点是集群管理的最小启停单位。
* 交易码信息包含了交易中文描述、交易应用包（动态库）文件名、客户端通讯超时、服务端应用处理超时（可选）、默认通讯节点名。
* 项目信息其实是客户端通讯节点集、服务端通讯节点集、交易码集的关系信息。
* 用户自定义KV配置下挂在通讯节点下。

（以下均为手工安装部署流程，正在研发一键自动安装通讯节点伸缩集群，但基本流程不变）

## 1.1. 初次部署

规划示例：

| 节点类型 | 节点名 | 节点说明 | 用户名 | 地址 |
| --- | --- | --- |
| 日志节点 | IBLOG | 日志归集 | iblog | 158.1.0.55:10101 |
| 注册节点 | IBMS | 注册中心 | ibms | 158.1.0.54:16001 |
| 通讯节点 | ECIF | ECIF业务平台 | ecif | 158.1.0.56:18001 |
| 通讯节点 | ECIF | ECIF业务平台 | ecif | 158.1.0.57:18001 |
| 通讯节点 | ECIF | ECIF业务平台 | ecif | 158.1.0.58:18001 |
| 通讯节点 | CORE | 核心系统 | herons | 66.88.1.10:10601 |

### 1.1.1. 部署日志归集节点

#### 1.1.1.1. 初始化环境

**创建用户（需要root权限）**

```
# useradd iblog
# passwd iblog
```

**进入用户**

```
# su - iblog
$
```

**上传logpipe安装包后解开**

```
$ tar xvzf ibp-Linux-0.0.24.1-bin.tar.gz
$ tar xvzf logpipe-0.16.1-bin.tar.gz
```

**改名、引用、重载用户登录配置**

```
$ mv .bash_profile .profile
$ echo ". ~/shbin/ibp_profile.add" >>.profile
$ . ~/.profile
```

#### 1.1.1.2. 安装日志归集端

**编写日志归集端配置文件**

```
$ cat $HOME/etc/logpipe.conf
{
        "log" : 
        {
                "log_file" : "/tmp/iblog_logpipe_log.log" ,
                "log_level" : "WARN"
        } ,

        "inputs" : 
        [
                { "plugin":"so/logpipe-input-tcp.so" , "ip":"158.1.0.55" , "port":10101 }
        ] ,

        "outputs" : 
        [
                { "plugin":"so/logpipe-output-file.so" , "path":"/home/iblog/log" , "rotate_size":10000000 }
        ]
}
```

**启动日志归集端**

```
$ logpipe -f $HOME/etc/logpipe.conf
```

其它节点采集端发来的日志都会以相同文件名落到`/home/iblog/log/`

`logpipe`由一个管理进程和一个工作进程组成，想要停止时只要向管理进程发送TERM信号即可。

**设置定时清理任务**

周期性日志文件转档任务，每天23点55分执行一次：

```
55 23 * * * . $HOME/shbin/baklog >/tmp/iblog_baklog.stdout 2>&1
```

周期性清理日志转档包任务，每天3点0分执行一次：

```
0 3 * * * . $HOME/shbin/rmlogbak 30 >/tmp/iblog_rmlogbak.stdout 2>&1
```

### 1.1.2. 部署注册节点

#### 1.1.2.1. 初始化环境

**创建用户（需要root权限）**

```
# useradd ibms
# passwd ibms
```

**进入用户**

```
# su - ibms
$
```

**上传安装包后解开**

```
$ tar xvzf ibp-Linux-0.0.24.1-bin.tar.gz
$ tar xvzf logpipe-0.16.1-bin.tar.gz
```

**改名、引用、重载用户登录配置**

```
$ mv .bash_profile .profile
$ echo ". ~/shbin/ibp_profile.add" >>.profile
$ . ~/.profile
```

**初始化ibms环境（检查创建目录、自动生成缺省配置文件）**

```
$ ibms -a init
mkdir /home/ibms/etc ok
/home/ibms/etc/ibms.conf created
/home/ibms/etc/ibp_nodes.conf created
/home/ibms/etc/ibp_apps.conf created
/home/ibms/etc/ibp_projects.conf created
mkdir /home/ibms/log ok
mkdir /home/ibms/file ok
mkdir /home/ibms/so ok , don't forget copy .so files in it
mkdir /home/ibms/keys ok , don't forget generate keys
$ l
drwxrwxr-x 2 ibms ibms    4096 04-05 15:56 bin
drwxr-xr-x 2 ibms ibms    4096 04-05 15:54 etc
drwxrwxr-x 2 ibms ibms    4096 04-05 15:56 exsh
drwxr-xr-x 2 ibms ibms    4096 04-05 15:32 file
-rw-rw-r-- 1 ibms ibms 1001633 04-05 15:56 ibp-Linux-0.0.24.1-bin.tar.gz
drwxr-xr-x 2 ibms ibms    4096 04-05 15:32 keys
drwxrwxr-x 2 ibms ibms    4096 04-05 15:56 lib
drwxr-xr-x 2 ibms ibms    4096 04-05 16:00 log
drwxrwxr-x 2 ibms ibms    4096 04-05 15:56 shbin
drwxr-xr-x 2 ibms ibms    4096 04-05 15:32 so
$ l etc/
-rw-rw-r-- 1 ibms ibms 605 04-05 15:32 ibms.conf
-rw-rw-r-- 1 ibms ibms 167 04-05 15:32 ibp_apps.conf
-rw-rw-r-- 1 ibms ibms 129 04-05 15:32 ibp_nodes.conf
-rw-rw-r-- 1 ibms ibms 146 04-05 15:32 ibp_projects.conf
```

`ibms.conf`是注册中心主配置文件，`ibp_nods.conf`是集群配置通讯节点配置文件，`ibp_apps.conf`是集群配置交易码配置文件，`ibp_projects.conf`是集群配置项目信息配置文件，以上配置文件格式均为JSON。

#### 1.1.2.2. 安装日志采集端

**编写日志采集端配置文件**

```
$ cat $HOME/etc/logpipe.conf
{
        "log" : 
        {
                "log_file" : "/tmp/ibms_logpipe_log.log" ,
                "log_level" : "WARN"
        } ,

        "inputs" : 
        [
                { "plugin":"so/logpipe-input-file.so" , "path":"/home/ecif/log" , "rotate_size":10000000 , "exec_after_rotating":"rm -f ${LOGPIPE_ROTATING_NEW_FILENAME}" }
        ] ,

        "outputs" : 
        [
                { "plugin":"so/logpipe-output-tcp.so" , "ip":"158.1.0.55","port":10101 }
        ]
}
```

**启动日志采集端**

```
$ logpipe -f $HOME/etc/logpipe.conf
```

`/home/iblog/log/`里新增日志或现存日志追加内容会被异步实时采集传输到日志归集端，日志文件到达10MB会被清除。

`logpipe`由一个管理进程和一个工作进程组成，想要停止时只要向管理进程发送TERM信号即可。

**设置定时清理任务**

周期性日志文件转档任务，每天23点55分执行一次：

```
55 23 * * * . $HOME/shbin/baklog >/tmp/ibms_baklog.stdout 2>&1
```

周期性清理日志转档包任务，每天3点0分执行一次：

```
0 3 * * * . $HOME/shbin/rmlogbak 30 >/tmp/ibms_rmlogbak.stdout 2>&1
```

#### 1.1.2.3. 安装注册中心

**修改注册中心配置文件**

```
{
	"ibms" :
	{
		"server" : // 服务器配置
		{
			"ip" : "158.1.0.54" ,
			"port" : 16001
		} ,
		
		"config" : // IBP集群配置文件名
		{
			"nodes_conf" : "ibp_nodes.conf" , // 通讯节点信息配置文件名
			"apps_conf" : "ibp_apps.conf" , // 交易码信息配置文件名
			"projects_conf" : "ibp_projects.conf" // 项目信息配置文件名
		} ,
		
        "security" : // 安全机制配置
        {
            "old_key_disable_elapse" : 120 , // 老密钥失效时间（单位：秒）
            "new_key_enable_elapse" : 60 // 新密钥生效时间（单位：秒）
        } ,

        "misc" : // 杂项配置
        {
            "auto_download_bin_enable" : 0 , // 是否启用立即自动推导下发应用包
			"second_config_dump" : "158.1.0.55:26001" // 冗余落地配置副本的ibcmd地址
        } ,

		"log" : // ibms日志配置
		{
			"iblog_server" : "" , // 该选项已弃用，改用logpipe实现大小转档和异步实时日志收集
			"event_output" : "file::log/event.log" , // 事件日志文件名
			"main_output" : "file::log/ibms_main.log" , // 启动初始化日志文件名
			"main_loglevel" : DEBUG , // 启动初始化日志等级
			"monitor_output" : "file::log/ibms_monitor.log" , // 注册中心父进程日志文件名
			"monitor_loglevel" : INFO , // 注册中心父进程日志等级
			"worker_output" : "file::log/ibms_worker.log" , // 注册中心子进程日志文件名
			"worker_loglevel" : INFO // 注册中心子进程日志等级
		}
	}
}
```

**启动注册中心**

```
$ ibms.sh start
ibms start ok
ibms      6745     1  0 15:58 pts/15   00:00:00 ibms -f ibms.conf -a start
ibms      6746  6745  0 15:58 pts/15   00:00:00 ibms -f ibms.conf -a start
```

注册中心由一个管理（父）进程和一个工作进程（子）组成，管理进程日志文件是`log/ibms_monitor.log`，工作进程日志文件是`log/ibms_worker.log`。

想要停止注册中心，只要向管理进程发送TERM信号即可，也可用单实例管理脚本`ibms.sh stop`。

### 1.1.3. 部署通讯节点

（以ecif@158.1.0.56:18001为例）

#### 1.1.3.1. 初始化环境

**创建用户（需要root权限）**

```
# useradd ecif
# passwd ecif
```

**进入用户**

```
# su - ecif
$
```

**上传安装包后解开**

```
$ tar xvzf ibp-Linux-0.0.24.1-bin.tar.gz
$ tar xvzf logpipe-0.16.1-bin.tar.gz
```

**改名、引用、重载用户登录配置**

```
$ mv .bash_profile .profile
$ echo ". ~/shbin/ibp_profile.add" >>.profile
$ . ~/.profile
```

**初始化ibma环境（检查创建目录、自动生成缺省配置文件）**

```
$ ibma -a init
mkdir /home/ecif/etc ok
/home/ecif/etc/ibma.conf created
mkdir /home/ecif/log ok
mkdir /home/ecif/file ok
mkdir /home/ecif/so ok , don't forget copy .so files in it
mkdir /home/ecif/keys ok , don't forget generate keys
$ l
drwxrwxr-x 2 ecif ecif    4096 04-05 16:06 bin
drwxr-xr-x 2 ecif ecif    4096 04-05 16:08 etc
drwxrwxr-x 2 ecif ecif    4096 04-05 16:06 exsh
drwxr-xr-x 2 ecif ecif    4096 04-05 16:08 file
-rw-rw-r-- 1 ecif ecif 1001633 04-05 16:06 ibp-Linux-0.0.24.1-bin.tar.gz
drwxr-xr-x 2 ecif ecif    4096 04-05 16:08 keys
drwxrwxr-x 2 ecif ecif    4096 04-05 16:06 lib
drwxr-xr-x 2 ecif ecif    4096 04-05 16:08 log
drwxrwxr-x 2 ecif ecif    4096 04-05 16:06 shbin
drwxr-xr-x 2 ecif ecif    4096 04-05 16:08 so
$ l etc/
-rw-rw-r-- 1 ecif ecif 476 04-05 16:08 ibma.conf

```

`ibma.conf`是注册中心主配置文件，配置文件格式为JSON。

#### 1.1.3.2. 安装日志采集端

**编写日志采集端配置文件**

```
$ cat $HOME/etc/logpipe.conf
{
        "log" : 
        {
                "log_file" : "/tmp/ibms_logpipe_log.log" ,
                "log_level" : "WARN"
        } ,

        "inputs" : 
        [
                { "plugin":"so/logpipe-input-file.so" , "path":"/home/ecif/log" , "rotate_size":10000000 , "exec_after_rotating":"rm -f ${LOGPIPE_ROTATING_NEW_FILENAME}" }
        ] ,

        "outputs" : 
        [
                { "plugin":"so/logpipe-output-tcp.so" , "ip":"158.1.0.55","port":10101 }
        ]
}
```

**启动日志采集端**

```
$ logpipe -f $HOME/etc/logpipe.conf
```

`/home/iblog/log/`里新增日志或现存日志追加内容会被异步实时采集传输到日志归集端，日志文件到达10MB会被清除。

`logpipe`由一个管理进程和一个工作进程组成，想要停止时只要向管理进程发送TERM信号即可。

**设置定时清理任务**

周期性日志文件转档任务，每天23点55分执行一次：

```
55 23 * * * . $HOME/shbin/baklog >/tmp/ibms_baklog.stdout 2>&1
```

周期性清理日志转档包任务，每天3点0分执行一次：

```
0 3 * * * . $HOME/shbin/rmlogbak 30 >/tmp/ibms_rmlogbak.stdout 2>&1
```

#### 1.1.3.3. 安装注册代理

**修改注册代理配置文件**

```
{
        "ibma" :
        {
                "this_node" : "ECIF" , // 本节点名

                "comm" :
                {
                        "min_compress_size" : 16 // 当HTTP体大于该大小时自动启用压缩
                } ,

                "log" :
                {
                        "iblog_server" : "" ,
                        "event_output" : "file::log/event.log" ,
                        "main_output" : "file::log/ibma_ECIF_127.0.0.1:18111_main.log" ,
                        "main_loglevel" : INFO ,
                        "worker_output" : "file::log/ibma_ECIF_127.0.0.1:18111_worker.log" ,
                        "worker_loglevel" : INFO
                }
        } ,

        "ibac" :
        {
				"connecting_timeout" : 10 // 客户端连接(connect)服务端超时时间（单位：秒）
                "retry_connect_timeval" : 60 , // 当连接失败后暂禁时间段（单位：秒）
        } ,

        "ibms" :
        {
                "server" :
                {
                        "ip" : "158.1.0.54" , // 注册中心IP
                        "port" : 16001 // 注册中心PORT
                }
        }
}
```

**生成通讯密钥**

$ cd ~/keys
$ ibpgenrsakeys ECIF
$ l
-rw-rw-r-- 1 ecif ECIF 1191 04-05 16:44 ECIF.prikey
-rw-rw-r-- 1 ECIF ECIF  270 04-05 16:44 ECIF.pubkey

注意：`ibpgenrsakeys`必须在`$HOME/keys/`目录里执行。

**在注册中心注册该节点主机**

```
$ ibms -a add_node --node ECIF
OK
$ ibms -a add_node_host --node ECIF --ip 158.1.0.56 --port 18001
OK
```

注意：如果该节点主机只做通讯客户端，port设为`-18001`。

**在通讯节点启动注册代理**

```
$ ibma.sh start
ibma start ok
ecif   9554     1  0 16:51 pts/16   00:00:00 ibma -f ibma.conf -a start
```

注册代理由一个工作进程组成，进程日志文件是`log/ibma_worker.log`。

想要停止注册代理，只要向工作进程发送TERM信号即可，也可用单实例管理脚本`ibma.sh stop`。

**在注册中心自动推导下发配置变动通知（主要通知关联节点）**

```
$ ibms -s changed_nodes
ECIF
$ ibms -a distribute_config
OK
```

#### 1.1.3.4. 安装通讯服务端平台（如果需要的话）

**初始化通讯服务端平台环境**

```
$ ibas -a init
WARN : /home/ecif/etc exist !
/home/ecif/etc/ibas.conf created
WARN : /home/ecif/log exist !
WARN : /home/ecif/file exist !
WARN : /home/ecif/so exist !
WARN : /home/ecif/keys exist !
$ l etc/
-rw-rw-r-- 1 ecif ecif 476 04-05 16:08 ibma.conf
-rw-rw-r-- 1 ecif ecif 864 04-05 17:34 ibas.conf
```

`ibas.conf`是通讯服务端平台主配置文件，格式为JSON。

**修改通讯服务端平台主配置文件**

```
{
        "ibas" :
        {
                "server" : // 服务端侦听地址
                {
                        "ip" : "158.1.0.56" , // 通讯服务端侦听IP
                        "port" : 18001 // 通讯服务端侦听PORT
                } ,
                "mpm" : // 多进程控制
                {
                        "mode" : "STATIC_WORKERPOOL" , /* FORK,STATIC_WORKERPOOL,DYNAMIC_WORKERPOOL */ // 服务模式：分别是 即时创建短工作进程、静态工作进程池、动态工作进程池
                        "max_count" : 10 , // 最大工作进程数量 或 静态保持工作进程数量
                        "DYNAMIC_WORKERPOOL" :
                        {
                                "min_idle_count" : 1 , // 最小空闲状态工作进程数量（动态进程池时有效）
                                "max_idle_count" : 5 , // 最大空闲状态工作进程数量（动态进程池时有效）
                                "create_interval" : 1 , // 每调整周期最大创建工作进程数量（动态进程池时有效）
                                "destroy_interval" : 10 , // 每调整周期最大销毁工作进程数量（动态进程池时有效）
                                "max_process_count" : 10000 // 每个工作进程处理多少交易后自动重启，以释放应用泄露的系统资源，保持工作进程健康
                        }
                } ,
				"security" : // 安全控制
				{
						"sign_flag" : 1 , // 与客户端握手时，建议双方业务报文是否签名
						"compress_flag" : 1 , // 与客户端握手时，建议双方业务报文是否压缩
						"encrypt_flag" : 1 // 与客户端握手时，建议双方业务报文是否加密 
				} ,
                "app" : // 应用包选项
                {
                        "max_so_cache_count" : 1000 // 应用包打开句柄缓存池最大缓存数量，采用LRU踢出使用最少的应用包打开句柄缓存
                } ,
                "log" : // 日志配置
                {
                        "iblog_server" : "" ,
                        "event_output" : "file::log/event.log" ,
                        "main_output" : "file::log/ibas_158.1.0.56-18001_main.log" ,
                        "main_loglevel" : DEBUG ,
                        "monitor_output" : "file::log/ibas_158.1.0.56-18001_monitor.log" ,
                        "monitor_loglevel" : INFO ,
                        "worker_output" : "file::log/ibas_158.1.0.56-18001_worker_%d.log" ,
                        "worker_loglevel" : INFO ,
                        "app_output" : "file::log/app_%s.log" ,
                        "app_loglevel" : INFO
                }
        } ,

        "ibma" :
        {
                "config_filename" : "ibma.conf" // 本地注册代理主配置文件，用于连接配置共享内存
        }
}
```

**启动通讯服务端平台**

```
$ ibas.sh start
ibas start ok
ecif   9554     1  0 16:51 pts/16   00:00:00 ibas -f ibas.conf -a start
ecif   9869 9554  0 16:51 pts/16   00:00:00 ibas -f ibas.conf -a start
ecif   9871 9554  0 16:51 pts/16   00:00:00 ibas -f ibas.conf -a start
ecif   9886 9554  0 16:51 pts/16   00:00:00 ibas -f ibas.conf -a start
...
```

通讯服务端平台由一个管理进程（父）和一组工作进程（子）组成，管理进程日志文件是`log/ibas_monitor.log`，工作进程日志文件是`log/ibas_worker_(数字).log`。

想要停止通讯服务端平台，只要向管理进程发送TERM信号即可，也可用单实例管理脚本`ibas.sh stop`。

## 1.2. 部署应用

（以ecif@158.1.0.56:18001为例）

### 1.2.1. 新增应用

**上传应用包**

```
$ scp ABCD0001.so ibms@158.1.0.54:~/so
```

**新增交易码配置**

```
$ ibms -a add_app --app ABCD0001 --desc "交易中文描述" --bin ABCD0001.so --timeout 60
OK
```

`timeout`是客户端通讯超时（单位：秒），`timeout2`是服务端应用超时（单位：秒），如果不设置的话则由`timeout`乘以`1.5`默认计算。`--server-node (server_node)`是缺省服务端节点名用于配置代替代码指定。

**新增或更新项目信息**

如果新增项目

```
$ ibms -a add_project --project "(项目英文名)" --server-nodes "ECIF" --client-nodes "CORE" --apps "ABCD0001"
```

如果项目已存在

```
$ ibms -a set_project --project "(项目英文名)" --server-nodes "ECIF" --client-nodes "CORE" --apps "(已有交易码集) ABCD0001"
```

**提交改动，自动推导出所有关联节点并下发**

```
$ ibms -a distribute_config
```

**保存配置到配置文件**

```
$ ibms -a save_config
```

### 1.2.2. 更新应用（立即自动推导下发模式）

如果注册中心启用了立即自动推导下发模式，即配置`misc/auto_download_bin_enable 1`。

**上传应用包**

```
$ scp ABCD0002.so ibms@158.1.0.54:~/so
```

注册中心监控`$HOME/so/`目录，一旦有应用包新增或发生变动则立即推导出关联节点并下发。如果找不到交易码配置则忽略。

### 1.2.3. 更新应用（批量自动推导下发模式）

**上传应用包**

```
$ scp ABCD0002.so ibms@158.1.0.54:~/so
```

**设置交易码更新标志**

```
$ ibms -a update_app --app "ABCD0002"
```

**确认自动推导结果变动了哪些节点**

```
$ ibms -s cnodes_changed
```

**批量下发配置和应用包**

```
$ ibms -a distribute_config
```

### 1.2.4. 删除应用

**删除交易码信息**

```
$ ibms -a remove_app --app ABCD0003
```

**确认自动推导结果变动了哪些节点**

```
$ ibms -s cnodes_changed
```

**批量下发配置和应用包**

```
$ ibms -a distribute_config
```

## 1.3. 注册节点其它管理

### 1.3.1. 注册中心

**重启注册中心**

```
$ ibms.sh restart
```

**列表所有通讯节点配置**

```
$ ibms -s nodes
```

**列表所有交易码配置**

```
$ ibms -s apps
```

**列表所有项目配置**

```
$ ibms -s projects
```

**列表已连接注册代理和通讯服务端平台会话**

```
$ ibms -s sessions
```

**强制下发配置和应用包某一通讯节点主机集群**

当自动推导有问题时，可使用指定节点名的强制下发。

```
$ ibms -a download_config --node (node)
```

**一键自动安装通讯节点扩大集群**

（正在研发中）

**一键自动安装通讯节点缩小集群**

（正在研发中）

### 1.3.2. 通讯节点集群管理

集群管理配置文件在`$HOME/etc/ibp_cluster.conf`，每行格式为`(节点名) (IP) (系统用户名)`。

**下发最新版安装包到集群**

```
$ ibp_distribute.sh (ibp-Linux-x.x.x.x-bin.tar.gz)
```

**集群解开最新版安装包**

```
$ ibma_cluster.sh ALL execmd ibp_unpack.sh (ibp-Linux-x.x.x.x-bin.tar.gz)
```

**重启集群中所有注册代理**

```
$ ibma_cluster.sh ALL restart
```

**重启集群中指定通讯节点的注册代理**

```
$ ibma_cluster.sh (node) restart
```

**优雅重启集群中所有通讯服务端平台**

```
$ ibas_cluster.sh ALL restart_graceful
```

**优雅重启集群中指定通讯节点的服务端平台**

```
$ ibas_cluster.sh (node) restart_graceful
```

## 1.4. 编译配置文件

当注册中心的通讯节点等配置文件很大时，启动加载将耗费很多解析时间，IBP引入编译配置文件机制，预先读入解析配置，吐出内存映像到二进制文件，再启动装载配置时发现有预编译二进制配置文件则从其装载，大大加快装载性能，缩短启动时间。

以下命令预先读入解析配置，吐出内存映像到二进制文件

```
$ ibms -a build_config
```

## 1.5. 用户自定义KV配置

每个通讯节点里的应用可能需要自己的配置，比如连接硬件加密机型号、IP、PORT，IBP在集群配置中加入了通讯节点KV配置机制，替代应用自己管理篇日志的一大套麻烦事儿（如重载），只需在注册中心配置通讯节点下的KV配置，随着集群配置一起下发给通讯节点，通讯节点里的应用通过注册代理API即可直接访问这些配置。

```
$ ibms -a set_node_kv --node (node) --key (key) --value (value)
```

**确认自动推导结果变动了哪些节点**

```
$ ibms -s cnodes_changed
```

**批量下发配置和应用包**

```
$ ibms -a distribute_config
```

# 2. 可执行程序参考

## 2.1. 注册中心主程序

不带任何参数执行ibms可得到所有参数列表

```
SAGE : ibms -f ibms.conf -a start
                          -s sessions
                          -s nodes
                          -a add_node --node (node) [ --invalid (invalid) ] [ --key-exp (key_exp) ]
                          -a set_node --node (node) [ --invalid (invalid) ] [ --key-exp (key_exp) ]
                          -a remove_node --node (node)
                          -a add_node_host --node (node) --ip (ip) --port (port)
                          -a remove_node_host --node (node) --ip (ip) --port (port)
                          -s apps
                          -a add_app --app (app) --desc (desc) --bin (bin) --timeout (timeout) [ --timeout2 (timeout2) ] [ --invalid (invalid) ] [ --server-node (server_node) ]
                          -a set_app --app (app) --desc (desc) --bin (bin) --timeout (timeout) [ --timeout2 (timeout2) ] [ --invalid (invalid) ] [ --server-node (server_node) ]
                          -a update_app --app (app)
                          -a remove_app --app (app)
                          -s projects
                          -a add_project --project (project) --server-nodes (server_nodes) --client-nodes (client_nodes) --apps (apps)
                          -a set_project --project (project) --server-nodes (server_nodes) --client-nodes (client_nodes) --apps (apps)
                          -a remove_project --project (project)
                          -a save_config
                          -s nodes_kv
                          -a add_node_kv --node (node) --key (key) --value (value)
                          -a remove_node_kv --node (node) --key (key) --value (value)
                          -a set_node_kv --node (node) --key (key) --value (value)
                          -a distribute_config
                          -a download_config --node (node)
                          -s nodes_changed
                          -a build_config
                          -a init
kill -USR1 (pid) : reload log output
kill -USR2 (pid) : reload nodes,apps,projects config
```

* -f 指定主配置文件名
* -a start 启动
* -s sessions 显示所有已建立连接（包含ibms client、ibma）
* -s nodes 显示所有已配置通讯节点信息
* -a add_node 新增通讯节点信息
* -a set_node 修改通讯节点信息
* -a remove_node 删除通讯节点信息
* -a add_node_host 新增通讯节点主机信息
* -a remove_node_host 删除通讯节点主机信息
* -s apps 显示所有已配置交易码信息
* -a add_app 新增交易码信息
* -a set_app 修改交易码信息
* -a remove_app 删除交易码信息
* -s projects 显示所有已配置项目信息
* -a add_project 新增项目信息
* -a set_project 修改项目信息
* -a remove_project 删除项目信息
* -a save_config   保存配置信息到文件
* -s nodes_kv 显示节点KV信息
* -a add_node_kv增加节点KV信息
* -a remove_node_kv 删除节点KV信息
* -a set_node_kv 修改节点KV信息
* -a distribute_config 全部下发配置
* -a build_config 生成.bin
* -s nodes_changed 显示所有已修改配置涉及通讯节点列表
* -a commit_config 下发所有已修改配置
* -a download_config 强制下发指定通讯节点所有配置
* -a init 初始化注册中心配置文件
* kill TERM (pid) 退出
* kill -USR1 (pid) 重载日志配置
* kill -USR2 (pid) 重载所有配置（未实现）

## 2.2. 注册代理主程序

不带任何参数执行ibma可得到所有参数列表

```
USAGE : ibma -f ibma.conf -a [ start | start_cleanly ]
                          -s this_node
                          -s [ nodes | apps | nodes_kv ]
                          -a init
kill -USR1 : reload log
kill -USR2 : stop with removing config space
```

* -f 指定主配置文件名
* -a start 启动
* -a start_cleanly 干净的启动（启动时清理所有存在的索引、配置共享内存；慎用）
* -s this_node显示本通讯节点名
* -s nodes 显示本地配置共享内的所有通讯节点信息
* -s apps显示本地配置共享内的所有交易码信息
* -s nodes_kv显示本地配置共享内的所有key-value信息
* -a init 初始化注册代理配置文件
* kill -TERM (pid) 退出
* kill -USR1 (pid) 重载日志配置
* kill -USR2 (pid) 干净的退出（退出时清理所有索引、配置共享内存；慎用）

## 2.3. 通讯服务端平台主程序

不带任何参数执行ibas可得到所有参数列表

```
USAGE : ibas -f ibas.conf -a start
                          -s status
                          -s bbstat
                          -s bbdetail
                          -a init
```

* -f 指定主配置文件名
* -a start 启动
* -s status 显示服务端状态
* -s bbstat 显示进程池统计信息
* -s bbdetail 显示进程池明细信息
* -a init 初始化通讯服务端配置文件
* kill TERM (pid) 退出
* kill -USR1 (pid) 重载日志配置

## 2.4. 远程命令代理主程序

```
USAGE : ibcmd -a start
              --ip (ip) --port (port) -a execmd --cmd (cmd)
              --ip (ip) --port (port) -a putfile --file (file)
              --ip (ip) --port (port) -a getfile --file (file)
```

* -a start 启动服务端
* --ip (ip) --port (port) -a execmd --cmd (cmd) 作为客户端连接服务端远程执行命令，捕获输出
* --ip (ip) --port (port) -a putfile --file (file) 作为客户端连接服务端远程执行命令，推送文件
* --ip (ip) --port (port) -a getfile --file (file) 作为客户端连接服务端远程执行命令，拉取文件

## 2.5. 日志收集器

不带任何参数执行logpipe可得到所有参数列表

```
USAGE : logpipe -v
        logpipe -f (config_file) [ --no-daemon ] [ --start-once-for-env "(key) (value)" ]
```

* -v 显示当前版本号
* -f 指定配置文件
* --no-daemon 不转换为守护进程
* --start-once-for-env "(key) (value)" 设置为环境变量传递给插件，启动后只传递一次，如插件自然重启或崩溃后重启初始化时不会收到该环境变量，特别用于`logpipe-input-file`插件启动时全量采集一次。

## 2.6. 模拟发起IBP交易测试程序

不带任何参数执行ibpsend可得到所有参数列表

```
USAGE : ibpsend node app req_msg_filename [ req_file_filename1 [ req_file_filename2 [ req_file_filename3 [ req_file_filename4 ] ] ] ]

NOTE : req_file_filename format "(file_id)_(filename).(ext)"
```

* node: 目标节点
* app: 请求交易码
* req_msg_filename: 请求文件名(请求文件必须存在)
* req_file_filename1:请求文件1(可选)
* req_file_filename2:请求文件2(可选)
* req_file_filename3:请求文件3(可选)
* req_file_filename4:请求文件4(可选)

# 3. 脚本参考

## 3.1. 注册中心管理脚本

不带任何参数执行ibms.sh可得到所有参数列表

```
USAGE : ibms.sh [ status | start | stop | kill | restart | reload_log | show_nodes | show_apps | show_projects ]
```

* status 查询状态
* start 启动
* stop 停止
* kill 强制停止
* restart 重启
* reload_log 重载日志配置
* show_nodes显示所有已配置通讯节点信息
* show_apps显示所有已配置交易码信息
* show_projects显示所有已配置项目信息

## 3.2. 注册代理管理脚本

不带任何参数执行可得到所有参数列表

```
USAGE : ibma.sh [ status | start | start_cleanly | stop | stop_cleanly | kill | restart | reload_log | this_node | nodes | apps ]
```

* status 查询状态
* start 启动
* start_cleanly 干净的启动，会清理残存的索引共享内存和配置共享内存
* stop 停止
* stop_cleanly 干净的停止，会清理残存的索引共享内存和配置共享内存
* kill 强制停止
* restart 重启
* reload_log 重载日志配置
* this_node显示本通讯节点名


## 3.3. 注册代理集群管理脚本

不带任何参数执行可得到所有参数列表

```
USAGE : ibma_cluster.do [ (node) | ALL ] [ start | start_cleanly | stop | stop_cleanly | kill | status | cmd (cmd) ]
```

* start 启动集群
* start_cleanly 干净的启动集群，会清理残存的索引共享内存和配置共享内存
* stop 停止集群
* stop_cleanly 干净的停止集群，会清理残存的索引共享内存和配置共享内存
* kill 强制停止集群
* status 查询集群状态
* cmd (cmd) 执行其它自定义命令

## 3.4. 通讯服务端平台管理脚本

不带任何参数执行可得到所有参数列表

```
USAGE : ibas.sh [ status | start | stop | kill | restart | restart_graceful | reload_log ]
```

* status 查询状态
* start 启动
* stop 停止
* kill 强制停止
* restart 重启
* restart_graceful 优雅重启
* reload_log 重载日志配置

## 3.5. 通讯服务端平台集群管理脚本

不带任何参数执行可得到所有参数列表

```
USAGE : ibas_cluster.do [ (node) | ALL ] [ start | stop | kill | status | cmd (cmd) ]
```

* start 启动集群
* stop 停止集群
* kill 强制停止集群
* status 查询集群状态
* cmd (cmd) 执行其它自定义命令

## 3.6. 版本打包脚本

必须在`$HOME/`执行

**打执行包**

```
$ ibp_pack_bin.sh
```

**打开发包**

```
$ ibp_pack_dev.sh
```

## 3.7. 集群分发脚本

```
$ ibp_distribute.sh (当前目录里的文件名)
```

## 3.8. 版本解包脚本

解包本机当前目录里的压缩包（可执行文件会先删除目标文件再解包）。

```
$ ibp_unpack.sh (当前目录里的文件名)
```

一般与集群管理脚本配合使用。

## 3.9. TM函数耗时日志解释脚本

```
USAGE : ibp_perfmstat.sh [ @FILENAME | (string) ]
```

## 3.10. 日志清理脚本

删除`$HOME/log/`里的所有日志文件`*.log*`。

```
USAGE : rmlog
```

## 3.11. 日志归档脚本

移动打包`$HOME/log/*.log*`到`$HOME/logbak/`里。

```
USAGE : baklog
```

## 3.12. 删除日志归档脚本

按保留天数清理`$HOME/logbak/`里的日志备份包。

```
USAGE : rmlogbak [ days ]
```

* days 保留天数

一般与crontab配合使用。

## 3.13. 日志解包脚本

```
USAGE : gunziplogbak [ .gz.tar patten ]
```

* .gz.tar 日志备份包
* patten 文件名匹配字符串
