�ֲ�ʽ�������������(IBP)�����ʵս���ġ�ҵ���߼������ܣ�
=========================================

| �汾�� | �޶����� | �޶��� | ���� |
| --- | --- | --- | --- |
| 0.0.1.0 | 2018-01-27 | ���� | ���� |

<!-- TOC -->

- [1. ����ת����](#1-����ת����)
    - [1.1. �ӿڶ�������](#11-�ӿڶ�������)
    - [1.2. ����ʹ��](#12-����ʹ��)
- [2. ���׹�������](#2-���׹�������)
    - [2.1. TM������](#21-tm������)
    - [2.2. �ṹ��](#22-�ṹ��)
    - [2.3. ���״�����](#23-���״�����)
    - [2.4. ��̬�ṹ����](#24-��̬�ṹ����)
- [3. ���׽׶ι����](#3-���׽׶ι����)
    - [3.1. ��`transmain`���ڵ�TM����](#31-��transmain���ڵ�tm����)
    - [3.2. Ԥ�÷ֽ׶�ģ��](#32-Ԥ�÷ֽ׶�ģ��)

<!-- /TOC -->

# 1. ����ת����

��IBPͨѶ����ˣ�һ�ʽ��׵Ĵ���Ҫ�����ܶ�㣺

`ͨѶ�����ƽ̨�����̹�����->ͨѶ������->Ӧ�ýӿڲ㣩 -somain()-> Ӧ�ð�������ת����->�ֽ׶�ģ��->TM��������`

`somain`��Ӧ�ð���ں���������ҵ�������ġ�ҵ����Ӧ���Ļ������͸����ļ���������

����ת���㸺���ҵ�������Ľ����C�ṹ�塢���ý�����ں���`transmain`������C�ṹ������ҵ����Ӧ���ġ�

## 1.1. �ӿڶ�������

JSON���Ľ�������ҷ�Ϊ��λ��������ȡ�������������п�ԴJSON������fasterjson����λ��������JSON��������JSON��֦����Ҷ�¼��ص�Ӧ�ú������������п�Դ���ݰ󶨹���DirectStruct������ȡ��������ӿڶ��������ļ����Զ�����fasterjson��Ҫ�Ļص��������Զ���������������ȡ���ݵ�C�ṹ�塣

IBP����ת������DirectStruct��fasterjson���ʵ��JSON������C�ṹ�廥�����ӳ��������

�ӿڶ������ԣ�IDL���ļ���һ���м��﷨��ʽ���ĳһ�౨�Ĳ����Լ���Ϣϸ�ڣ�DirectStruct�Զ�����һ��IDL�﷨��������һ��ʾ����

```
STRUCT                  ibms_app_reqmsg # ibms����Э��app���� ������
{
        STRING 32       app
        STRING 256      desc
        STRING 256      bin
        INT 4           timeout
        INT 4           timeout2
        STRING 32       server_node
        INT 4           invalid
}
```

����`STRUCT`��ʾ���Ķ��忪ʼ������`STRUCT`��ʾ������Ƕ�ӱ��ġ����������������

�ֶζ�������һ�����ֶ����ͣ��ڶ������ֶ�ʵ��ռ���ֳ������������ֶ�����DirectStruct֧���ֶ�������INT 1��INT 2��INT 8��FLOAT 4��FLOAT 8���Լ��޷���������UINT 4����Щ�����ڲ�ͬ���뻷�������Բ�ͬ������������INT 8��

��'DirectStruct'���߳���`dsc`����ö����ļ����������`-c -c-LOG -c-json`�������ͷ�ļ�

```
...
typedef struct
{
        char    app[ 32 + 1 ] ;
        char    desc[ 256 + 1 ] ;
        char    bin[ 256 + 1 ] ;
        int     timeout ;
        int     timeout2 ;
        char    server_node[ 32 + 1 ] ;
        int     invalid ;
} ibms_app_reqmsg ;

_WINDLL_FUNC int DSCINIT_ibms_app_reqmsg( ibms_app_reqmsg *pst );

#include "fasterjson.h"

_WINDLL_FUNC int DSCSERIALIZE_JSON_ibms_app_reqmsg( ibms_app_reqmsg *pst , char *encoding , char *buf , int *p_len );
_WINDLL_FUNC int DSCSERIALIZE_JSON_DUP_ibms_app_reqmsg( ibms_app_reqmsg *pst , char *encoding , char **pp_base , int *p_buf_size , int *p_len );
_WINDLL_FUNC int DSCSERIALIZE_JSON_DUP_ibms_app_reqmsg_V( void *pv , char *encoding , char **pp_base , int *p_buf_size , int *p_len );
_WINDLL_FUNC int DSCDESERIALIZE_JSON_ibms_app_reqmsg( char *encoding , char *buf , int *p_len , ibms_app_reqmsg *pst );
_WINDLL_FUNC int DSCDESERIALIZE_JSON_ibms_app_reqmsg_V( char *encoding , char *buf , int *p_len , void *pv );
...
```

��ʵ���ļ�

```
...
int DSCSERIALIZE_JSON_ibms_app_reqmsg( ibms_app_reqmsg *pst , char *encoding , char *buf , int *p_len )
{
    ...
}

int DSCSERIALIZE_JSON_DUP_ibms_app_reqmsg( ibms_app_reqmsg *pst , char *encoding , char **pp_base , int *p_buf_size , int *p_len )
{
    ...
}
...
```

Ӧ��Դ�����ͷ�ļ���������C�ṹ�嶨��ibms_app_reqmsg����ṹ�����������ʵ���ļ�����Ӧ������һ�𣬾��ܵ���ͷ�ļ��������ĺ������纯��`DSCDESERIALIZE_JSON_ibms_app_reqmsg`���ڰѱ���`ibms_app_reqmsg`���������ӳ�䵽C�ṹ��`ibms_app_reqmsg`�����У��纯��`DSCSERIALIZE_JSON_DUP_ibms_app_reqmsg`���ڰ�C�ṹ��`ibms_app_reqmsg`����������Է����ڴ���ű���`ibms_app_reqmsg`��

����Ϊһ������DirectStruct��fasterjson���ۺ�ʾ����

```
#include "IDL_ibms_app_reqmsg.dsc.h"

ibms_node_reqmsg    ibms_node ;
int                 *p_msg = NULL ;
int                 msg_len = 0 ;

/* ���ṹ�� */
DSCINIT_ibms_app_reqmsg( & ibms_node );
strcpy( ibms_node.node , "TEST_NODE" );

/* ��� */
nret = DSCSERIALIZE_JSON_DUP_ibms_app_reqmsg( & ibms_node , "GB18030" , & p_msg , NULL , & msg_len ) ;
if( nret )
{
    ...
}

/* ��� */
DSCINIT_ibms_app_reqmsg( & ibms_node );
msg_len = 0 ;
nret = DSCDESERIALIZE_JSON_ibms_app_reqmsg( "GB18030" , p_msg , & msg_len , & ibms_node ) ;
if( nret )
{
    ...
}

free( p_msg );
```

## 1.2. ����ʹ��

IBP����ת����������ԭ�����£�

```
/* ������ģ����ý��״�����ں������������ */
int IBMSGVReceiver_JSON( struct HttpBuffer *req_buf , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , void *pv_req_st
                        , struct HttpBuffer *rsp_buf , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st
                        , funcIbmsgvTransmain *p_transmain_func , struct IbasAddonFiles *addon_files );
```

`req_buf`��ҵ�������ģ�`p_unpack_func`��`DirectStruct`���ݽӿڶ��������ļ��Զ����ɵĽ��������`pv_req_st`�ǽ��������ݵĽṹ�壬�ṹ�嶨��Ҳ����`DirectStruct`���ݽӿڶ��������ļ��Զ����ɡ�

`rsp_buf`��ҵ����Ӧ���ģ�`p_pack_func`��`DirectStruct`���ݽӿڶ��������ļ��Զ����ɵĴ��������`pv_rsp_st`�Ǵ��������Դ�Ľṹ�壬�ṹ�嶨��Ҳ����`DirectStruct`���ݽӿڶ��������ļ��Զ����ɡ�

`p_transmain_func`�ǽ�����ں���ָ�룬��Ӧ���ṩ��`addon_files`��ҵ�����󸽴��ļ�������Ӧ�����ļ�����������`somain`ֱ�Ӵ�������

һ���Ծ���ʵ��ʾ�����£�

`somain.c`

```
#include "ibmsgv_api.h"

#include "IDL_test_ibpts1_request.dsc.h"
#include "IDL_test_ibpts1_response.dsc.h"

funcIbmsgvTransmain transmain ;

funcIbasSomain somain ;
int somain( struct HttpBuffer *req_body , struct HttpBuffer *rsp_body , struct IbasAddonFiles *addon_files )
{
        test_ibpts1_request     req_st ;
        test_ibpts1_response    rsp_st ;

        int                     nret = 0 ;

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

`transmain����ԭ��`

`int transmain( void *pv_req_st , void *pv_rsp_st , struct IbasAddonFiles *addon_files );`

����`somain`ͨ������ת���㺯��`IBMSGVReceiver_JSON`���õ�����`transmain`ʱ��������Ӧ�����Ѿ������������Ӧ�ṹ���ˡ�

# 2. ���׹�������

�ܶ�ֲ�ʽ������ܶ�ȱ�ٽ��׹����ܣ�IBP���׹�������̥����ҵ���к���ϵͳ���׹���淶���ṩ����Ӧ��������淶Ӧ�ÿ������ÿ��Լ��ҵ���߼�ģ�黯��Ʒ�ʽ���й����ݿ�������Ƶ�һ���ӽ��������

IBP���׹����ܷ�Ϊ���׹�������ͽ��׽׶ι�������㡣

���׹��������ǽ��׽׶ι����Ĺ����ײ㣬���ṩ��TM���������ṹ�������״���������̬�ṹ�ȹ�����������׽׶ι�����Ǹ���ʵʩ�û�������������ƵĹ淶�㡣

## 2.1. TM������

ģ�黯ҵ�񿪷�ģʽ�У�TM������ҵ���߼�������Ԫ��һ��TM����������һ������װ����Сҵ���߼���Ԫ���������ԱȨ�޼�顢����״̬��顢�Ǽ�ҵ����ˮ�����ĵǼǲ���¼״̬��������˵ȡ�����Ҫҵ�񿪷���Ա��ǰ�����ʱ��ַֽ�ͽ���ɸ����߼��߽硣

TM����ԭ�����£�

`int TransFunc( struct TransEnv *p_te );`

`p_te`�ǽ��״����������н��׹����������蹫����Ϣ������������ṹ���С�

TM����������װԽ��Խ��ֱ����۳�һ������

IBP��TM���������Ƶĺ�����TM��������ṹ�壺

```
struct TransFuncArray
{
        int                     type ; /* ����Ԫ�¹ҵ����� */

        char                    *desc ; /* ���������������������� */
        struct TransFuncArray   *func_array ; /* �¹ҵ��Ǻ������� */
        TransFunc               *func ; /* �¹ҵ��Ǻ��� */
        char                    *func_para ; /* �������� */

        char                    *trans_codes ; /* �������б����ڽ������֧ */
} ;
```

ͨ������ṹ�嶨����﷨�Ǻ꣬ҵ���߼���װ��Ա���Ժ�ֱ�۷����������TM�������¿���TM�������ó�һ���������磺

```
struct TransFuncArray   TFA_BP_BS_TESTTPS1[] =
        {
                FUNC( "ҵ������1" , TF_BP_BS_TESTTPS1_F1 )
                FUNCARRAY( "ҵ����������2" , TFA_BP_TESTTPS1_FA2 )
                IF_IN_TRANSCODES_THEN_FUNC( "ҵ����������3" , "TESTTPS1" , TF_BP_BS_TESTTPS1_F3 )
                IF_NOTIN_TRANSCODES_THEN_FUNCARRAY( "ҵ����������0" , "TESTTPS1" , TFA_BP_BS_TESTTPS1_FA0 )
                IF_FUNC_THEN( "ҵ������4" , TF_BP_BS_TESTTPS1_F4 )
                        FUNC( "ҵ������5" , TF_BP_BS_TESTTPS1_F5 )
                ELSE
                        FUNC( "ҵ������0" , TF_BP_BS_TESTTPS1_F0 )
                ENDIF
                IF_FUNCARRAY_THEN( "ҵ����������6" , TFA_BP_BS_TESTTPS1_FA6 )
                        FUNC( "ҵ������0" , TF_BP_BS_TESTTPS1_F0 )
                ELSE
                        FUNC( "ҵ������7" , TF_BP_BS_TESTTPS1_F7 )
                ENDIF
                FUNC( "ҵ������8" , TF_BP_BS_TESTTPS1_F8 )
                RETURN
        } ;
```

�﷨�Ǻ������б����£�

| TM���������﷨�Ǻ� | ˵�� |
| --- | --- |
| FUNCARRAY(_desc_,_funcarray_) | ִ����TM������ |
| FUNC(_desc_,_func_) | ִ��TM���� |
| FUNC_PARA(_desc_,_func_,_para_) | ִ�д�������TM���� |
| IF_IN_TRANSCODES_THEN_FUNCARRAY(_desc_,_transcode_,_funcarray_) | �����ǰ�����������ý������б��У���ݹ�ִ����TM������ |
| IF_IN_TRANSCODES_THEN_FUNC(_desc_,_transcode_,_func_) | �����ǰ�����������ý������б��У�ִ��TM���� |
| IF_IN_TRANSCODES_THEN_FUNC_PARA(_desc_,_transcode_,_func_,_para_) | �����ǰ�����������ý������б��У�ִ�д�������TM���� |
| IF_NOTIN_TRANSCODES_THEN_FUNCARRAY(_desc_,_transcode_,_funcarray_) | �����ǰ�����벻�����ý������б��У���ݹ�ִ����TM������ |
| IF_NOTIN_TRANSCODES_THEN_FUNC(_desc_,_transcode_,_func_) | �����ǰ�����벻�����ý������б��У�ִ��TM���� |
| IF_NOTIN_TRANSCODES_THEN_FUNC_PARA(_desc_,_transcode_,_func_,_para_) | �����ǰ�����벻�����ý������б��У�ִ�д�������TM���� |
| IF_FUNCARRAY_THEN(_desc_,_funcarray_) | �ݹ�ִ����TM������������б���ִ��������� |
| IF_FUNC_THEN(_desc_,_func_) | ִ��TM����������б���ִ��������� |
| IF_FUNC_PARA_THEN(_desc_,_func_,_para_) | ִ�д�������TM����������б���ִ��������� |
| ELSE | IF����Ϊ��ʱ��ִ��������� |
| ENDIF | ����IF���� |
| RETURN | �������ÿ� |

���׹��������ṩ��TM������ִ�����溯�����ڸ����﷨�Ǻ걳������̿����߼�ִ��TM��������

`int IBTMExecuteFuncArray( struct TransEnv *p_te , char *desc , struct TransFuncArray *p_tfa );`

һ��ҵ�񿪷���Ա����ֱ�ӵ��ø����溯����TM�������뽻��֮�仹�зֽ׶�ģ�壬ҵ�񿪷���Ա���÷ֽ׶�ģ�����溯�����ֽ׶�ģ�����溯������ִ�н����ڲ�ͬ�׶��߼������ݿ�������ơ�

## 2.2. �ṹ��

�ṹ�������ڲ�ͬTM����֮�䴫�����ݣ����ݰ��ڽṹ���ÿ���ṹ����һ�����֣��ַ��������ṹ��ҳ�һ�����������ṹ����

���׹��������ṩ�˽ṹ�����������ڹҽṹ��ȡ�ṹ��

```
int IBTMAppendStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem );
int IBTMGetStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem );
int IBTMAppendGetStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem );
```

����`struct_size`��Ϊ�˷�ֹԴ��δ�����ر�����ɵĽṹ�嶨��汾��һ�¡�

## 2.3. ���״�����

���״����������˽��״�����������й�����Ϣ����ṹ�����ڵ㣬ͳһ����һ���ṹ�壬Ҳ��TM����ԭ���е�Ψһͳһ������

��������������Ҫ��Ӧ�ðѽ����롢��Ӧ�롢��Ӧ�������ֶε�ַ����������������������TM�����Ĵ����оͿ�����ͳһ�Ŀ�ܺ�����д��Щ��Ϣ���粻ͬ���ĵ���Ӧ���ֶο���·����һ�£���������������¼����Ӧ���ֶε�ַ����ܺ���IBTMFormatResponseInfo���������⽻����ͳһ������Ӧ�롣

���״������ṹ�������£�

```
struct TransEnv
{
        struct rb_root          structs_rbtree ; /* �ṹ���ݿ��� */
        struct IbasAddonFiles   *addon_files ; /* ibas�����ļ�����Ӧ�ļ���Ϣ */
        char                    trans_code[ IBP_MAXLEN_APP + 1 ] ; /* ҵ������ */
        char                    *func_para ; /* �������ò��� */

        int                     execute_depth ; /* ������� */

        char                    *response_code ; /* ���׽�������� */
        int                     response_code_bufsize ; /* ���׽����������С */
        char                    *response_desc ; /* ���׽������������ */
        int                     response_desc_bufsize ; /* ���׽��������������С */

        int                     database_transation_depth ; /* ���ݿ�������� */
} ;
```

�Ժ������Ҫ���Բ����ֶΡ�

�ýṹ���Ӧ�ò㲻��ֱ�ӷ����ֶΣ�����ͨ����ܺ������ʣ��Ա����ڲ��汾һ�¡�

## 2.4. ��̬�ṹ����

����Ŀ��ģԽ��Խ��ģ��Խ��Խ�࣬�����Ŷ�Խ��Խϸ�֣����ɱ���Ҫ��ģ�黯��ģ����ϵͳ��ģ���ӿڰ汾�����Ե�Խ��Խ��Ҫ��һ�ּܹ������������ǲ���΢���񣬵�΢���񵥸�ʵ���л��Ǵ��ڶ�ģ�齻�����⡣

֮ǰ��Cջ��Ŀʵ���з��֣�ģ��亯������ҵ���ֶζ���װ�ڵ����ṹ���ڣ����ײ�ģ��ʹ�ýṹ����ı������ϲ��漰ģ��û�м�ʱȫ�����������ʱ����ɵ�ַcrash��Ҫ�������������ȵ��ó������������ֺͷ�����IBP����˶�̬�ṹ������ʵ������ʱӦ���������֣������Ǳ���crash��

��̬�ṹ����ԭ��ǳ��򵥣����÷����ݽӿڶ��壬������̬�ṹ���������������ֶζ�ѹ���������ҽ����ϣ���Ȼ����ñ����÷��������÷��������а��ֶζ���������������ж������������ȫ��飬������ֲ����Ͻӿڹ����������ؽӿڲ�һ�´������Ĺ���������ʱ�����ģ�������������ʱ���������ӿڱ䶯���в��ִ���δȫ��������⡣

��̬�ṹ����ʵ�ֵ��ѵ�����ξ�����Ӧ�ÿ�����Ա��ʹ�����Ǹ�����IBPʹ�ÿɱ�������װ���˵ײ㸴���ԡ�

ʾ������ϵ�С����������ӿڲο�����

# 3. ���׽׶ι����

## 3.1. ��`transmain`���ڵ�TM����

![IBP���״�����](tm_framework.png)

һ�ʽ����ڿ�ܹ����о����Ĳ�����£�

`transmain->�ֽ׶�ģ��->TM������->TM����`

����`transmain`���÷ֽ׶�ģ�����档

```
funcIbmsgvTransmain transmain ;
int transmain( void *pv_req_st , void *pv_rsp_st , struct IbasAddonFiles *addon_files )
{
        test_ibpts1_request     *p_req_st = (test_ibpts1_request *) pv_req_st ;
        test_ibpts1_response    *p_rsp_st = (test_ibpts1_response *) pv_rsp_st ;

        int                     nret = 0 ;

        nret = IBTSExecuteSchedule_BT_PC_BP_AP_AT( "test_ibpts1_request" , sizeof(test_ibpts1_request) , pv_req_st
                                                , "test_ibpts1_response" , sizeof(test_ibpts1_response) , pv_rsp_st
                                                , addon_files
                                                , p_req_st->test_request_header.trans_code
                                                , p_rsp_st->test_response_header.response_code , sizeof(p_rsp_st->test_response_header.response_code)
                                                , p_rsp_st->test_response_header.response_desc , sizeof(p_rsp_st->test_response_header.response_desc)
                                                , NULL , NULL , & TS_TESTTPS1 ) ;
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

�ֽ׶�ģ���������TM������ִ������ֱ�ִ�зֽ׶����ã����Խ׶�Ϊ��λ�������ݿ�����

```
int IBTSExecuteSchedule_BT_PC_BP_AP_AT( char *req_msg_name , int sizeof_req_msg , void *p_req_st
                                        , char *rsp_msg_name , int sizeof_rsp_msg , void *p_rsp_st
                                        , struct IbasAddonFiles *addon_files
                                        , char *trans_code
                                        , char *response_code , int response_code_bufsize
                                        , char *response_desc , int response_desc_bufsize
                                        , struct TransFuncArray  *TF_PC_BF_ResgisterTransTblA1
                                        , struct TransFuncArray  *TF_BC_BF_UpdateTransTblB1
                                        , struct TransSchedule_BT_PC_BP_AP_AT *p_ts )
{
        struct TransEnv         *p_te = NULL ;

        int                     nret = 0 ;

        /* �������״����� */
        p_te = IBTMCreateTransEnv( req_msg_name , sizeof_req_msg , p_req_st
                                        , rsp_msg_name , sizeof_rsp_msg , p_rsp_st
                                        , addon_files
                                        , trans_code
                                        , response_code , response_code_bufsize
                                        , response_desc , response_desc_bufsize ) ;
        if( p_te == NULL )
        {
                ERRORLOGG( "CreateTransEnv failed , errno[%d]" , errno );
                return IBP_IBTM_ERROR_ALLOC;
        }

        /* ִ�мƻ� */
        nret = IBTSRecursiveSchedule_BT_PC_BP_AP_AT( p_te , TF_PC_BF_ResgisterTransTblA1 , TF_BC_BF_UpdateTransTblB1 , p_ts ) ;
        if( nret )
        {
                ERRORLOGSG( "IBTSRecursiveSchedule_BT_PC_BP_AP_AT failed[%d]" , nret );
                IBTMFormatResponseInfo( p_te , 999999 , "����ʧ��" );
        }
        else
        {
                INFOLOGSG( "IBTSRecursiveSchedule_BT_PC_BP_AP_AT ok" );
                IBTMFormatResponseInfo( p_te , 0 , "���׳ɹ�" );

        }

        /* ���ٽ��״����� */
        IBTMDestroyTransEnv( p_te );

        return 0;
}

int IBTSRecursiveSchedule_BT_PC_BP_AP_AT( struct TransEnv *p_te , struct TransFuncArray  *TF_PC_BF_ResgisterTransTblA1
                                        , struct TransFuncArray  *TF_BC_BF_UpdateTransTblB1
                                        , struct TransSchedule_BT_PC_BP_AP_AT *p_ts )
{
        int             nret = 0 ;

        if( TF_PC_BF_ResgisterTransTblA1 == NULL )
        {
                ERRORLOGG( "TF_PC_BF_ResgisterTransTblA1 IS NOT NULL" );
                return IBP_IBTS_ERROR_PARAMETER ;
        }
        TFA_BT_RegistTransList[1].func_array = TF_PC_BF_ResgisterTransTblA1 ;

        if( TF_BC_BF_UpdateTransTblB1 == NULL )
        {
                ERRORLOGG( "TF_PC_BF_ResgisterTransTblA1 IS NOT NULL" );
                return IBP_IBTS_ERROR_PARAMETER ;
        }
        TFA_BT_PC_BP_AT_UpdateTransList[1].func_array = TF_BC_BF_UpdateTransTblB1 ;

        DBBEGINWORK

        /* ����ǰ���� �׶� */
        nret = IBTMExecuteFuncArray( p_te , p_ts->before_trans_desc , p_ts->before_trans_funcarray ) ;
        IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT(return 0;)

        DBCOMMIT

        DBBEGINWORK

        /* �Ǽ���ˮ�� */
        nret = IBTMExecuteFuncArray( p_te , "�Ǽ���ˮ��" ,  TFA_BT_RegistTransList ) ;
        IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT(return 0;)

        DBCOMMIT

        do
        {
                DBBEGINWORK

                /* ����������� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->PC.channel_public_check_desc , p_ts->PC.channel_public_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT(break;)

                /* ����Ա������� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->PC.oper_public_check_desc , p_ts->PC.oper_public_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT(break;)

                /* ����������� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->PC.org_public_check_desc , p_ts->PC.org_public_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT(break;)

                /* ����������� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->PC.other_public_check_desc , p_ts->PC.other_public_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT(break;)

                DBCOMMIT

                DBBEGINWORK

                /* ���ʲ�ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BC.media_busi_check_desc , p_ts->BC.media_busi_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* �˻���ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BC.account_busi_check_desc , p_ts->BC.account_busi_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* �ͻ���ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BC.customer_busi_check_desc , p_ts->BC.customer_busi_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* ҵ���ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BC.business_busi_check_desc , p_ts->BC.business_busi_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* ����ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BC.other_busi_check_desc , p_ts->BC.other_busi_check_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                DBCOMMIT

                DBBEGINWORK

                /* ���ʲ�ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BP.media_busi_process_desc , p_ts->BP.media_busi_process_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* �˻���ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BP.account_busi_process_desc , p_ts->BP.account_busi_process_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* �ͻ���ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BP.customer_busi_process_desc , p_ts->BP.customer_busi_process_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* ҵ���ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BP.business_busi_process_desc , p_ts->BP.business_busi_process_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* ����ҵ���� �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->BP.other_busi_process_desc , p_ts->BP.other_busi_process_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                /* ������ �׶� */
                nret = IBTMExecuteFuncArray( p_te , p_ts->account_process_desc , p_ts->account_process_funcarray ) ;
                IF_RET_LT_ROLLBACK_RETURN_GT_ROLLBACK(break;)

                DBCOMMIT
        }
        while(0);

        /* ���׺��� �׶� */
        DBBEGINWORK

        nret = IBTMExecuteFuncArray( p_te , p_ts->after_trans_desc , p_ts->after_trans_funcarray ) ;
        IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT()

        DBCOMMIT


        DBBEGINWORK

        /* ����IBP��ˮ��ecif��ˮ�� */
        /* ����IBP��ˮ�� */
        nret = IBTMExecuteFuncArray( p_te , "����IBP������ˮ��" ,  TFA_BT_PC_BP_AT_UpdateTransList ) ;
        IF_RET_LT_ROLLBACK_RETURN_GT_COMMIT(return 0;)

        DBCOMMIT

        return 0;
}
```

�ֽ׶�ģ��������ÿ���׶ιҽӵ�TM������

```
struct TransSchedule_BT_PC_BP_AP_AT     TS_TESTTPS1 =
        {
                "����ǰ����" , TFA_BT_TESTTPS1 ,
                {
                        "�����������" , TFA_PC_CH_TESTTPS1 ,
                        "����Ա�������" , TFA_PC_OP_TESTTPS1 ,
                        "�����������" , TFA_PC_OG_TESTTPS1 ,
                        "�����������" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , TFA_BC_MD_TESTTPS1 ,
                        "�˻���ҵ����" , TFA_BC_AT_TESTTPS1 ,
                        "�ͻ���ҵ����" , TFA_BC_CT_TESTTPS1 ,
                        "ҵ���ҵ����" , TFA_BC_BS_TESTTPS1 ,
                        "����ҵ����" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , TFA_BP_MD_TESTTPS1 ,
                        "�˻���ҵ����" , TFA_BP_AT_TESTTPS1 ,
                        "�ͻ���ҵ����" , TFA_BP_CT_TESTTPS1 ,
                        "ҵ���ҵ����" , TFA_BP_BS_TESTTPS1 ,
                        "����ҵ����" , NULL
                } ,
                "������" , TFA_AP_TESTTPS1 ,
                "���׺���" , TFA_AT_TESTTPS1
        } ;
```

���ִ�е�ҵ�񿪷���Ա����ҵ���߼���װ��TM���������������£�

```
struct TransFuncArray   TFA_BP_BS_TESTTPS1[] =
        {
                FUNC( "ҵ������1" , TF_BP_BS_TESTTPS1_F1 )
                FUNCARRAY( "ҵ����������2" , TFA_BP_TESTTPS1_FA2 )
                IF_IN_TRANSCODES_THEN_FUNC( "ҵ����������3" , "TESTTPS1" , TF_BP_BS_TESTTPS1_F3 )
                IF_NOTIN_TRANSCODES_THEN_FUNCARRAY( "ҵ����������0" , "TESTTPS1" , TFA_BP_BS_TESTTPS1_FA0 )
                IF_FUNC_THEN( "ҵ������4" , TF_BP_BS_TESTTPS1_F4 )
                        FUNC( "ҵ������5" , TF_BP_BS_TESTTPS1_F5 )
                ELSE
                        FUNC( "ҵ������0" , TF_BP_BS_TESTTPS1_F0 )
                ENDIF
                IF_FUNCARRAY_THEN( "ҵ����������6" , TFA_BP_BS_TESTTPS1_FA6 )
                        FUNC( "ҵ������0" , TF_BP_BS_TESTTPS1_F0 )
                ELSE
                        FUNC( "ҵ������7" , TF_BP_BS_TESTTPS1_F7 )
                ENDIF
                FUNC( "ҵ������8" , TF_BP_BS_TESTTPS1_F8 )
                RETURN
        } ;

TransFunc TF_BP_BS_TESTTPS1_F8 ;
int TF_BP_BS_TESTTPS1_F8( struct TransEnv *p_te )
{
        test_ibpts1_request     *p_req_msg = NULL ;
        test_ibpts1_response    *p_rsp_msg = NULL ;

        int                     nret = 0 ;

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

        strcpy( p_rsp_msg->test_ibpts1.account_no , p_req_msg->test_ibpts1.account_no );

        return 0;
}
```

## 3.2. Ԥ�÷ֽ׶�ģ��

IBP���׹�����Ŀǰ�ṩ�������ֽ׶�ģ�壬�Ժ�����Ҫ���Բ������ģ��

��ͨI�ͣ�

```
struct TransSchedule_BT_PC_BP_AP_AT     TS_ =
        {
                "����ǰ����" , NULL ,
                {
                        "�����������" , NULL ,
                        "����Ա�������" , NULL ,
                        "�����������" , NULL ,
                        "�����������" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , NULL ,
                        "�˻���ҵ����" , NULL ,
                        "�ͻ���ҵ����" , NULL ,
                        "ҵ���ҵ����" , NULL ,
                        "����ҵ����" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , NULL ,
                        "�˻���ҵ����" , NULL ,
                        "�ͻ���ҵ����" , NULL ,
                        "ҵ���ҵ����" , NULL ,
                        "����ҵ����" , NULL
                } ,
                "������" , NULL ,
                "���׺���" , NULL
        } ;
```

���׷��غ������������ͣ�

```
struct TransSchedule_BT_PC_BP_AP_AT     TS_ =
        {
                "����ǰ����" , NULL ,
                {
                        "�����������" , NULL ,
                        "����Ա�������" , NULL ,
                        "�����������" , NULL ,
                        "�����������" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , NULL ,
                        "�˻���ҵ����" , NULL ,
                        "�ͻ���ҵ����" , NULL ,
                        "ҵ���ҵ����" , NULL ,
                        "����ҵ����" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , NULL ,
                        "�˻���ҵ����" , NULL ,
                        "�ͻ���ҵ����" , NULL ,
                        "ҵ���ҵ����" , NULL ,
                        "����ҵ����" , NULL
                } ,
                "���׺���" , NULL ,
                "������" , NULL
        } ;
```

������ǰ�����������������ͣ�

```
struct TransSchedule_BT_PC_BP_AP_AT     TS_ =
        {
                "����ǰ����" , NULL ,
                {
                        "�����������" , NULL ,
                        "����Ա�������" , NULL ,
                        "�����������" , NULL ,
                        "�����������" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , NULL ,
                        "�˻���ҵ����" , NULL ,
                        "�ͻ���ҵ����" , NULL ,
                        "ҵ���ҵ����" , NULL ,
                        "����ҵ����" , NULL
                } ,
                {
                        "���ʲ�ҵ����" , NULL ,
                        "�˻���ҵ����" , NULL ,
                        "�ͻ���ҵ����" , NULL ,
                        "ҵ���ҵ����" , NULL ,
                        "����ҵ����" , NULL
                } ,
                "��������" , NULL , 
                "������" , NULL ,
                "���׺���" , NULL
        } ;
```
