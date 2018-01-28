分布式联机服务技术框架(IBP)设计与实战（六、开发接口参考）
=========================================

| 版本号 | 修订日期 | 修订人 | 内容 |
| --- | --- | --- | --- |
| 0.0.1.0 | 2018-01-28 | 厉华 | 创建 |

<!-- TOC -->

- [1. API接口](#1-api接口)
    - [1.1. 公共API接口](#11-公共api接口)
        - [1.1.1. 文件类](#111-文件类)
            - [1.1.1.1. IBPCreateTempFile](#1111-ibpcreatetempfile)
    - [1.2. 注册代理API接口](#12-注册代理api接口)
        - [1.2.1. 环境类](#121-环境类)
            - [1.2.1.1. IBMAOpenConfigSpace](#1211-ibmaopenconfigspace)
            - [1.2.1.2. IBMACheckConfigSpaceAttaching](#1212-ibmacheckconfigspaceattaching)
            - [1.2.1.3. IBMACloseConfigSpace](#1213-ibmacloseconfigspace)
            - [1.2.1.4. IBMAGetConfigSpaceAttaching](#1214-ibmagetconfigspaceattaching)
            - [1.2.1.5. IBMAGetThisNodePtr](#1215-ibmagetthisnodeptr)
            - [1.2.1.6. IBMAGetRetryConnectTimeval](#1216-ibmagetretryconnecttimeval)
            - [1.2.1.7. IBMAGetMinCompressSize](#1217-ibmagetmincompresssize)
            - [1.2.1.8. IBMAGetIbmsServerIp](#1218-ibmagetibmsserverip)
            - [1.2.1.9. IBMAGetIbmsServerPort](#1219-ibmagetibmsserverport)
        - [1.2.2. 通讯节点类](#122-通讯节点类)
            - [1.2.2.1. IBMAGetNodeCount](#1221-ibmagetnodecount)
            - [1.2.2.2. IBMAGetThisNode](#1222-ibmagetthisnode)
            - [1.2.2.3. IBMATravelNodes](#1223-ibmatravelnodes)
            - [1.2.2.4. IBMAQueryNode](#1224-ibmaquerynode)
            - [1.2.2.5. IBMAGetNodePtr](#1225-ibmagetnodeptr)
            - [1.2.2.6. IBMAGetNodeInvalid](#1226-ibmagetnodeinvalid)
            - [1.2.2.7. IBMAGetNodeHostCount](#1227-ibmagetnodehostcount)
            - [1.2.2.8. IBMAGetNodeEncryptKeyExpPtr](#1228-ibmagetnodeencryptkeyexpptr)
            - [1.2.2.9. IBMAGetNodeOldKeyDisableTimestamp](#1229-ibmagetnodeoldkeydisabletimestamp)
            - [1.2.2.10. IBMAGetNodeNewKeyEnableTimestamp](#12210-ibmagetnodenewkeyenabletimestamp)
        - [1.2.3. 通讯节点主机集群类](#123-通讯节点主机集群类)
            - [1.2.3.1. IBMATravelNodeHosts](#1231-ibmatravelnodehosts)
            - [1.2.3.2. IBMAQueryNodeHost](#1232-ibmaquerynodehost)
            - [1.2.3.3. IBMAGetHostIpPtr](#1233-ibmagethostipptr)
            - [1.2.3.4. IBMAGetHostPort](#1234-ibmagethostport)
            - [1.2.3.5. IBMAGetHostLoad](#1235-ibmagethostload)
            - [1.2.3.6. IBMASetHostLoad](#1236-ibmasethostload)
            - [1.2.3.7. IBMAGetHostInvalid](#1237-ibmagethostinvalid)
            - [1.2.3.8. IBMAGetHostRetryConnectTimestamp](#1238-ibmagethostretryconnecttimestamp)
        - [1.2.4. 交易码信息类](#124-交易码信息类)
            - [1.2.4.1. IBMAGetAppCount](#1241-ibmagetappcount)
            - [1.2.4.2. IBMATravelApps](#1242-ibmatravelapps)
            - [1.2.4.3. IBMAQueryApp](#1243-ibmaqueryapp)
            - [1.2.4.4. IBMAGetAppPtr](#1244-ibmagetappptr)
            - [1.2.4.5. IBMAGetAppDescPtr](#1245-ibmagetappdescptr)
            - [1.2.4.6. IBMAGetAppBinPtr](#1246-ibmagetappbinptr)
            - [1.2.4.7. IBMAGetAppTimeout](#1247-ibmagetapptimeout)
            - [1.2.4.8. IBMAGetAppTimeout2](#1248-ibmagetapptimeout2)
            - [1.2.4.9. IBMAGetAppServerNodePtr](#1249-ibmagetappservernodeptr)
        - [1.2.5. 应用自定义KV配置类](#125-应用自定义kv配置类)
            - [1.2.5.1. IBMATravelNodeKvs](#1251-ibmatravelnodekvs)
            - [1.2.5.2. IBMAQueryNodekv](#1252-ibmaquerynodekv)
            - [1.2.5.3. IBMAGetKvKeyPtr](#1253-ibmagetkvkeyptr)
            - [1.2.5.4. IBMAGetKvValuePtr](#1254-ibmagetkvvalueptr)
            - [1.2.5.5. IBMAGetNodeKvCount](#1255-ibmagetnodekvcount)
    - [1.3. 通讯客户端API接口](#13-通讯客户端api接口)
        - [1.3.1. 环境类](#131-环境类)
            - [1.3.1.1. IBACCreateEnvirment](#1311-ibaccreateenvirment)
            - [1.3.1.2. IBACDestroyEnvirment](#1312-ibacdestroyenvirment)
            - [1.3.1.3. IBACCreateMultiEnvirments](#1313-ibaccreatemultienvirments)
            - [1.3.1.4. IBACDestroyMultiEnvirments](#1314-ibacdestroymultienvirments)
        - [1.3.2. 请求类（中层）](#132-请求类中层)
            - [1.3.2.1. IBACRequester](#1321-ibacrequester)
        - [1.3.3. 请求类（低层）](#133-请求类低层)
            - [1.3.3.1. IBACConnect](#1331-ibacconnect)
            - [1.3.3.2. IBACSendRequestAndReceiveResponse](#1332-ibacsendrequestandreceiveresponse)
            - [1.3.3.3. IBACDisconnect](#1333-ibacdisconnect)
            - [1.3.3.4. IBACMultiConnect](#1334-ibacmulticonnect)
            - [1.3.3.5. IBACMultiSendRequestsAndReceiveResponses](#1335-ibacmultisendrequestsandreceiveresponses)
            - [1.3.3.6. IBACMultiSendCommitOrRollbackAndReceiveResponses](#1336-ibacmultisendcommitorrollbackandreceiveresponses)
            - [1.3.3.7. IBACMultiDisconnect](#1337-ibacmultidisconnect)
    - [1.4. 通讯服务端API接口](#14-通讯服务端api接口)
        - [1.4.1. 信息查询类](#141-信息查询类)
            - [1.4.1.1. IBASGetThisNode](#1411-ibasgetthisnode)
            - [1.4.1.2. IBASGetThisApp](#1412-ibasgetthisapp)
            - [1.4.1.3. IBASSendResponseAhead](#1413-ibassendresponseahead)
            - [1.4.1.4. IBASGetClientNode](#1414-ibasgetclientnode)
            - [1.4.1.5. IBASGetClientIp](#1415-ibasgetclientip)
            - [1.4.1.6. IBASGetClientPort](#1416-ibasgetclientport)
            - [1.4.1.7. IBASGetCommJnlsno](#1417-ibasgetcommjnlsno)
            - [1.4.1.8. IBASGetThisAppCommTimeout](#1418-ibasgetthisappcommtimeout)
            - [1.4.1.9. IBASGetThisAppTimeout](#1419-ibasgetthisapptimeout)
            - [1.4.1.10. IBASGetWorkerIndex](#14110-ibasgetworkerindex)
            - [1.4.1.11. IBASGetWorkerProcessCount](#14111-ibasgetworkerprocesscount)
            - [1.4.1.12. IBASGetResponseBody](#14112-ibasgetresponsebody)
        - [1.4.2. 数据类](#142-数据类)
            - [1.4.2.1. IBASGetHttpEnv](#1421-ibasgethttpenv)
            - [1.4.2.2. IBASSetTransactionAddonInfo](#1422-ibassettransactionaddoninfo)
        - [1.4.3. 附带文件类](#143-附带文件类)
            - [1.4.3.1. IBASGetRequestFileCount](#1431-ibasgetrequestfilecount)
            - [1.4.3.2. IBASGetRequestFileById](#1432-ibasgetrequestfilebyid)
            - [1.4.3.3. IBASGetResponseFileCount](#1433-ibasgetresponsefilecount)
            - [1.4.3.4. IBASPutResponseFile](#1434-ibasputresponsefile)
            - [1.4.3.5. IBASGetPathFilename](#1435-ibasgetpathfilename)
            - [1.4.3.6. IBASGetEnv](#1436-ibasgetenv)
    - [1.5. 报文转换层API接口](#15-报文转换层api接口)
        - [1.5.1. 交易发起类](#151-交易发起类)
            - [1.5.1.1. IBMSGVSendRequestAndReceiveResponse_JSON](#1511-ibmsgvsendrequestandreceiveresponse_json)
            - [1.5.1.2. IBMSGVRequester_JSON](#1512-ibmsgvrequester_json)
            - [1.5.1.3. IBMSGVCall_JSON](#1513-ibmsgvcall_json)
        - [1.5.2. 交易接收类](#152-交易接收类)
            - [1.5.2.1. IBMSGVReceiver_JSON](#1521-ibmsgvreceiver_json)
            - [1.5.2.2. IBMSGVReceiver_JSON_SendResponseAhead](#1522-ibmsgvreceiver_json_sendresponseahead)
    - [1.6. 交易管理层API接口](#16-交易管理层api接口)
        - [1.6.1. 分阶段模板类](#161-分阶段模板类)
            - [1.6.1.1. IBTSExecuteSchedule_BT_PC_BP_AP_AT](#1611-ibtsexecuteschedule_bt_pc_bp_ap_at)
            - [1.6.1.2. IBTSRecursiveSchedule_BT_PC_BP_AP_AT](#1612-ibtsrecursiveschedule_bt_pc_bp_ap_at)
            - [1.6.1.3. IBTSExecuteSchedule_BT_PC_RI_BP_AP_AT](#1613-ibtsexecuteschedule_bt_pc_ri_bp_ap_at)
            - [1.6.1.4. IBTSRecursiveSchedule_BT_PC_BP_RI_AP_AT](#1614-ibtsrecursiveschedule_bt_pc_bp_ri_ap_at)
            - [1.6.1.5. IBTSExecuteSchedule_BT_PC_BP_AT__AP](#1615-ibtsexecuteschedule_bt_pc_bp_at__ap)
            - [1.6.1.6. IBTSRecursiveSchedule_BT_PC_BP_AP_AT](#1616-ibtsrecursiveschedule_bt_pc_bp_ap_at)
        - [1.6.2. 得到配置信息类](#162-得到配置信息类)
            - [1.6.2.1. IBTMGetFuncParaPtr](#1621-ibtmgetfuncparaptr)
        - [1.6.3. 设置响应信息类](#163-设置响应信息类)
            - [1.6.3.1. IBTMFormatResponseCode](#1631-ibtmformatresponsecode)
            - [1.6.3.2. IBTMFormatResponseCode](#1632-ibtmformatresponsecode)
            - [1.6.3.3. IBTMFormatResponseDesc](#1633-ibtmformatresponsedesc)
            - [1.6.3.4. IBTMFormatResponseInfo](#1634-ibtmformatresponseinfo)
        - [1.6.4. 结构体树类](#164-结构体树类)
            - [1.6.4.1. IBTMAppendStructBlock](#1641-ibtmappendstructblock)
            - [1.6.4.2. IBTMGetStructBlock](#1642-ibtmgetstructblock)
            - [1.6.4.3. IBTMAppendGetStructBlock](#1643-ibtmappendgetstructblock)
        - [1.6.5. 动态结构体类](#165-动态结构体类)
            - [1.6.5.1. DS_NEW](#1651-ds_new)
            - [1.6.5.2. DS_ADD](#1652-ds_add)
            - [1.6.5.3. DS_SET](#1653-ds_set)
            - [1.6.5.4. DS_GET](#1654-ds_get)
        - [1.6.6. 数据库操作类](#166-数据库操作类)
            - [1.6.6.1. OpenDatabaseSessions](#1661-opendatabasesessions)
            - [1.6.6.2. CloseDatabaseSessions](#1662-closedatabasesessions)
            - [1.6.6.3. BeginDatabaseTransaction](#1663-begindatabasetransaction)
            - [1.6.6.4. CommitDatabaseTransaction](#1664-commitdatabasetransaction)
            - [1.6.6.5. RollbackDatabaseTransaction](#1665-rollbackdatabasetransaction)
- [2. 代码示例](#2-代码示例)
    - [2.1. 公共API](#21-公共api)
        - [2.1.1. 创建临时文件](#211-创建临时文件)
    - [2.2. 通讯客户端API](#22-通讯客户端api)
        - [2.2.1. 发起通讯请求（中层）](#221-发起通讯请求中层)
        - [2.2.2. 发起通讯请求（中层）（附带文件）](#222-发起通讯请求中层附带文件)
        - [2.2.3. 发起通讯请求（低层）](#223-发起通讯请求低层)
    - [2.3. 通讯服务端API](#23-通讯服务端api)
        - [2.3.1. 回射服务](#231-回射服务)
        - [2.3.2. 回射服务（附带文件）](#232-回射服务附带文件)
    - [2.4. 报文转换API](#24-报文转换api)
    - [2.5. 动态结构容器](#25-动态结构容器)
    - [2.6. 分阶段管理层API](#26-分阶段管理层api)

<!-- /TOC -->

# 1. API接口

## 1.1. 公共API接口

### 1.1.1. 文件类

#### 1.1.1.1. IBPCreateTempFile

| | |
| ---:| --- |
| 函数原型： | FILE *IBPCreateTempFile( char *file_id , char *filename , char *pathfilename , char *mode ); |
| 函数描述： | 创建本地唯一附带临时文件 |
| 函数说明： | char *file_id 文件ID，用于前后台交换多个文件时指定文件用<br />char *filename 附带文件名；声明变量“char filename[ IBP_MAXLEN_FILENAME + 1 ] ;”；如果填为NULL，则函数返回时不填充<br />char *pathfilename 带路径的附带文件名；声明变量“char filename[ IBP_MAXLEN_FILENAME + 1 ] ;”；如果填为NULL，则函数返回时不填充<br />char *mode fopen打开模式，文本文件用"w"，二进制文件用"b" |
| 返回值： | 返回非NULL表示成功，值为打开FILE指针；返回NULL表示失败 |
| | |

## 1.2. 注册代理API接口

### 1.2.1. 环境类

#### 1.2.1.1. IBMAOpenConfigSpace

| | |
| ---:| --- |
| 函数原型： | struct IbmaConfigSpace *IBMAOpenConfigSpace( char *config_filename ); |
| 函数描述： | 打开配置共享内存 |
| 函数说明： | 从注册代理主配置文件config_filename得到配置共享内存key，申请配置共享内存句柄所需内存，打开配置共享内存，返回该句柄指针。<br />当config_filename为NULL时取缺省值"ibma.conf"。<br />config_filename不含路径，写死路径在"$HOME/etc"。 |
| 返回值： | 返回非NULL表示成功，值为打开句柄指针；返回NULL表示失败 |
| | |

#### 1.2.1.2. IBMACheckConfigSpaceAttaching

| | |
| ---:| --- |
| 函数原型： | int IBMACheckConfigSpaceAttaching( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 检查是否有新构建的配置共享内存，如果有则切换到新构建的 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄。 |
| 返回值： | 返回1表示切换配置共享内存；0表示成功；非0表示失败 |
| | |

#### 1.2.1.3. IBMACloseConfigSpace

| | |
| ---:| --- |
| 函数原型： | void IBMACloseConfigSpace( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 关闭配置共享内存打开句柄 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | （无） |
| | |

#### 1.2.1.4. IBMAGetConfigSpaceAttaching

| | |
| ---:| --- |
| 函数原型： | struct ConfigSpaceAttaching *IBMAGetConfigSpaceAttaching( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到配置空间首区结构指针 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 配置空间首区结构地址（只读） |
| | |

#### 1.2.1.5. IBMAGetThisNodePtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetThisNodePtr( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到自己通讯节点名 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回自己通讯节点名（只读） |
| | |

#### 1.2.1.6. IBMAGetRetryConnectTimeval

| | |
| ---:| --- |
| 函数原型： | int IBMAGetRetryConnectTimeval( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到暂禁时间配置 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回暂禁时间配置（只读） |
| | |

#### 1.2.1.7. IBMAGetMinCompressSize

| | |
| ---:| --- |
| 函数原型： | int IBMAGetMinCompressSize( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到最小压缩数据大小 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回最小压缩数据大小（只读）；当HTTP体数据大于等于该配置值时才激活压缩 |
| | |

#### 1.2.1.8. IBMAGetIbmsServerIp

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetIbmsServerIp( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到注册中心IP |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回注册中心IP（只读） |
| | |

#### 1.2.1.9. IBMAGetIbmsServerPort

| | |
| ---:| --- |
| 函数原型： | int IBMAGetIbmsServerPort( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到注册中心PORT |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回注册中心PORT（只读） |
| | |

### 1.2.2. 通讯节点类

#### 1.2.2.1. IBMAGetNodeCount

| | |
| ---:| --- |
| 函数原型： | int IBMAGetNodeCount( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到本地配置副本中的通讯节点数量（包含自己） |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回通讯节点数量 |
| | |

#### 1.2.2.2. IBMAGetThisNode

| | |
| ---:| --- |
| 函数原型： | struct NodeSpaceUnit *IBMAGetThisNode( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到自己通讯节点结构信息，需要通过其它函数获取属性 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回自己通讯节点结构信息（只读） |
| | |

#### 1.2.2.3. IBMATravelNodes

| | |
| ---:| --- |
| 函数原型： | struct NodeSpaceUnit *IBMATravelNodes( struct IbmaConfigSpace *ibma_config_space , struct NodeSpaceUnit *p_node_unit ); |
| 函数描述： | 遍历本地配置副本中所有通讯节点结构信息，需要通过其它函数获取属性 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />struct NodeSpaceUnit *p_node_unit 上一次遍历值，第一次设置为NULL |
| 返回值： | 返回每次遍历的通讯节点结构信息（只读） |
| | |

#### 1.2.2.4. IBMAQueryNode

| | |
| ---:| --- |
| 函数原型： | struct NodeSpaceUnit *IBMAQueryNode( struct IbmaConfigSpace *ibma_config_space , char *node ); |
| 函数描述： | 查询本地配置副本中指定名字的通讯节点结构信息，需要通过其它函数获取属性 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />char *node 指定通讯节点名 |
| 返回值： | 返回指定名字的通讯节点结构信息（只读） |
| | |

#### 1.2.2.5. IBMAGetNodePtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetNodePtr( struct NodeSpaceUnit *p_node_unit ); |
| 函数描述： | 从通讯节点结构信息中获取节点名 |
| 函数说明： | struct NodeSpaceUnit *p_node_unit 通讯节点结构信息 |
| 返回值： | 返回节点名（只读） |
| | |

#### 1.2.2.6. IBMAGetNodeInvalid

| | |
| ---:| --- |
| 函数原型： | char IBMAGetNodeInvalid( struct NodeSpaceUnit *p_node_unit ); |
| 函数描述： | 从通讯节点结构信息中获取节点是否被禁用 |
| 函数说明： | struct NodeSpaceUnit *p_node_unit 通讯节点结构信息 |
| 返回值： | 返回0表示该节点可用，返回非0表示该节点禁用 |
| | |

#### 1.2.2.7. IBMAGetNodeHostCount

| | |
| ---:| --- |
| 函数原型： | int IBMAGetNodeHostCount( struct NodeSpaceUnit *p_node_unit ); |
| 函数描述： | 从通讯节点结构信息中获取节点的主机集群数量 |
| 函数说明： | struct NodeSpaceUnit *p_node_unit 通讯节点结构信息 |
| 返回值： | 返回主机集群数量 |
| | |

#### 1.2.2.8. IBMAGetNodeEncryptKeyExpPtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetNodeEncryptKeyExpPtr( struct NodeSpaceUnit *p_node_unit ) |
| 函数描述： | 从通讯节点结构信息中获取节点的通讯节点密钥 |
| 函数说明： | struct NodeSpaceUnit *p_node_unit 通讯节点结构信息 |
| 返回值： | 返回通讯节点密钥 |
| | |

#### 1.2.2.9. IBMAGetNodeOldKeyDisableTimestamp

| | |
| ---:| --- |
| 函数原型： | int IBMAGetNodeOldKeyDisableTimestamp( struct NodeSpaceUnit *p_node_unit ) |
| 函数描述： | 从通讯节点结构信息中获取节点的旧密钥失效时间戳 |
| 函数说明： | struct NodeSpaceUnit *p_node_unit 通讯节点结构信息 |
| 返回值： | 返回旧密钥失效时间戳 |
| | |

#### 1.2.2.10. IBMAGetNodeNewKeyEnableTimestamp

| | |
| ---:| --- |
| 函数原型： | int IBMAGetNodeNewKeyEnableTimestamp( struct NodeSpaceUnit *p_node_unit ) |
| 函数描述： | 从通讯节点结构信息中获取节点的新密钥生效时间戳 |
| 函数说明： | struct NodeSpaceUnit *p_node_unit 通讯节点结构信息 |
| 返回值： | 返回新密钥生效时间戳 |
| | |

### 1.2.3. 通讯节点主机集群类

#### 1.2.3.1. IBMATravelNodeHosts

| | |
| ---:| --- |
| 函数原型： | struct HostSpaceUnit *IBMATravelNodeHosts( struct IbmaConfigSpace *ibma_config_space , struct NodeSpaceUnit *p_node_unit , struct HostSpaceUnit *p_host_unit ); |
| 函数描述： | 遍历本地配置副本中的指定通讯节点的主机信息 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />struct NodeSpaceUnit *p_node_unit 通讯节点结构信息<br />struct HostSpaceUnit *p_host_unit 上一次主机信息结构指针，第一次设置为NULL |
| 返回值： | 遍历指定通讯节点的主机信息 |
| | |

#### 1.2.3.2. IBMAQueryNodeHost

| | |
| ---:| --- |
| 函数原型： | struct HostSpaceUnit *IBMAQueryNodeHost( struct IbmaConfigSpace *ibma_config_space , struct NodeSpaceUnit *p_node_unit , char *ip , int port ); |
| 函数描述： | 查询指定通讯节点的主机信息结构 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />struct NodeSpaceUnit *p_node_unit 通讯节点结构信息<br />char *ip 主机IP<br />int port 主机PORT |
| 返回值： | 查询指定通讯节点的主机信息 |
| | |

#### 1.2.3.3. IBMAGetHostIpPtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetHostIpPtr( struct HostSpaceUnit *p_host_unit ); |
| 函数描述： | 得到主机信息结构中的IP |
| 函数说明： | struct HostSpaceUnit *p_host_unit主机结构信息 |
| 返回值： | 主机信息结构IP |
| | |

#### 1.2.3.4. IBMAGetHostPort

| | |
| ---:| --- |
| 函数原型： | int IBMAGetHostPort( struct HostSpaceUnit *p_host_unit ); |
| 函数描述： | 得到主机信息结构中的PORT |
| 函数说明： | struct HostSpaceUnit *p_host_unit 主机结构信息 |
| 返回值： | 主机信息结构PORT |
| | |

#### 1.2.3.5. IBMAGetHostLoad

| | |
| ---:| --- |
| 函数原型： | int IBMAGetHostLoad( struct HostSpaceUnit *p_host_unit ); |
| 函数描述： | 得到主机信息结构中的当前负载 |
| 函数说明： | struct HostSpaceUnit *p_host_unit 主机结构信息 |
| 返回值： | 主机信息结构当前负载 |
| | |

#### 1.2.3.6. IBMASetHostLoad

| | |
| ---:| --- |
| 函数原型： | void IBMASetHostLoad( struct HostSpaceUnit *p_host_unit , int load , int loop ); |
| 函数描述： | 设置主机信息结构中的当前负载 |
| 函数说明： | struct HostSpaceUnit *p_host_unit 主机结构信息<br />int load     负载值<br />int loop     是否循环标志 |
| 返回值： | 设置主机信息结构的负载 |
| | |

#### 1.2.3.7. IBMAGetHostInvalid

| | |
| ---:| --- |
| 函数原型： | char IBMAGetHostInvalid( struct HostSpaceUnit *p_host_unit ); |
| 函数描述： | 得到主机信息结构中的有效性 |
| 函数说明： | struct HostSpaceUnit *p_host_unit 主机结构信息 |
| 返回值： | 主机信息结构有效性 |
| | |

#### 1.2.3.8. IBMAGetHostRetryConnectTimestamp

| | |
| ---:| --- |
| 函数原型： | time_t IBMAGetHostRetryConnectTimestamp( struct HostSpaceUnit *p_host_unit ); |
| 函数描述： | 得到主机重连时间戳 |
| 函数说明： | struct HostSpaceUnit *p_host_unit 主机结构信息 |
| 返回值： | 主机重连时间戳 |
| | |

### 1.2.4. 交易码信息类

#### 1.2.4.1. IBMAGetAppCount

| | |
| ---:| --- |
| 函数原型： | int IBMAGetAppCount( struct IbmaConfigSpace *ibma_config_space ); |
| 函数描述： | 得到本地配置副本中的交易码数量（包含自己） |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄 |
| 返回值： | 返回交易码数量 |
| | |

#### 1.2.4.2. IBMATravelApps

| | |
| ---:| --- |
| 函数原型： | struct AppSpaceUnit *IBMATravelApps( struct IbmaConfigSpace *ibma_config_space , struct AppSpaceUnit *p_app_unit ); |
| 函数描述： | 遍历本地配置副本中所有交易码结构信息，需要通过其它函数获取属性 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />struct AppSpaceUnit *p_app_unit 上一次遍历值，第一次设置为NULL |
| 返回值： | 返回每次遍历的交易码结构信息（只读） |
| | |

#### 1.2.4.3. IBMAQueryApp

| | |
| ---:| --- |
| 函数原型： | struct AppSpaceUnit *IBMAQueryApp( struct IbmaConfigSpace *ibma_config_space , char *app ); |
| 函数描述： | 查询本地配置副本中指定名字的交易码结构信息，需要通过其它函数获取属性 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />char *app 指定交易码 |
| 返回值： | 返回指定名字的交易码结构信息（只读） |
| | |

#### 1.2.4.4. IBMAGetAppPtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetAppPtr( struct AppSpaceUnit *p_app_unit ); |
| 函数描述： | 得到交易码信息结构中的IP |
| 函数说明： | struct AppSpaceUnit *p_app_unit 交易码信息结构 |
| 返回值： | 交易码信息结构中的交易码 |
| | |

#### 1.2.4.5. IBMAGetAppDescPtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetAppDescPtr( struct AppSpaceUnit *p_app_unit ); |
| 函数描述： | 得到交易码信息结构中的描述 |
| 函数说明： | struct AppSpaceUnit *p_app_unit 交易码信息结构 |
| 返回值： | 交易码信息结构中的描述 |
| | |

#### 1.2.4.6. IBMAGetAppBinPtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetAppBinPtr( struct AppSpaceUnit *p_app_unit ); |
| 函数描述： | 得到交易码信息结构中的应用包名 |
| 函数说明： | struct AppSpaceUnit *p_app_unit 交易码信息结构 |
| 返回值： | 交易码信息结构中的应用包名 |
| | |

#### 1.2.4.7. IBMAGetAppTimeout

| | |
| ---:| --- |
| 函数原型： | int IBMAGetAppTimeout( struct AppSpaceUnit *p_app_unit ); |
| 函数描述： | 得到交易码信息结构中的超时值 |
| 函数说明： | struct AppSpaceUnit *p_app_unit 交易码信息结构 |
| 返回值： | 交易码信息结构中的超时值<br /> |
| | |

#### 1.2.4.8. IBMAGetAppTimeout2

| | |
| ---:| --- |
| 函数原型： | int IBMAGetAppTimeout2( struct AppSpaceUnit *p_app_unit ); |
| 函数描述： | 得到交易码信息结构中的timeout2值 |
| 函数说明： | struct AppSpaceUnit *p_app_unit 交易码信息结构 |
| 返回值： | 交易码信息结构中的timeout2值 |
| | |

#### 1.2.4.9. IBMAGetAppServerNodePtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetAppServerNodePtr( struct AppSpaceUnit *p_app_unit ); |
| 函数描述： | 得到交易码信息结构中的服务节点 |
| 函数说明： | struct AppSpaceUnit *p_app_unit 交易码信息结构 |
| 返回值： | 交易码信息结构中的服务节点 |
| | |

### 1.2.5. 应用自定义KV配置类

#### 1.2.5.1. IBMATravelNodeKvs

| | |
| ---:| --- |
| 函数原型： | struct KvSpaceUnit *IBMATravelNodeKvs( struct IbmaConfigSpace *ibma_config_space , struct KvSpaceUnit *p_kv_unit ); |
| 函数描述： | 遍历本地配置副本中的本节点的key-value信息 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />struct KvSpaceUnit * p_kv_unit 上一次key-value信息结构指针，第一次设置为NULL |
| 返回值： | 遍历本节点的key-value信息 |
| | |

#### 1.2.5.2. IBMAQueryNodekv

| | |
| ---:| --- |
| 函数原型： | struct KvSpaceUnit *IBMAQueryNodekv( struct IbmaConfigSpace *ibma_config_space , char *p_kv_key ); |
| 函数描述： | 查询本节点的key-value信息结构 |
| 函数说明： | struct IbmaConfigSpace *ibma_config_space 配置共享内存句柄<br />char *p_kv_key  key-value中key信息 |
| 返回值： | 查询本节点的key-value信息 |
| | |

#### 1.2.5.3. IBMAGetKvKeyPtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetKvKeyPtr( struct KvSpaceUnit *p_kv_unit ); |
| 函数描述： | 得到key-value信息结构中的key |
| 函数说明： | struct KvSpaceUnit * p_kv_unit   key-value结构信息 |
| 返回值： | key-value结构中的key |
| | |

#### 1.2.5.4. IBMAGetKvValuePtr

| | |
| ---:| --- |
| 函数原型： | char *IBMAGetKvValuePtr( struct KvSpaceUnit *p_kv_unit ); |
| 函数描述： | 得到key-value信息结构中的value |
| 函数说明： | struct KvSpaceUnit * p_kv_unit   key-value结构信息 |
| 返回值： | key-value结构中的value |
| | |

#### 1.2.5.5. IBMAGetNodeKvCount

| | |
| ---:| --- |
| 函数原型： | int IBMAGetNodeKvCount( struct NodeSpaceUnit *p_node_unit ); |
| 函数描述： | 得到本地配置副本中的key-value数量（包含自己） |
| 函数说明： | struct NodeSpaceUnit *p_node_unit通讯节点结构信息 |
| 返回值： | 返回本节点key-value信息 |
| | |

## 1.3. 通讯客户端API接口

### 1.3.1. 环境类

#### 1.3.1.1. IBACCreateEnvirment

| | |
| ---:| --- |
| 函数原型： | struct IbacApiEnv *IBACCreateEnvirment( char *config_filename ); |
| 函数描述： | 创建通讯客户端API环境 |
| 函数说明： | char *config_filename 注册代理主配置文件 |
| 返回值： | 成功则返回通讯客户端API环境，失败则返回NULL |
| | |

#### 1.3.1.2. IBACDestroyEnvirment

| | |
| ---:| --- |
| 函数原型： | void IBACDestroyEnvirment( struct IbacApiEnv *p_env ); |
| 函数描述： | 销毁通讯客户端API环境 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端API环境结构 |
| 返回值： | （无） |
| | |

#### 1.3.1.3. IBACCreateMultiEnvirments

| | |
| ---:| --- |
| 函数原型： | struct IbacMultiEnvs *IBACCreateMultiEnvirments( char *config_filename , int count ); |
| 函数描述： | 创建通讯客户端并行交易API环境 |
| 函数说明： | char *config_filename 注册代理主配置文件<br />int count 并行交易数量 |
| 返回值： | 成功则返回通讯客户端并行交易API环境，失败则返回NULL |
| | |

#### 1.3.1.4. IBACDestroyMultiEnvirments

| | |
| ---:| --- |
| 函数原型： | void IBACDestroyMultiEnvirments( struct IbacMultiEnvs *p_multi_envs ); |
| 函数描述： | 销毁通讯客户端并行交易API环境 |
| 函数说明： | struct IbacMultiEnvs *p_multi_env 通讯客户端并行交易API环境结构 |
| 返回值： | （无） |
| | |

### 1.3.2. 请求类（中层）

#### 1.3.2.1. IBACRequester

| | |
| ---:| --- |
| 函数原型： | int IBACRequester( struct IbacApiEnv *p_env , char *node , char *app , char **pp_msg , int *p_msg_len , ... ); |
| 函数描述： | 连接服务端，发送接收交易，断开服务 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端环境结构<br />char *node 服务端通讯节点名<br />char *app 交易码<br />char **pp_msg 输入时指向请求报文首地址的指针，输出时指向响应报文首地址的指针<br />int *p_msg_len 输入时存放请求报文大小，输出时存放响应报文大小<br />... 请求文件名字符串列表和响应文件名字符串列表（无请求响应文件时填"NULL,NULL"，有一个请求文件无响应文件时填"req_pathfilename,NULL,NULL"，无请求文件有一个响应文件时填"NULL,rsp_pathfilename,NULL"，同时又请求响应文件时填"req_pathfilename,NULL,rsp_pathfilename,NULL"），如果字符串为空则跳过 |
| 返回值： | 成功则0，失败则返回非0 |
| | |

### 1.3.3. 请求类（低层）

#### 1.3.3.1. IBACConnect

| | |
| ---:| --- |
| 函数原型： | int IBACConnect( struct IbacApiEnv *ibac_api_env , char *node ); |
| 函数描述： | 连接服务端主机 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端环境结构<br />char *node 服务端通讯节点名 |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.3.3.2. IBACSendRequestAndReceiveResponse

| | |
| ---:| --- |
| 函数原型： | int IBACSendRequestAndReceiveResponse( struct IbacApiEnv *ibac_api_env , char *app , char **pp_msg , int *p_msg_len , ... ); |
| 函数描述： | 发送请求到服务端主机并同步接收响应 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端环境结构<br />char *app 交易码<br />char **pp_msg 输入时指向请求报文首地址的指针，输出时指向响应报文首地址的指针<br />int *p_msg_len 输入时存放请求报文大小，输出时存放响应报文大小<br />... 请求文件名字符串列表和响应文件名字符串列表（无请求响应文件时填"NULL,NULL"，有一个请求文件无响应文件时填"req_pathfilename,NULL,NULL"，无请求文件有一个响应文件时填"NULL,rsp_pathfilename,NULL"，同时又请求响应文件时填"req_pathfilename,NULL,rsp_pathfilename,NULL"），如果字符串为空则跳过 |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.3.3.3. IBACDisconnect

| | |
| ---:| --- |
| 函数原型： | int IBACDisconnect( struct IbacApiEnv *ibac_api_env ); |
| 函数描述： | 断开服务端主机 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端环境结构 |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.3.3.4. IBACMultiConnect

| | |
| ---:| --- |
| 函数原型： | int IBACMultiConnect( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters ); |
| 函数描述： | 并行连接通讯服务端 |
| 函数说明： | struct IbacMultiEnvs *p_multi_envs通讯客户端并行交易API环境结构<br />struct IbacMultiRequesters *multi_requesters 并行交易配置 |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.3.3.5. IBACMultiSendRequestsAndReceiveResponses

| | |
| ---:| --- |
| 函数原型： | int IBACMultiSendRequestsAndReceiveResponses( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters ); |
| 函数描述： | 发送并行交易请求并接收响应 |
| 函数说明： | struct IbacMultiEnvs *p_multi_envs通讯客户端并行交易API环境结构<br />struct IbacMultiRequesters *multi_requesters 并行交易配置 |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.3.3.6. IBACMultiSendCommitOrRollbackAndReceiveResponses

| | |
| ---:| --- |
| 函数原型： | int IBACMultiSendCommitOrRollbackAndReceiveResponses( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters , int commit_or_rollback_flag ); |
| 函数描述： | 发送二阶段提交或回滚请求并接收响应 |
| 函数说明： | struct IbacMultiEnvs *p_multi_envs通讯客户端并行交易API环境结构<br />struct IbacMultiRequesters *multi_requesters 并行交易配置<br />int commit_or_rollback_flag 并行提交宏IBAC_MULTI_COMMIT_DATABASE 或 并行回滚宏IBAC_MULTI_ROLLBACK_DATABASE |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.3.3.7. IBACMultiDisconnect

| | |
| ---:| --- |
| 函数原型： | void IBACMultiDisconnect( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters ); |
| 函数描述： | 并行断开通讯服务端 |
| 函数说明： | struct IbacMultiEnvs *p_multi_envs通讯客户端并行交易API环境结构<br />struct IbacMultiRequesters *multi_requesters 并行交易配置 |
| 返回值： | （无） |
| | |

## 1.4. 通讯服务端API接口

### 1.4.1. 信息查询类

#### 1.4.1.1. IBASGetThisNode

| | |
| ---:| --- |
| 函数原型： | const char *IBASGetThisNode( struct IbasEnv *p_env ); |
| 函数描述： | 得到本通讯节点名 |
| 函数说明： | struct IbasEnv *p_env 通讯服务端环境结构 |
| 返回值： | 本通讯节点名（只读） |
| | |

#### 1.4.1.2. IBASGetThisApp

| | |
| ---:| --- |
| 函数原型： | const char *IBASGetThisApp( struct IbasEnv *p_env ); |
| 函数描述： | 得到当前交易码 |
| 函数说明： | struct IbasEnv *p_env 通讯服务端环境结构 |
| 返回值： | 当前交易码（只读） |
| | |

#### 1.4.1.3. IBASSendResponseAhead

| | |
| ---:| --- |
| 函数原型： | int IBASSendResponseAhead(); |
| 函数描述： | 提前发送响应 |
| 函数说明： | （无） |
| 返回值： | 0表示成功；非0表示失败 |
| | |

#### 1.4.1.4. IBASGetClientNode

| | |
| ---:| --- |
| 函数原型： | const char *IBASGetClientNode(); |
| 函数描述： | 得到客户端节点 |
| 函数说明： | （无） |
| 返回值： | 客户端节点 |
| | |

#### 1.4.1.5. IBASGetClientIp

| | |
| ---:| --- |
| 函数原型： | const char *IBASGetClientIp(); |
| 函数描述： | 得到客户端IP |
| 函数说明： | （无） |
| 返回值： | 客户端节点 |
| | |

#### 1.4.1.6. IBASGetClientPort

| | |
| ---:| --- |
| 函数原型： | const int  IBASGetClientPort() |
| 函数描述： | 得到客户端访问端口 |
| 函数说明： | （无） |
| 返回值： | 客户端访问端口 |
| | |

#### 1.4.1.7. IBASGetCommJnlsno

| | |
| ---:| --- |
| 函数原型： | const char *IBASGetCommJnlsno(); |
| 函数描述： | 得到客户端流水号 |
| 函数说明： | （无） |
| 返回值： | 客户端流水号 |
| | |

#### 1.4.1.8. IBASGetThisAppCommTimeout

| | |
| ---:| --- |
| 函数原型： | int IBASGetThisAppCommTimeout(); |
| 函数描述： | 得到客户端通讯超时时间 |
| 函数说明： | （无） |
| 返回值： | 通讯超时时间 |
| | |

#### 1.4.1.9. IBASGetThisAppTimeout

| | |
| ---:| --- |
| 函数原型： | int IBASGetThisAppTimeout(); |
| 函数描述： | 得到交易超时时间 |
| 函数说明： | （无） |
| 返回值： | 交易超时时间 |
| | |

#### 1.4.1.10. IBASGetWorkerIndex

| | |
| ---:| --- |
| 函数原型： | int IBASGetWorkerIndex(); |
| 函数描述： | 得到工作进程序号 |
| 函数说明： | （无） |
| 返回值： | 工作进程序号 |
| | |

#### 1.4.1.11. IBASGetWorkerProcessCount

| | |
| ---:| --- |
| 函数原型： | int IBASGetWorkerProcessCount(); |
| 函数描述： | 得到工作进程数目 |
| 函数说明： | （无） |
| 返回值： | 工作进程数目 |
| | |

#### 1.4.1.12. IBASGetResponseBody

| | |
| ---:| --- |
| 函数原型： | struct HttpBuffer *IBASGetResponseBody(); |
| 函数描述： | 得到响应报文体 |
| 函数说明： | （无） |
| 返回值： | 响应报文体 |
| | |

### 1.4.2. 数据类

#### 1.4.2.1. IBASGetHttpEnv

| | |
| ---:| --- |
| 函数原型： | struct HttpEnv *IBASGetHttpEnv( struct IbasEnv *p_env ); |
| 函数描述： | 得到HTTP协议环境 |
| 函数说明： | struct IbasEnv *p_env 通讯服务端环境结构 |
| 返回值： | HTTP协议环境 |
| | |

#### 1.4.2.2. IBASSetTransactionAddonInfo

| | |
| ---:| --- |
| 函数原型： | int IBASSetTransactionAddonInfo( char *busi_channel , char *busi_jnlsno , char *busi_transaction_code , long response_code , char *addon_text ); |
| 函数描述： | 设置交易响应信息 |
| 函数说明： | char *busi_channel   渠道号<br />char *busi_jnlsno     流水号<br />char *busi_transaction_code  业务交易码<br />long response_code 响应码<br />char *addon_text 附加信息 |
| 返回值： | 设置交易响应信息 |
| | |

### 1.4.3. 附带文件类

#### 1.4.3.1. IBASGetRequestFileCount

| | |
| ---:| --- |
| 函数原型： | int IBASGetRequestFileCount( struct IbasAddonFiles *addon_files ); |
| 函数描述： | 得到请求附带文件数量 |
| 函数说明： | struct IbasAddonFiles *addon_files 附带文件名容器 |
| 返回值： | 请求附带文件数量 |
| | |

#### 1.4.3.2. IBASGetRequestFileById

| | |
| ---:| --- |
| 函数原型： | char *IBASGetRequestFileById( struct IbasAddonFiles *addon_files , char *file_id ); |
| 函数描述： | 得到指定文件ID的请求附带文件名 |
| 函数说明： | struct IbasAddonFiles *addon_files 附带文件名容器<br />char *file_id |
| 返回值： | 指定文件ID的请求附带文件名 |
| | |

#### 1.4.3.3. IBASGetResponseFileCount

| | |
| ---:| --- |
| 函数原型： | int IBASGetResponseFileCount( struct IbasAddonFiles *addon_files ); |
| 函数描述： | 得到响应附带文件数量 |
| 函数说明： | struct IbasAddonFiles *addon_files 附带文件名容器 |
| 返回值： | 响应附带文件数量 |
| | |

#### 1.4.3.4. IBASPutResponseFile

| | |
| ---:| --- |
| 函数原型： | int IBASPutResponseFile( struct IbasAddonFiles *addon_files , char *filename ); |
| 函数描述： | 压入响应附带文件名 |
| 函数说明： | struct IbasAddonFiles *addon_files 附带文件名容器<br />char *file_id |
| 返回值： | 0表示成功；非0表示失败 |
| | |

#### 1.4.3.5. IBASGetPathFilename

| | |
| ---:| --- |
| 函数原型： | void IBASGetPathFilename( char *filename , char *pathfilename , int sizeof_pathfilename ); |
| 函数描述： | 给定附加文件名，返回追加绝对路径的附带文件名 |
| 函数说明： | char *filename 附加文件名<br />char *pathfilename 追加绝对路径的附带文件名<br />int sizeof_pathfilename 追加绝对路径的附带文件名缓冲区大小 |
| 返回值： | （无） |
| | |

#### 1.4.3.6. IBASGetEnv

| | |
| ---:| --- |
| 函数原型： | struct IbasEnv *IBASGetEnv(); |
| 函数描述： | 得到ibas主环境结构 |
| 函数说明： | （无） |
| 返回值： | ibas主环境结构 |
| | |

## 1.5. 报文转换层API接口

### 1.5.1. 交易发起类

#### 1.5.1.1. IBMSGVSendRequestAndReceiveResponse_JSON

| | |
| ---:| --- |
| 函数原型： | int IBMSGVSendRequestAndReceiveResponse_JSON( struct IbacEnv *p_env , char *app , void *pv_req_st , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , ... ); |
| 函数描述： | 打包JSON报文，发送接收通讯报文，解包JSON报文 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端环境结构<br />char *app 交易码<br />void *pv_req_st 请求结构体<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func打包JSON报文函数<br />void *pv_rsp_st 响应结构体<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func 解包JSON报文函数<br />... 请求文件名字符串列表和响应文件名字符串列表（具体见通讯客户端API） |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.5.1.2. IBMSGVRequester_JSON

| | |
| ---:| --- |
| 函数原型： | int IBMSGVRequester_JSON( struct IbacApiEnv *p_env , char *node , char *app , void *pv_req_st , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , ... ); |
| 函数描述： | 连接服务端，打包JSON报文，发送接收通讯报文，解包JSON报文，断开服务 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端环境结构<br />char *node 服务端通讯节点名<br />char *app 交易码<br />void *pv_req_st 请求结构体<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func打包JSON报文函数<br />void *pv_rsp_st 响应结构体<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func 解包JSON报文函数<br />... 请求文件名字符串列表和响应文件名字符串列表（具体见通讯客户端API） |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.5.1.3. IBMSGVCall_JSON

| | |
| ---:| --- |
| 函数原型： | int IBMSGVCall_JSON( struct IbacApiEnv *ibac_api_env , char *app , void *pv_req_st , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , ... ); |
| 函数描述： | 创建通讯客户端API环境，连接服务端，打包JSON报文，发送接收通讯报文，解包JSON报文，断开服务，销毁通讯客户端API环境 |
| 函数说明： | struct IbacApiEnv *p_env 通讯客户端环境结构<br />char *app 交易码<br />void *pv_req_st 请求结构体<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func打包JSON报文函数<br />void *pv_rsp_st 响应结构体<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func 解包JSON报文函数<br />... 请求文件名字符串列表和响应文件名字符串列表（具体见通讯客户端API） |
| 返回值： | 成功则0，失败则返回非0<br /> |
| | |

### 1.5.2. 交易接收类

#### 1.5.2.1. IBMSGVReceiver_JSON

| | |
| ---:| --- |
| 函数原型： | int IBMSGVReceiver_JSON( struct HttpBuffer *req_buf , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , void *pv_req_st , struct HttpBuffer *rsp_buf , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , funcIbmsgvTransmain *p_transmain_func , struct IbasAddonFiles *addon_files ); |
| 函数描述： | 解包JSON报文，调用回调函数transmain，打包JSON报文 |
| 函数说明： | struct HttpBuffer *req_buf 请求报文缓冲区<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func 解包JSON报文函数<br />void *pv_req_st 请求结构体<br />struct HttpBuffer *rsp_buf 响应报文缓冲区<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func 打包JSON报文函数<br />void *pv_rsp_st 响应结构体<br />funcIbmsgvTransmain *p_transmain_func 交易层入口回调函数<br />struct IbasAddonFiles *addon_files 请求和响应附带文件缓冲区，通过ibas_api函数存取 |
| 返回值： | 成功则0，失败则返回非0 |
| | |

#### 1.5.2.2. IBMSGVReceiver_JSON_SendResponseAhead

| | |
| ---:| --- |
| 函数原型： | int IBMSGVReceiver_JSON_SendResponseAhead<br />( DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st ); |
| 函数描述： | 打包JSON报文，通讯发送响应 |
| 函数说明： | DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func 打包JSON报文函数<br />void *pv_rsp_st 响应结构体 |
| 返回值： | 成功则0，失败则返回非0<br /> |
| | |

## 1.6. 交易管理层API接口

### 1.6.1. 分阶段模板类

#### 1.6.1.1. IBTSExecuteSchedule_BT_PC_BP_AP_AT

| | |
| ---:| --- |
| 函数原型： | int IBTSExecuteSchedule_BT_PC_BP_AP_AT( char *req_msg_name , int sizeof_req_msg , void *p_req_st , char *rsp_msg_name , int sizeof_rsp_msg , void *p_rsp_st , struct IbasAddonFiles *addon_files , char *trans_code , char *response_code , int response_code_bufsize , char *response_desc , int response_desc_bufsize , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList ,  struct TransSchedule_BT_PC_BP_AP_AT *p_ts ); |
| 函数描述： | 数据库事务（交易前处理）（如果报错跳到交易后处理），<br />数据库事务（公共检查）（如果报错跳到交易后处理），<br />数据库事务（业务检查、业务处理、账务处理）（如果报错跳到交易后处理），<br />数据库事务（交易后处理）（如果报错则结束） |
| 函数说明： | char *req_msg_name 请求结构体名称<br />int sizeof_req_msg 请求结构体大小<br />void *p_req_st 请求结构体<br />char *rsp_msg_name 响应结构体名称<br />int sizeof_rsp_msg 响应结构体大小<br />void *p_rsp_st 响应结构体<br />struct IbasAddonFiles *addon_files 请求和响应附带文件缓冲区<br />char *trans_code 业务交易码<br />char *response_code 响应码缓冲区<br />int response_code_bufsize 响应码缓冲区大小<br />char *response_desc 响应描述缓冲区<br />int response_desc_bufsize 响应描述缓冲区大小<br />TransFunc  *TF_HeaderMapping  填充translist结构函数(注: IB2和IB1填充TF_BT_InsertTransListHeaderMapping即可，IB1自定义)<br />TransFunc  *TF_InsertTransList  登记业务流水表函数<br />TransFunc  *TF_UpdateTransList  更新业务流水表函数<br />struct TransSchedule_BT_PC_BP_AP_AT *p_ts 分阶段模板配置 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.1.2. IBTSRecursiveSchedule_BT_PC_BP_AP_AT

| | |
| ---:| --- |
| 函数原型： | int IBTSRecursiveSchedule_BT_PC_BP_AP_AT( struct TransEnv *p_te , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList , struct TransSchedule_BT_PC_BP_AP_AT *p_ts );<br />	<br />	  |
| 函数描述： | 递归子交易分阶段模板 |
| 函数说明： | struct TransEnv *p_te 交易环境结构<br />struct TransSchedule_BT_PC_BP_AP_AT *p_ts 分阶段模板配置<br />TransFunc  *TF_HeaderMapping  填充translist结构函数(注: IB2和IB1填充TF_BT_InsertTransListHeaderMapping即可，IB1自定义)<br />TransFunc  *TF_InsertTransList  登记业务流水表函数<br />TransFunc  *TF_UpdateTransList  更新业务流水表函数<br /> |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.1.3. IBTSExecuteSchedule_BT_PC_RI_BP_AP_AT

| | |
| ---:| --- |
| 函数原型： | int IBTSExecuteSchedule_BT_PC_BP_RI_AP_AT( char *req_msg_name , int sizeof_req_msg , void *p_req_st , char *rsp_msg_name , int sizeof_rsp_msg , void *p_rsp_st , struct IbasAddonFiles *addon_files , char *trans_code , char *response_code , int response_code_bufsize , char *response_desc , int response_desc_bufsize , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList , struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts ); |
| 函数描述： | 数据库事务（交易前处理）（如果报错跳到交易后处理），<br />数据库事务（公共检查）（如果报错跳到交易后处理），<br />数据库事务（业务检查、请求联动交易、业务处理、账务处理）（如果报错跳到交易后处理），<br />数据库事务（交易后处理）（如果报错则结束） |
| 函数说明： | char *req_msg_name 请求结构体名称<br />int sizeof_req_msg 请求结构体大小<br />void *p_req_st 请求结构体<br />char *rsp_msg_name 响应结构体名称<br />int sizeof_rsp_msg 响应结构体大小<br />void *p_rsp_st 响应结构体<br />struct IbasAddonFiles *addon_files 请求和响应附带文件缓冲区<br />char *trans_code 业务交易码<br />char *response_code 响应码缓冲区<br />int response_code_bufsize 响应码缓冲区大小<br />char *response_desc 响应描述缓冲区<br />int response_desc_bufsize 响应描述缓冲区大小<br />TransFunc  *TF_HeaderMapping  填充translist结构函数(注: IB2和IB1填充TF_BT_InsertTransListHeaderMapping即可，IB1自定义)<br />TransFunc  *TF_InsertTransList  登记业务流水表函数<br />TransFunc  *TF_UpdateTransList  更新业务流水表函数<br />struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts 分阶段模板配置 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.1.4. IBTSRecursiveSchedule_BT_PC_BP_RI_AP_AT

| | |
| ---:| --- |
| 函数原型： | int IBTSRecursiveSchedule_BT_PC_BP_RI_AP_AT( struct TransEnv *p_te  , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList , struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts ); |
| 函数描述： | 递归子交易分阶段模板 |
| 函数说明： | struct TransEnv *p_te 交易环境结构<br />struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts 分阶段模板配置<br />TransFunc  *TF_HeaderMapping  填充translist结构函数(注: IB2和IB1填充TF_BT_InsertTransListHeaderMapping即可，IB1自定义)<br />TransFunc  *TF_InsertTransList  登记业务流水表函数<br />TransFunc  *TF_UpdateTransList  更新业务流水表函数 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.1.5. IBTSExecuteSchedule_BT_PC_BP_AT__AP

| | |
| ---:| --- |
| 函数原型： | int IBTSExecuteSchedule_BT_PC_BP_AT_AP( char *req_msg_name , int sizeof_req_msg , void *p_req_st , char *rsp_msg_name , int sizeof_rsp_msg , void *p_rsp_st , struct IbasAddonFiles *addon_files , char *trans_code , char *response_code , int response_code_bufsize , char *response_desc , int response_desc_bufsize , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList ,  struct TransSchedule_BT_PC_BP_AT_AP *p_ts ); |
| 函数描述： | 数据库事务（交易前处理）（如果报错跳到交易后处理），<br />数据库事务（公共检查）（如果报错跳到交易后处理），<br />数据库事务（交易后处理）（如果报错则结束），<br />数据库事务（业务检查、业务处理、账务处理）（如果报错则结束） |
| 函数说明： | char *req_msg_name 请求结构体名称<br />int sizeof_req_msg 请求结构体大小<br />void *p_req_st 请求结构体<br />char *rsp_msg_name 响应结构体名称<br />int sizeof_rsp_msg 响应结构体大小<br />void *p_rsp_st 响应结构体<br />struct IbasAddonFiles *addon_files 请求和响应附带文件缓冲区<br />char *trans_code 业务交易码<br />char *response_code 响应码缓冲区<br />int response_code_bufsize 响应码缓冲区大小<br />char *response_desc 响应描述缓冲区<br />int response_desc_bufsize 响应描述缓冲区大小<br />TransFunc  *TF_HeaderMapping  填充translist结构函数(注: IB2和IB1填充TF_BT_InsertTransListHeaderMapping即可，IB1自定义)<br />TransFunc  *TF_InsertTransList  登记业务流水表函数<br />TransFunc  *TF_UpdateTransList  更新业务流水表函数<br />struct TransSchedule_BT_PC_BP_AT_AP *p_ts 分阶段模板配置 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.1.6. IBTSRecursiveSchedule_BT_PC_BP_AP_AT

| | |
| ---:| --- |
| 函数原型： | int IBTSRecursiveSchedule_BT_PC_BP_AT_AP( struct TransEnv *p_te , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList ,  struct TransSchedule_BT_PC_BP_AT_AP *p_ts ); |
| 函数描述： | 递归子交易分阶段模板 |
| 函数说明： | struct TransEnv *p_te 交易环境结构<br />struct TransSchedule_BT_PC_BP_AT_AP *p_ts 分阶段模板配置<br />TransFunc  *TF_HeaderMapping  填充translist结构函数(注: IB2和IB1填充TF_BT_InsertTransListHeaderMapping即可，IB1自定义)<br />TransFunc  *TF_InsertTransList  登记业务流水表函数<br />TransFunc  *TF_UpdateTransList  更新业务流水表函数 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

### 1.6.2. 得到配置信息类

#### 1.6.2.1. IBTMGetFuncParaPtr

| | |
| ---:| --- |
| 函数原型： | char *IBTMGetFuncParaPtr( struct TransEnv *p_te ); |
| 函数描述： | 得到函数树配置中的函数参数 |
| 函数说明： | struct TransEnv *p_te 交易环境 |
| 返回值： | 返回函数树配置中的函数参数 |
| | |

### 1.6.3. 设置响应信息类

#### 1.6.3.1. IBTMFormatResponseCode

| | |
| ---:| --- |
| 函数原型： | int IBTMFormatResponseCode( struct TransEnv *p_te , int response_code ); |
| 函数描述： | 设置响应码到交易环境中的响应码字段（调用分阶段执行引擎指定）中 |
| 函数说明： | struct TransEnv *p_te 交易环境<br />int response_code 响应码 |
| 返回值： | 返回输入参数response_code的值 |
| | |

#### 1.6.3.2. IBTMFormatResponseCode

| | |
| ---:| --- |
| 函数原型： | int IBTMFormatResponseCode( struct TransEnv *p_te , int response_code ); |
| 函数描述： | 设置响应码到交易环境中的响应码字段（调用分阶段执行引擎指定）中 |
| 函数说明： | struct TransEnv *p_te 交易环境<br />int response_code 响应码 |
| 返回值： | 返回输入参数response_code的值 |
| | |

#### 1.6.3.3. IBTMFormatResponseDesc

| | |
| ---:| --- |
| 函数原型： | void IBTMFormatResponseDesc( struct TransEnv *p_te , char *response_desc_format , ... ); |
| 函数描述： | 设置响应描述到交易环境中的响应码字段（调用分阶段执行引擎指定）中 |
| 函数说明： | struct TransEnv *p_te 交易环境<br />char *response_desc_format , ... 响应描述可变参数列表 |
| 返回值： | （无） |
| | |

#### 1.6.3.4. IBTMFormatResponseInfo

| | |
| ---:| --- |
| 函数原型： | int IBTMFormatResponseInfo( struct TransEnv *p_te , int response_code , char *response_desc_format , ... ); |
| 函数描述： | 设置响应码和响应描述到交易环境中的响应码字段（调用分阶段执行引擎指定）中 |
| 函数说明： | struct TransEnv *p_te 交易环境<br />int response_code 响应码<br />char *response_desc_format , ... 响应描述可变参数列表 |
| 返回值： | 返回输入参数response_code的值 |
| | |

### 1.6.4. 结构体树类

#### 1.6.4.1. IBTMAppendStructBlock

| | |
| ---:| --- |
| 函数原型： | int IBTMAppendStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem ); |
| 函数描述： | 挂接一个结构体到结构体树中 |
| 函数说明： | struct TransEnv *p_te 交易环境<br />char *name 结构体名字（最长64字符）<br />long struct_size 结构体大小<br />void **ppmem 如果(*ppmem)==NULL则自动分配内存用以存放该结构体 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.4.2. IBTMGetStructBlock

| | |
| ---:| --- |
| 函数原型： | int IBTMGetStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem ); |
| 函数描述： | 从结构体树中获取一个结构体 |
| 函数说明： | struct TransEnv *p_te 交易环境<br />char *name 结构体名字（最长64字符）<br />long struct_size 结构体大小<br />void **ppmem 返回成功时，(*ppmem)指向该结构体 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.4.3. IBTMAppendGetStructBlock

| | |
| ---:| --- |
| 函数原型： | int IBTMAppendGetStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem ); |
| 函数描述： | 从结构体树中获取一个结构体，如果没有就挂接一个 |
| 函数说明： | struct TransEnv *p_te 交易环境<br />char *name 结构体名字（最长64字符）<br />long struct_size 结构体大小<br />void **ppmem如果(*ppmem)==NULL则自动分配内存用以存放该结构体 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

### 1.6.5. 动态结构体类

#### 1.6.5.1. DS_NEW

| | |
| ---:| --- |
| 宏使用示例： | DS      *ds = DS_NEW( "struct_name" ) ; |
| 函数描述： | 创建一个动态结构体。动态结构体用于在应用模块之间安全的交换数据 |
| 函数说明： | 动态结构体名称 |
| 返回值： | 成功则返回动态结构体，失败则返回NULL |
| | |

#### 1.6.5.2. DS_ADD

| | |
| ---:| --- |
| 宏使用示例： | DS_TRY(ds)<br />{       <br />        DS_ADD( ds , char , char_field , 0x30 ); <br />        DS_ADD( ds , int , int_field , 123 );<br />        DS_ADD( ds , long , long_field , 45678 );<br />        DS_ADD( ds , float , float_field , 123.0 );<br />        DS_ADD( ds , double , double_field , 456.789 );<br />        DS_ADD( ds , char* , string_field , "hello" );<br />}       <br />DS_CATCH(ds)<br />{       <br />        ERRORLOGG( "DS_ADD failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) )<br />        DS_DELETE ( ds );<br />        return -1;<br />}       |
| 函数描述： | 往动态结构体中添加变量字段并直接赋值 |
| 函数说明： | 动态结构体、变量类型、变量名、变量值 |
| 返回值： | 全部ADD成功则跳到DS_CATCH后面，有一个ADD失败则跳到DS_CATCH里面 |
| | |

#### 1.6.5.3. DS_SET

| | |
| ---:| --- |
| 宏使用示例： | DS_TRY(ds)<br />{       <br />        DS_SET( ds , char , char_field , 0x30 ); <br />        DS_SET( ds , int , int_field , 123 );<br />        DS_SET( ds , long , long_field , 45678 );<br />        DS_SET( ds , float , float_field , 123.0 );<br />        DS_SET( ds , double , double_field , 456.789 );<br />        DS_SET( ds , char* , string_field , "hello" );<br />}       <br />DS_CATCH(ds)<br />{       <br />        ERRORLOGG( "DS_SET failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) )<br />        DS_DELETE( ds );<br />        return -1;<br />} |
| 函数描述： | 设置值到动态结构体中的变量字段中 |
| 函数说明： | 动态结构体、变量类型、变量名、变量值 |
| 返回值： | 全部SET成功则跳到DS_CATCH后面，有一个SET失败则跳到DS_CATCH里面 |
| | |

#### 1.6.5.4. DS_GET

| | |
| ---:| --- |
| 宏使用示例： | DS_TRY(ds)<br />{       <br />        DS_GET( ds , char , char_field , ch ); <br />        DS_GET( ds , int , int_field , i );<br />        DS_GET( ds , long , long_field , l );<br />        DS_GET( ds , float , float_field , f );<br />        DS_GET( ds , double , double_field , d );<br />        DS_GET( ds , char* , string_field , buf , sizeof(buf) );<br />}       <br />DS_CATCH(ds)<br />{       <br />        ERRORLOGG( "DS_GET failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) )<br />        DS_DELETE( ds );<br />        return -1;<br />} |
| 函数描述： | 从动态结构体中的变量字段中提取值出来 |
| 函数说明： | 动态结构体、变量类型、变量名、变量值<br />当类型为字符串时，最后需要再加一个参数设置输出缓冲区大小 |
| 返回值： | 全部GET成功则跳到DS_CATCH后面，有一个GET失败则跳到DS_CATCH里面<br /> |
| | |

### 1.6.6. 数据库操作类

#### 1.6.6.1. OpenDatabaseSessions

| | |
| ---:| --- |
| 函数原型： | int OpenDatabaseSessions(); |
| 函数描述： | 打开数据库 |
| 函数说明： | 无 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.6.2. CloseDatabaseSessions

| | |
| ---:| --- |
| 函数原型： | int CloseDatabaseSessions(); |
| 函数描述： | 关闭数据库 |
| 函数说明： | 无 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.6.3. BeginDatabaseTransaction

| | |
| ---:| --- |
| 函数原型： | int BeginDatabaseTransaction(); |
| 函数描述： | 开始数据库事务 |
| 函数说明： | 无 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.6.4. CommitDatabaseTransaction

| | |
| ---:| --- |
| 函数原型： | int CommitDatabaseTransaction(); |
| 函数描述： | 提交数据库事务 |
| 函数说明： | 无 |
| 返回值： | 成功则返回0，失败则返回非0 |
| | |

#### 1.6.6.5. RollbackDatabaseTransaction

| | |
| ---:| --- |
| 函数原型： | int RollbackDatabaseTransaction(); |
| 函数描述： | 提交回滚数据库事务 |
| 函数说明： | 无 |

# 2. 代码示例

## 2.1. 公共API

### 2.1.1. 创建临时文件

```
	char	 	filename[ IBP_MAXLEN_FILENAME + 1 ] ;
	FILE		*fp = NULL ;
	
	fp = IBPCreateTempFile( "id" , filename , NULL , "w" ) ;
	if( fp == NULL )
	{
		printf( " IBPCreateTempFile failed , errno[%d]\n" , errno );
		return -1;
	}
	...
	fclose( fp );
	
	nret = IBASPutResponseFile( addon_files , filename ) ;
	if( nret )
	{
		printf( " IBASPutResponseFile failed , errno[%d]\n" , errno );
		return -1;
	}
```

## 2.2. 通讯客户端API

### 2.2.1. 发起通讯请求（中层）

test/test_ibpclient/ibp_test_echo/ibp_test_echo.c

```
#include "ibac_api.h"

int ibp_test_echo_IBACRequester( char *node , char *app , char *msg )
{
	struct IbacEnv		*p_env = NULL ;
	
	char			*p_msg = NULL ;
	int			msg_len ;
	
	int			nret = 0 ;
	
	/* 创建通讯客户端环境 */
	p_env = IBACCreateEnvirment( NULL ) ;
	if( p_env == NULL )
	{
		printf( "IBACCreateEnvirment failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		printf( "IBACCreateEnvirment ok\n" );
	}
	
	/* 连接通讯服务端，发送请求，接收响应，断开通讯服务端 */
	/* 向节点node发起交易app，p_msg指向请求报文，交易完成后，响应报文存放在通讯客户端环境中，p_msg指向它 */
	p_msg = msg ;
	msg_len = strlen(msg) ;
	nret = IBACRequester( p_env , node , app , & p_msg , & msg_len , NULL , NULL ) ;
	if( nret )
	{
		printf( "IBACRequester failed[%d] , errno[%d]\n" , nret , errno );
		return -1;
	}
	else
	{
		printf( "IBACRequester ok , msg[%.*s]\n" , msg_len , p_msg );
	}
	
	/* 销毁通讯客户端环境 */
	IBACDestroyEnvirment( p_env );
	printf( "IBACDestroyEnvirment ok\n" );
	
	return 0;
}

static void usage()
{
	printf( "USAGE : ibp_test_echo node app msg\n" );
	return;
}

int main( int argc , char *argv[] )
{
	int		nret = 0 ;
	
	if( argc == 1 + 3 )
	{
		IBPInitLogEnv( "" , "ibp_test_echo" , "file::log/event.log" , LOG_LEVEL_DEBUG , "file::log/ibp_test_echo.log" );
		nret = ibp_test_echo_IBACRequester( argv[1] , argv[2] , argv[3] ) ;
		IBPCleanLogEnv();
		return -nret;
	}
	else
	{
		usage();
		exit(7);
	}
}
```

test/test_ibpclient/ibp_test_echo/makefile

```
# 此文件由makeobj.sh自动生成
############################################################
# 项目名 : 
# 模块名 : 
# 备  注 : 
############################################################

###### 源文件配置区
#@ c_FILE
c_FILE		=	\
			ibp_test_echo.c \

###### 目标文件、安装目录配置区
include makeinstall
BIN		=	ibp_test_echo
BININST		=	$(_BININST)

###### 编译选项
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \

###### 链接选项
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libac_api

###### 额外宏定义区
CLEAN_ADDITION	=

###### 加载mktpl模板库
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_BININST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_BININST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### 目标文件依赖关系
ibp_test_echo		:	$(c_FILE_o)
	$(CC) -o $@ $(c_FILE_o) $(LFLAGS)
```

### 2.2.2. 发起通讯请求（中层）（附带文件）

test/test_ibpclient/ibp_test_file/ibp_test_file.c

```
#include "ibac_api.h"

static int ibp_test_file( char *node , char *msg )
{
	struct IbacEnv		*p_env = NULL ;
	FILE			*fp = NULL ;
	char			tmp_req_filename1[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			tmp_req_filename2[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			tmp_req_filename3[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			tmp_req_filename4[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			tmp_rsp_filename1[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			tmp_rsp_filename2[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			tmp_rsp_filename3[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			tmp_rsp_filename4[ IBP_MAXLEN_FILENAME + 1 ] ;
	char			*p_msg = NULL ;
	int			msg_len ;
	
	int			nret = 0 ;
	
	/* 创建通讯客户端环境 */
	p_env = IBACCreateEnvirment( NULL ) ;
	if( p_env == NULL )
	{
		printf( "IBACCreateEnvirment failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		printf( "IBACCreateEnvirment ok\n" );
	}
	
	/* 创建请求临时文件1 */
	/* 是个空文件 */
	memset( tmp_req_filename1 , 0x00 , sizeof(tmp_req_filename1) );
	fp = IBPCreateTempFile( "AFILE" , tmp_req_filename1 , NULL , "wb" ) ;
	if( fp == NULL )
	{
		printf( "IBPCreateTempFile failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		printf( "IBPCreateTempFile ok , tmp_req_filename1[%s]\n" , tmp_req_filename1 );
		fclose( fp );
	}
	
	/* 创建请求临时文件2 */
	/* 文件大小为1个字节 */
	memset( tmp_req_filename2 , 0x00 , sizeof(tmp_req_filename2) );
	fp = IBPCreateTempFile( "BFILE" , tmp_req_filename2 , NULL , "wb" ) ;
	if( fp == NULL )
	{
		printf( "IBPCreateTempFile failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		printf( "IBPCreateTempFile ok , tmp_req_filename2[%s]\n" , tmp_req_filename2 );
		fprintf( fp , "2\n" );
		fclose( fp );
	}
	
	/* 创建请求临时文件3 */
	/* 文件大小为1024个字节 */
	memset( tmp_req_filename3 , 0x00 , sizeof(tmp_req_filename3) );
	fp = IBPCreateTempFile( "CFILE" , tmp_req_filename3 , NULL , "wb" ) ;
	if( fp == NULL )
	{
		printf( "IBPCreateTempFile failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		char	buf[ 1023 ] ;
		printf( "IBPCreateTempFile ok , tmp_req_filename3[%s]\n" , tmp_req_filename3 );
		memset( buf , '3' , sizeof(buf) );
		fwrite( buf , sizeof(buf) , 1 , fp );
		fclose( fp );
	}
	
	/* 创建请求临时文件4 */
	/* 文件大小为1024*1024个字节 */
	memset( tmp_req_filename4 , 0x00 , sizeof(tmp_req_filename4) );
	fp = IBPCreateTempFile( "DFILE" , tmp_req_filename4 , NULL , "wb" ) ;
	if( fp == NULL )
	{
		printf( "IBPCreateTempFile failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		char	buf[ 1025 ] ;
		int	i ;
		printf( "IBPCreateTempFile ok , tmp_req_filename4[%s]\n" , tmp_req_filename4 );
		memset( buf , '4' , sizeof(buf) );
		for( i = 0 ; i < 1025 ; i++ )
			fwrite( buf , sizeof(buf) , 1 , fp );
		fclose( fp );
	}
	
	/* 初始化响应临时文件名缓冲区，如果有响应临时文件回来就会往里面放 */
	memset( tmp_rsp_filename1 , 0x00 , sizeof(tmp_rsp_filename1) );
	memset( tmp_rsp_filename2 , 0x00 , sizeof(tmp_rsp_filename2) );
	memset( tmp_rsp_filename3 , 0x00 , sizeof(tmp_rsp_filename3) );
	memset( tmp_rsp_filename4 , 0x00 , sizeof(tmp_rsp_filename4) );
	
	/* 连接通讯服务端，发送请求，接收响应，断开通讯服务端 */
	/* 向节点node发起交易app，p_msg指向请求报文，交易完成后，响应报文存放在通讯客户端环境中，p_msg指向它 */
	p_msg = msg ;
	msg_len = strlen(msg) ;
	nret = IBACRequester( p_env , node , "ibp_test_file" , & p_msg , & msg_len , tmp_req_filename1 , tmp_req_filename2 , tmp_req_filename3 , tmp_req_filename4 , NULL , tmp_rsp_filename1 , tmp_rsp_filename2 , tmp_rsp_filename3 , tmp_rsp_filename4 , NULL ) ;
	if( nret )
	{
		printf( "IBACRequester failed[%d] , errno[%d]\n" , nret , errno );
		return -1;
	}
	else
	{
		printf( "IBACRequester ok , msg[%.*s]\n" , msg_len , p_msg );
		printf( "tmp_rsp_filename1[%s]\n" , tmp_rsp_filename1 );
		printf( "tmp_rsp_filename2[%s]\n" , tmp_rsp_filename2 );
		printf( "tmp_rsp_filename3[%s]\n" , tmp_rsp_filename3 );
		printf( "tmp_rsp_filename4[%s]\n" , tmp_rsp_filename4 );
	}
	
	/* 销毁通讯客户端环境 */
	IBACDestroyEnvirment( p_env );
	printf( "IBACDestroyEnvirment ok\n" );
	
	return 0;
}

static void usage()
{
	printf( "USAGE : ibp_test_file node msg\n" );
	return;
}

int main( int argc , char *argv[] )
{
	int		nret = 0 ;
	
	if( argc == 1 + 2 )
	{
		IBPInitLogEnv( "" , "ibp_test_file" , "file::log/event.log" , LOG_LEVEL_DEBUG , "file::log/ibp_test_file.log" );
		nret = ibp_test_file( argv[1] , argv[2] ) ;
		IBPCleanLogEnv();
		return -nret;
	}
	else
	{
		usage();
		exit(7);
	}
}
```

### 2.2.3. 发起通讯请求（低层）

test/test_ibpclient/ibp_test_echo/ibp_test_echo.c

```
#include "ibac_api.h"

int ibp_test_echo_IBACSendRequestAndReceiveResponse( char *node , char *app , char *msg )
{
	struct IbacEnv		*p_env = NULL ;
	
	char			*p_msg = NULL ;
	int			msg_len ;
	
	int			nret = 0 ;
	
	/* 创建通讯客户端环境 */
	p_env = IBACCreateEnvirment( NULL ) ;
	if( p_env == NULL )
	{
		printf( "IBACCreateEnvirment failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		printf( "IBACCreateEnvirment ok\n" );
	}
	
	/* 连接通讯服务端 */
	nret = IBACConnect( p_env , node ) ;
	if( nret )
	{
		printf( "IBACConnect failed , errno[%d]\n" , errno );
		return -1;
	}
	else
	{
		printf( "IBACConnect ok\n" );
	}
	
	/* 发送请求，接收响应 */
	/* 向节点node发起交易app，p_msg指向请求报文，交易完成后，响应报文存放在通讯客户端环境中，p_msg指向它 */
	p_msg = msg ;
	msg_len = strlen(msg) ;
	nret = IBACSendRequestAndReceiveResponse( p_env , app , & p_msg , & msg_len , NULL , NULL ) ;
	if( nret )
	{
		printf( "IBACSendRequestAndReceiveResponse failed[%d] , errno[%d]\n" , nret , errno );
		return -1;
	}
	else
	{
		printf( "IBACSendRequestAndReceiveResponse ok , msg[%.*s]\n" , msg_len , p_msg );
	}
	
	/* 断开通讯服务端 */
	IBACDisconnect( p_env );
	printf( "IBACDisconnect ok\n" );
	
	/* 销毁通讯客户端环境 */
	IBACDestroyEnvirment( p_env );
	printf( "IBACDestroyEnvirment ok\n" );
	
	return 0;
}

static void usage()
{
	printf( "USAGE : ibp_test_echo node app msg\n" );
	return;
}

int main( int argc , char *argv[] )
{
	int		nret = 0 ;
	
	if( argc == 1 + 3 )
	{
		IBPInitLogEnv( "" , "ibp_test_echo" , "file::log/event.log" , LOG_LEVEL_DEBUG , "file::log/ibp_test_echo.log" );
		nret = ibp_test_echo_IBACSendRequestAndReceiveResponse ( argv[1] , argv[2] , argv[3] ) ;
		IBPCleanLogEnv();
		return -nret;
	}
	else
	{
		usage();
		exit(7);
	}
}
```

## 2.3. 通讯服务端API

### 2.3.1. 回射服务

test/test_ibpserver/ibp_test_echo/ibp_test_echo.c

```
#include "ibas_api.h"

funcIbasSomain somain ;
int somain( struct HttpBuffer *req_body , struct HttpBuffer *rsp_body , struct IbasAddonFiles *addon_files )
{
	char			*msg = NULL ;
	int			msg_len ;
	
	int			nret = 0 ;
	
	INFOLOGSG( "ENTER ibp_test_echo" );
	
	/* 回射请求报文 */
	msg = GetHttpBufferBase( req_body , & msg_len ) ;
	nret = MemcatHttpBuffer( rsp_body , msg , msg_len ) ;
	if( nret )
	{
		ERRORLOGG( "MemcatHttpBuffer failed[%d] , errno[%d]" , nret , errno );
		return -1;
	}
	else
	{
		INFOLOGG( "msg[%.*s]" , msg_len , msg );
	}
	
	INFOLOGSG( "LEAVE ibp_test_echo" );
	
	return nret;
}
```

test/test_ibpserver/ibp_test_echo/makefile

```
# 此文件由makeobj.sh自动生成
############################################################
# 项目名 : 
# 模块名 : 
# 备  注 : 
############################################################

###### 源文件配置区
#@ c_FILE
c_FILE		=	\
			ibp_test_echo.c \

###### 目标文件、安装目录配置区
include makeinstall
LIB		=	ibp_test_echo.so
LIBINST		=	$(_LIBINST)

###### 编译选项
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \

###### 链接选项
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libas_api \

###### 额外宏定义区
CLEAN_ADDITION	=

###### 加载mktpl模板库
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_LIBINST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_LIBINST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### 目标文件依赖关系
ibp_test_echo.so		:	$(c_FILE_o)
	$(CC) -o $@ $(c_FILE_o) $(SOFLAGS) $(LFLAGS)
	ibpcheckso $@ -r
```

### 2.3.2. 回射服务（附带文件）

test/test_ibpserver/ibp_test_file/ibp_test_file.c

```
#include "ibas_api.h"

funcIbasSomain somain ;
int somain( struct HttpBuffer *req_body , struct HttpBuffer *rsp_body , struct IbasAddonFiles *addon_files )
{
	char			*msg = NULL ;
	int			msg_len ;
	
	int			i ;
	int			count ;
	char			*p_filename = NULL ;
	
	int			nret = 0 ;
	
	INFOLOGSG( "ENTER ibp_test_file" );
	
	/* 回射请求报文 */
	msg = GetHttpBufferBase( req_body , & msg_len ) ;
	nret = MemcatHttpBuffer( rsp_body , msg , msg_len ) ;
	if( nret )
	{
		ERRORLOGG( "MemcatHttpBuffer failed[%d] , errno[%d]" , nret , errno );
		return -1;
	}
	else
	{
		INFOHEXLOGG( msg , msg_len , "msg [%d]bytes" , msg_len );
	}
	
	/* 按文件ID取请求文件名 */
	p_filename = IBASGetRequestFileById( addon_files , "BFILE" ) ;
	if( p_filename )
	{
		INFOLOGG( "IBASGetRequestFile ok , [%s]" , p_filename );
	}
	
	/* 回射所有请求文件 */
	count = IBASGetRequestFileCount( addon_files ) ;
	for( i = 0 ; i < count ; i++ )
	{
		p_filename = IBASGetRequestFile( addon_files , i ) ;
		INFOLOGG( "FILE[%s] " , p_filename );
		
		nret = IBASPutResponseFile( addon_files , p_filename ) ;
		if( nret )
		{
			ERRORLOGG( "IBASPutResponseFile failed[%d]" , nret );
			return -2;
		}
	}
	
	INFOLOGSG( "LEAVE ibp_test_file" );
	
	return 0;
}
```

## 2.4. 报文转换API

test/test_ibpclient/ibp_test_ts1/ibp_test_ts1.c

```
#include "ibmsgv_api.h"

#include "IDL_test_ibpts1_request.dsc.h"
#include "IDL_test_ibpts1_response.dsc.h"

static int ibp_test_ts1( char *node )
{
	test_ibpts1_request	req_msg ;
	test_ibpts1_response	rsp_msg ;
	
	int			nret = 0 ;
	
	memset( & req_msg , 0x00 , sizeof(test_ibpts1_request) );
	strcpy( req_msg.test_request_header.trans_code , "ibp_test_ts1" );
	strcpy( req_msg.test_ibpts1.account_no , "603367123412341234" );
	memset( & rsp_msg , 0x00 , sizeof(test_ibpts1_response) );
	nret = IBMSGVCall_JSON( NULL , node , "ibp_test_ts1" , (void*) & req_msg , & DSCSERIALIZE_JSON_DUP_test_ibpts1_request_V , (void*) & rsp_msg , & DSCDESERIALIZE_JSON_test_ibpts1_response_V , NULL , NULL ) ;
	if( nret )
	{
		printf( "IBMSGVCall failed[%d] , errno[%d]\n" , nret , errno );
		return -1;
	}
	else
	{
		printf( "IBMSGVCall ok\n" );
	}
	
	printf( "response_code[%s] response_desc[%s] - account_no[%s] balance[%.2lf]\n"
		, rsp_msg.test_response_header.response_code , rsp_msg.test_response_header.response_desc
		, rsp_msg.test_ibpts1.account_no , rsp_msg.test_ibpts1.balance );
	
	return 0;
}

static void usage()
{
	printf( "USAGE : ibp_test_ts1 node\n" );
	return;
}

int main( int argc , char *argv[] )
{
	int		nret = 0 ;
	
	if( argc == 1 + 1 )
	{
		IBPInitLogEnv( "" , "ibp_test_ts1" , "file::log/event.log" , LOG_LEVEL_DEBUG , "file::log/ibp_test_ts1.log" );
		nret = ibp_test_ts1( argv[1] ) ;
		IBPCleanLogEnv();
		return -nret;
	}
	else
	{
		usage();
		exit(7);
	}
}
```

test/test_ibpclient/ibp_test_ts1/makefile

```
# 此文件由makeobj.sh自动生成
############################################################
# 项目名 : 
# 模块名 : 
# 备  注 : 
############################################################

###### 源文件配置区
#@ c_FILE
c_FILE		=	\
			ibp_test_ts1.c \

###### 目标文件、安装目录配置区
include makeinstall
BIN		=	ibp_test_ts1
BININST		=	$(_BININST)

###### 编译选项
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \
			-I../../test_ibpserver/ibp_test_ts1 \

###### 链接选项
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libmsgv_api \

###### 额外宏定义区
CLEAN_ADDITION	=

###### 加载mktpl模板库
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_BININST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_BININST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### 目标文件依赖关系
ibp_test_ts1		:	$(c_FILE_o) IDL_test_ibpts1_request.dsc.o IDL_test_ibpts1_response.dsc.o
	$(CC) -o $@ $(c_FILE_o) IDL_test_ibpts1_request.dsc.o IDL_test_ibpts1_response.dsc.o $(LFLAGS)
```

## 2.5. 动态结构容器

src/ibtm/test.c

```
/*
 * IBP - Technology architecture for real-time transaction
 * author	: calvin
 * email	: calvinwilliams@163.com
 *
 * Licensed under the LGPL v2.1, see the file LICENSE in base directory.
 */

#include "ibtm_in.h"

struct DS_infunc
{
	char	ch ;
	short	s ;
	int	i ;
	long	l ;
	float	f ;
	double	d ;
	char	buf[ 64 + 1 ] ;
} ;

int test_DS_infunc( DS *ds )
{
	struct DS_infunc	infunc ;
	
	DS_TRY(ds)
	{
		DS_GET( ds , char , char_field , & (infunc.ch) )
		DS_GET( ds , short , short_field , & (infunc.s) )
		DS_GET( ds , int , int_field , & (infunc.i) )
		DS_GET( ds , long , long_field , & (infunc.l) )
		DS_GET( ds , float , float_field , & (infunc.f) )
		DS_GET( ds , double , double_field , & (infunc.d) )
		DS_GET( ds , char* , string_field , infunc.buf , sizeof(infunc.buf) )
	}
	DS_CATCH(ds)
	{
		printf( "DS_GET failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]\n" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) );
		return -1;
	}
	
	printf( "--- infunc ---\n" );
	printf( "infunc.ch [%c]\n" , infunc.ch );
	printf( "infunc.s  [%hd]\n" , infunc.s );
	printf( "infunc.i  [%d]\n" , infunc.i );
	printf( "infunc.l  [%ld]\n" , infunc.l );
	printf( "infunc.f  [%f]\n" , infunc.f );
	printf( "infunc.d  [%lf]\n" , infunc.d );
	printf( "infunc.buf[%s]\n" , infunc.buf );
	
	DS_TRY(ds)
	{
		DS_SET( ds , char , char_field , 'Z' )
		DS_SET( ds , short , short_field , 9 )
		DS_SET( ds , int , int_field , 87 )
		DS_SET( ds , long , long_field , 654321 )
		DS_SET( ds , float , float_field , 9.8 )
		DS_SET( ds , double , double_field , 7654.3210 )
		DS_SET( ds , char* , string_field , "world" )
	}
	DS_CATCH(ds)
	{
		printf( "DS_SET failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]\n" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) );
		return -1;
	}
	
	return 0;
}

struct DS_caller
{
	char	ch ;
	short	s ;
	int	i ;
	long	l ;
	float	f ;
	double	d ;
	char	buf[ 64 + 1 ] ;
} ;

int test_DS_caller()
{
	struct DS_caller	caller ;
	DS			*ds = DS_NEW( "struct_name" ) ;
	
	if( ds == NULL )
	{
		printf( "DS_NEW failed , errno[%d]\n" , errno );
		return -1;
	}
	
	memset( & caller , 0x00 , sizeof(struct DS_caller) );
	caller.ch = 'A' ;
	caller.s = 1 ;
	caller.i = 23 ;
	caller.l = 456789 ;
	caller.f = 1.2 ;
	caller.d = 3456.7890 ;
	strcpy( caller.buf , "hello" );
	
	DS_TRY(ds)
	{
		DS_ADD( ds , char , char_field , caller.ch )
		DS_ADD( ds , short , short_field , caller.s )
		DS_ADD( ds , int , int_field , caller.i )
		DS_ADD( ds , long , long_field , caller.l )
		DS_ADD( ds , float , float_field , caller.f )
		DS_ADD( ds , double , double_field , caller.d )
		DS_ADD( ds , char* , string_field , caller.buf )
	}
	DS_CATCH(ds)
	{
		printf( "DS_ADD failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]\n" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) );
		DS_DELETE( ds )
		return -1;
	}
	
	test_DS_infunc( ds );
	
	memset( & caller , 0x00 , sizeof(struct DS_caller) );
	
	DS_TRY(ds)
	{
		DS_GET( ds , char , char_field , & (caller.ch) )
		DS_GET( ds , short , short_field , & (caller.s) )
		DS_GET( ds , int , int_field , & (caller.i) )
		DS_GET( ds , long , long_field , & (caller.l) )
		DS_GET( ds , float , float_field , & (caller.f) )
		DS_GET( ds , double , double_field , & (caller.d) )
		DS_GET( ds , char* , string_field , caller.buf , sizeof(caller.buf) )
	}
	DS_CATCH(ds)
	{
		printf( "DS_GET failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]\n" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) );
		DS_DELETE( ds )
		return -1;
	}
	
	printf( "--- caller ---\n" );
	printf( "caller.ch [%c]\n" , caller.ch );
	printf( "caller.s  [%hd]\n" , caller.s );
	printf( "caller.i  [%d]\n" , caller.i );
	printf( "caller.l  [%ld]\n" , caller.l );
	printf( "caller.f  [%f]\n" , caller.f );
	printf( "caller.d  [%lf]\n" , caller.d );
	printf( "caller.buf[%s]\n" , caller.buf );
	
	DS_DELETE( ds )
	
	return 0;
}

int main()
{
	return -test_DS_caller();
}
```

## 2.6. 分阶段管理层API

test/test_ibpserver/ibp_test_ts1/IDL_test_ibpts1_request.dsc

```
STRUCT	test_ibpts1_request			# 余额查询 请求
{
	INCLUDE IDL_test_request_header.dsc
	
	STRUCT	test_ibpts1
	{
		STRING	40	account_no	# 账号
		STRING	16	password	# 密码
	}
}
```

test/test_ibpserver/ibp_test_ts1/IDL_test_ibpts1_response.dsc

```
STRUCT	test_ibpts1_response		# 余额查询 响应
{
	INCLUDE IDL_test_response_header.dsc
	
	STRUCT	test_ibpts1
	{
		STRING	40	account_no		# 账号
		NUMERIC	16,2	balance			# 余额
	}
}
	test/test_ibpserver/ibp_test_ts1/IDL_test_request_header.dsc
	STRUCT	test_request_header		# 请求公共头
	{
		STRING 10	sender_date	# 发起方日期
		STRING 8	sender_time	# 发起方时间
		STRING 20	sender_trans_no	# 发起方流水号
		STRING 6	channel_code	# 交易渠道
		STRING 10	branch_no	# 交易网点
		STRING 12	oper_no		# 交易柜员
		STRING 32	login_session	# 签到会话
		STRING 20	trans_code	# 交易码
	}
	test/test_ibpserver/ibp_test_ts1/IDL_test_response_header.dsc
	STRUCT	test_response_header			# 响应公共头
	{
		STRING 10	sender_date		# 发起方日期
		STRING 8	sender_time		# 发起方时间
		STRING 20	sender_trans_no		# 发起方流水号
		STRING 10	receiver_date		# 接收方日期
		STRING 8	receiver_time		# 接收方时间
		STRING 20	receiver_trans_no	# 接收方流水号
		STRING 10	response_code		# 交易结果
		STRING 128	response_desc		# 交易结果描述
		STRING 128	response_message	# 额外信息
	}
```

test/test_ibpserver/ibp_test_ts1/somain.c

```
#include "ibmsgv_api.h"

#include "IDL_test_ibpts1_request.dsc.h"
#include "IDL_test_ibpts1_response.dsc.h"

funcIbmsgvTransmain transmain ;

funcIbasSomain somain ;
int somain( struct HttpBuffer *req_body , struct HttpBuffer *rsp_body , struct IbasAddonFiles *addon_files )
{
	test_ibpts1_request	req_st ;
	test_ibpts1_response	rsp_st ;
	
	int			nret = 0 ;
	
	INFOLOGG( "ENTER TESTTPS1" );
	
	memset( & req_st , 0x00 , sizeof(test_ibpts1_request) );
	memset( & rsp_st , 0x00 , sizeof(test_ibpts1_response) );
	nret = IBMSGVReceiver_JSON( req_body , & DSCDESERIALIZE_JSON_test_ibpts1_request_V , & req_st
				, rsp_body , & DSCSERIALIZE_JSON_DUP_test_ibpts1_response_V , & rsp_st
				, & transmain , addon_files ) ;
	if( nret )
	{
		ERRORLOGG( "IBMSGVReceiver_JSON failed[%d]" , nret );
	}
	else
	{
		INFOLOGG( "IBMSGVReceiver_JSON ok" );
	}
	
	INFOLOGG( "LEAVE TESTTPS1" );
	
	return nret;
}
```

test/test_ibpserver/ibp_test_ts1/transmain.c

```
#include "ibts_api.h"

#include "IDL_test_ibpts1_request.dsc.h"
#include "IDL_test_ibpts1_response.dsc.h"

#include "TF_BT.c"
#include "TF_PC.c"
#include "TF_BC.c"
#include "TF_BP.c"
#include "TF_AP.c"
#include "TF_AT.c"

struct TransFuncArray	TFA_BT_TESTTPS1[] =
	{
		FUNC( "交易前处理1" , TF_BT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_PC_CH_TESTTPS1[] =
	{
		FUNC( "渠道公共检查" , TF_PC_CH_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_PC_OP_TESTTPS1[] =
	{
		FUNC( "操作员公共检查" , TF_PC_OP_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_PC_OG_TESTTPS1[] =
	{
		FUNC( "机构公共检查" , TF_PC_OG_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_MD_TESTTPS1[] =
	{
		FUNC( "介质层业务检查" , TF_BC_MD_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_AT_TESTTPS1[] =
	{
		FUNC( "账户层业务检查" , TF_BC_AT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_CT_TESTTPS1[] =
	{
		FUNC( "客户层业务检查" , TF_BC_CT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_BS_TESTTPS1[] =
	{
		FUNC( "业务层检查函数1" , TF_BC_BS_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_MD_TESTTPS1[] =
	{
		FUNC( "介质层业务处理" , TF_BP_MD_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_AT_TESTTPS1[] =
	{
		FUNC( "账户层业务处理" , TF_BP_AT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_CT_TESTTPS1[] =
	{
		FUNC( "客户层业务处理" , TF_BP_CT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_BS_TESTTPS1[] =
	{
		FUNC( "业务处理函数1" , TF_BP_BS_TESTTPS1_F1 )
		FUNCARRAY( "业务处理函数数组2" , TFA_BP_TESTTPS1_FA2 )
		IF_IN_TRANSCODES_THEN_FUNC( "业务处理函数数组3" , "TESTTPS1" , TF_BP_BS_TESTTPS1_F3 )
		IF_NOTIN_TRANSCODES_THEN_FUNCARRAY( "业务处理函数数组0" , "TESTTPS1" , TFA_BP_BS_TESTTPS1_FA0 )
		IF_FUNC_THEN( "业务处理函数4" , TF_BP_BS_TESTTPS1_F4 )
			FUNC( "业务处理函数5" , TF_BP_BS_TESTTPS1_F5 )
		ELSE
			FUNC( "业务处理函数0" , TF_BP_BS_TESTTPS1_F0 )
		ENDIF
		IF_FUNCARRAY_THEN( "业务处理函数数组6" , TFA_BP_BS_TESTTPS1_FA6 )
			FUNC( "业务处理函数0" , TF_BP_BS_TESTTPS1_F0 )
		ELSE
			FUNC( "业务处理函数7" , TF_BP_BS_TESTTPS1_F7 )
		ENDIF
		FUNC( "业务处理函数8" , TF_BP_BS_TESTTPS1_F8 )
		RETURN
	} ;

struct TransFuncArray	TFA_AP_TESTTPS1[] =
	{
		FUNC( "账务处理" , TF_AP_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_AT_TESTTPS1[] =
	{
		FUNC( "交易后处理" , TF_AT_TESTTPS1 )
		RETURN
	} ;

struct TransSchedule_BT_PC_BP_AP_AT	TS_TESTTPS1 =
	{
		"交易前处理" , TFA_BT_TESTTPS1 ,
		{
			"渠道公共检查" , TFA_PC_CH_TESTTPS1 ,
			"操作员公共检查" , TFA_PC_OP_TESTTPS1 ,
			"机构公共检查" , TFA_PC_OG_TESTTPS1 ,
			"其它公共检查" , NULL
		} ,
		{
			"介质层业务检查" , TFA_BC_MD_TESTTPS1 ,
			"账户层业务检查" , TFA_BC_AT_TESTTPS1 ,
			"客户层业务检查" , TFA_BC_CT_TESTTPS1 ,
			"业务层业务检查" , TFA_BC_BS_TESTTPS1 ,
			"其它业务检查" , NULL
		} ,
		{
			"介质层业务处理" , TFA_BP_MD_TESTTPS1 ,
			"账户层业务处理" , TFA_BP_AT_TESTTPS1 ,
			"客户层业务处理" , TFA_BP_CT_TESTTPS1 ,
			"业务层业务处理" , TFA_BP_BS_TESTTPS1 ,
			"其它业务处理" , NULL
		} ,
		"账务处理" , TFA_AP_TESTTPS1 ,
		"交易后处理" , TFA_AT_TESTTPS1
	} ;

funcIbmsgvTransmain transmain ;
int transmain( void *pv_req_st , void *pv_rsp_st , struct IbasAddonFiles *addon_files )
{
	test_ibpts1_request	*p_req_st = (test_ibpts1_request *) pv_req_st ;
	test_ibpts1_response	*p_rsp_st = (test_ibpts1_response *) pv_rsp_st ;
	
	int			nret = 0 ;
	
	nret = IBTSExecuteSchedule_BT_PC_BP_AP_AT( "test_ibpts1_request" , sizeof(test_ibpts1_request) , pv_req_st
						, "test_ibpts1_response" , sizeof(test_ibpts1_response) , pv_rsp_st
						, addon_files
						, p_req_st->test_request_header.trans_code
						, p_rsp_st->test_response_header.response_code , sizeof(p_rsp_st->test_response_header.response_code)
						, p_rsp_st->test_response_header.response_desc , sizeof(p_rsp_st->test_response_header.response_desc)
						, & TS_TESTTPS1 ) ;
	if( nret )
	{
		ERRORLOGG( "IBTSExecuteSchedule_BT_PC_BP_AP_AT failed[%d]" , nret );
	}
	else
	{
		INFOLOGG( "IBTSExecuteSchedule_BT_PC_BP_AP_AT ok" );
	}
	
	return nret;
}
```

test/test_ibpserver/ibp_test_ts1/TF_BT.c

```
#include "ibtm_api.h"

TransFunc TF_BT_TESTTPS1 ;
int TF_BT_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}
	test/test_ibpserver/ibp_test_ts1/TF_PC.c
#include "ibtm_api.h"

TransFunc TF_PC_CH_TESTTPS1 ;
int TF_PC_CH_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_PC_OP_TESTTPS1 ;
int TF_PC_OP_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_PC_OG_TESTTPS1 ;
int TF_PC_OG_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}
	test/test_ibpserver/ibp_test_ts1/TF_BC.c
#include "ibtm_api.h"

TransFunc TF_BC_MD_TESTTPS1 ;
int TF_BC_MD_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	/*
	return IBTMFormatResponseInfo( p_te , -1 , "无此卡号[%s]" , "603367123412341234" );
	*/
	return 0;
}

TransFunc TF_BC_AT_TESTTPS1 ;
int TF_BC_AT_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BC_CT_TESTTPS1 ;
int TF_BC_CT_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BC_BS_TESTTPS1 ;
int TF_BC_BS_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}
	test/test_ibpserver/ibp_test_ts1/TF_BP.c
#include "ibtm_api.h"

TransFunc TF_BP_MD_TESTTPS1 ;
int TF_BP_MD_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BP_AT_TESTTPS1 ;
int TF_BP_AT_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BP_CT_TESTTPS1 ;
int TF_BP_CT_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BP_BS_TESTTPS1_F0 ;
int TF_BP_BS_TESTTPS1_F0( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

struct TransFuncArray	TFA_BP_BS_TESTTPS1_FA0[] =
	{
		FUNC( "业务层业务处理0" , TF_BP_BS_TESTTPS1_F0 )
		RETURN
	} ;

TransFunc TF_BP_BS_TESTTPS1_F1 ;
int TF_BP_BS_TESTTPS1_F1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BP_BS_TESTTPS1_F2 ;
int TF_BP_BS_TESTTPS1_F2( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

struct TransFuncArray	TFA_BP_TESTTPS1_FA2[] =
	{
		FUNC( "业务层业务处理2" , TF_BP_BS_TESTTPS1_F2 )
		RETURN
	} ;

TransFunc TF_BP_BS_TESTTPS1_F3 ;
int TF_BP_BS_TESTTPS1_F3( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BP_BS_TESTTPS1_F4 ;
int TF_BP_BS_TESTTPS1_F4( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BP_BS_TESTTPS1_F5 ;
int TF_BP_BS_TESTTPS1_F5( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

TransFunc TF_BP_BS_TESTTPS1_F6 ;
int TF_BP_BS_TESTTPS1_F6( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 1;
}

struct TransFuncArray	TFA_BP_BS_TESTTPS1_FA6[] =
	{
		FUNC( "业务层业务处理6" , TF_BP_BS_TESTTPS1_F6 )
		RETURN
	} ;

TransFunc TF_BP_BS_TESTTPS1_F7 ;
int TF_BP_BS_TESTTPS1_F7( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}

void do_coredump( struct TransEnv *p_te )
{
#if 0
	char	*p = NULL ;
	strcpy( p , "let's core" );
#endif
	
	return;
}

TransFunc TF_BP_BS_TESTTPS1_F8 ;
int TF_BP_BS_TESTTPS1_F8( struct TransEnv *p_te )
{
	test_ibpts1_request	*p_req_msg = NULL ;
	test_ibpts1_response	*p_rsp_msg = NULL ;
	
	int			nret = 0 ;
	
	nret = IBTMGetStructBlock( p_te , "test_ibpts1_request" , sizeof(test_ibpts1_request) , (void**) & p_req_msg ) ;
	if( nret )
	{
		ERRORLOGG( "IBTMGetStructBlock failed[%d]" , nret );
		return 1;
	}
	
	nret = IBTMGetStructBlock( p_te , "test_ibpts1_response" , sizeof(test_ibpts1_response) , (void**) & p_rsp_msg ) ;
	if( nret )
	{
		ERRORLOGG( "IBTMGetStructBlock failed[%d]" , nret );
		return 1;
	}
	
	do_coredump( p_te );
	
	strcpy( p_rsp_msg->test_ibpts1.account_no , p_req_msg->test_ibpts1.account_no );
	p_rsp_msg->test_ibpts1.balance = 1000.00 ;
	
	return 0;
}
	test/test_ibpserver/ibp_test_ts1/TF_AP.c
#include "ibtm_api.h"

TransFunc TF_AP_TESTTPS1 ;
int TF_AP_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}
	test/test_ibpserver/ibp_test_ts1/TF_AT.c
#include "ibtm_api.h"

TransFunc TF_AT_TESTTPS1 ;
int TF_AT_TESTTPS1( struct TransEnv *p_te )
{
	INFOLOGG( "..." );
	
	return 0;
}
```

test/test_ibpserver/ibp_test_ts1/makefile

```
# 此文件由makeobj.sh自动生成
############################################################
# 项目名 : 
# 模块名 : 
# 备  注 : 
############################################################

###### 源文件配置区
#@ c_FILE
c_FILE		=	\
			IDL_test_ibpts1_request.dsc.c \
			IDL_test_ibpts1_response.dsc.c \
			somain.c \
			transmain.c \

###### 目标文件、安装目录配置区
include makeinstall
LIB		=	ibp_test_ts1.so
LIBINST		=	$(_LIBINST)

###### 编译选项
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \

###### 链接选项
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libmsgv_api \
			-libtm_api \
			-libts_api \

###### 额外宏定义区
CLEAN_ADDITION	=

###### 加载mktpl模板库
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_LIBINST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_LIBINST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### 目标文件依赖关系
ibp_test_ts1.so		:	$(c_FILE_o)
	$(CC) -o $@ $(c_FILE_o) $(SOFLAGS) $(LFLAGS)
	ibpcheckso $@ -r
```
