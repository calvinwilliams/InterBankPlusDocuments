�ֲ�ʽ�������������(IBP)�����ʵս�����������ӿڲο���
=========================================

| �汾�� | �޶����� | �޶��� | ���� |
| --- | --- | --- | --- |
| 0.0.1.0 | 2018-01-28 | ���� | ���� |

<!-- TOC -->

- [1. API�ӿ�](#1-api�ӿ�)
    - [1.1. ����API�ӿ�](#11-����api�ӿ�)
        - [1.1.1. �ļ���](#111-�ļ���)
            - [1.1.1.1. IBPCreateTempFile](#1111-ibpcreatetempfile)
    - [1.2. ע�����API�ӿ�](#12-ע�����api�ӿ�)
        - [1.2.1. ������](#121-������)
            - [1.2.1.1. IBMAOpenConfigSpace](#1211-ibmaopenconfigspace)
            - [1.2.1.2. IBMACheckConfigSpaceAttaching](#1212-ibmacheckconfigspaceattaching)
            - [1.2.1.3. IBMACloseConfigSpace](#1213-ibmacloseconfigspace)
            - [1.2.1.4. IBMAGetConfigSpaceAttaching](#1214-ibmagetconfigspaceattaching)
            - [1.2.1.5. IBMAGetThisNodePtr](#1215-ibmagetthisnodeptr)
            - [1.2.1.6. IBMAGetRetryConnectTimeval](#1216-ibmagetretryconnecttimeval)
            - [1.2.1.7. IBMAGetMinCompressSize](#1217-ibmagetmincompresssize)
            - [1.2.1.8. IBMAGetIbmsServerIp](#1218-ibmagetibmsserverip)
            - [1.2.1.9. IBMAGetIbmsServerPort](#1219-ibmagetibmsserverport)
        - [1.2.2. ͨѶ�ڵ���](#122-ͨѶ�ڵ���)
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
        - [1.2.3. ͨѶ�ڵ�������Ⱥ��](#123-ͨѶ�ڵ�������Ⱥ��)
            - [1.2.3.1. IBMATravelNodeHosts](#1231-ibmatravelnodehosts)
            - [1.2.3.2. IBMAQueryNodeHost](#1232-ibmaquerynodehost)
            - [1.2.3.3. IBMAGetHostIpPtr](#1233-ibmagethostipptr)
            - [1.2.3.4. IBMAGetHostPort](#1234-ibmagethostport)
            - [1.2.3.5. IBMAGetHostLoad](#1235-ibmagethostload)
            - [1.2.3.6. IBMASetHostLoad](#1236-ibmasethostload)
            - [1.2.3.7. IBMAGetHostInvalid](#1237-ibmagethostinvalid)
            - [1.2.3.8. IBMAGetHostRetryConnectTimestamp](#1238-ibmagethostretryconnecttimestamp)
        - [1.2.4. ��������Ϣ��](#124-��������Ϣ��)
            - [1.2.4.1. IBMAGetAppCount](#1241-ibmagetappcount)
            - [1.2.4.2. IBMATravelApps](#1242-ibmatravelapps)
            - [1.2.4.3. IBMAQueryApp](#1243-ibmaqueryapp)
            - [1.2.4.4. IBMAGetAppPtr](#1244-ibmagetappptr)
            - [1.2.4.5. IBMAGetAppDescPtr](#1245-ibmagetappdescptr)
            - [1.2.4.6. IBMAGetAppBinPtr](#1246-ibmagetappbinptr)
            - [1.2.4.7. IBMAGetAppTimeout](#1247-ibmagetapptimeout)
            - [1.2.4.8. IBMAGetAppTimeout2](#1248-ibmagetapptimeout2)
            - [1.2.4.9. IBMAGetAppServerNodePtr](#1249-ibmagetappservernodeptr)
        - [1.2.5. Ӧ���Զ���KV������](#125-Ӧ���Զ���kv������)
            - [1.2.5.1. IBMATravelNodeKvs](#1251-ibmatravelnodekvs)
            - [1.2.5.2. IBMAQueryNodekv](#1252-ibmaquerynodekv)
            - [1.2.5.3. IBMAGetKvKeyPtr](#1253-ibmagetkvkeyptr)
            - [1.2.5.4. IBMAGetKvValuePtr](#1254-ibmagetkvvalueptr)
            - [1.2.5.5. IBMAGetNodeKvCount](#1255-ibmagetnodekvcount)
    - [1.3. ͨѶ�ͻ���API�ӿ�](#13-ͨѶ�ͻ���api�ӿ�)
        - [1.3.1. ������](#131-������)
            - [1.3.1.1. IBACCreateEnvirment](#1311-ibaccreateenvirment)
            - [1.3.1.2. IBACDestroyEnvirment](#1312-ibacdestroyenvirment)
            - [1.3.1.3. IBACCreateMultiEnvirments](#1313-ibaccreatemultienvirments)
            - [1.3.1.4. IBACDestroyMultiEnvirments](#1314-ibacdestroymultienvirments)
        - [1.3.2. �����ࣨ�в㣩](#132-�������в�)
            - [1.3.2.1. IBACRequester](#1321-ibacrequester)
        - [1.3.3. �����ࣨ�Ͳ㣩](#133-������Ͳ�)
            - [1.3.3.1. IBACConnect](#1331-ibacconnect)
            - [1.3.3.2. IBACSendRequestAndReceiveResponse](#1332-ibacsendrequestandreceiveresponse)
            - [1.3.3.3. IBACDisconnect](#1333-ibacdisconnect)
            - [1.3.3.4. IBACMultiConnect](#1334-ibacmulticonnect)
            - [1.3.3.5. IBACMultiSendRequestsAndReceiveResponses](#1335-ibacmultisendrequestsandreceiveresponses)
            - [1.3.3.6. IBACMultiSendCommitOrRollbackAndReceiveResponses](#1336-ibacmultisendcommitorrollbackandreceiveresponses)
            - [1.3.3.7. IBACMultiDisconnect](#1337-ibacmultidisconnect)
    - [1.4. ͨѶ�����API�ӿ�](#14-ͨѶ�����api�ӿ�)
        - [1.4.1. ��Ϣ��ѯ��](#141-��Ϣ��ѯ��)
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
        - [1.4.2. ������](#142-������)
            - [1.4.2.1. IBASGetHttpEnv](#1421-ibasgethttpenv)
            - [1.4.2.2. IBASSetTransactionAddonInfo](#1422-ibassettransactionaddoninfo)
        - [1.4.3. �����ļ���](#143-�����ļ���)
            - [1.4.3.1. IBASGetRequestFileCount](#1431-ibasgetrequestfilecount)
            - [1.4.3.2. IBASGetRequestFileById](#1432-ibasgetrequestfilebyid)
            - [1.4.3.3. IBASGetResponseFileCount](#1433-ibasgetresponsefilecount)
            - [1.4.3.4. IBASPutResponseFile](#1434-ibasputresponsefile)
            - [1.4.3.5. IBASGetPathFilename](#1435-ibasgetpathfilename)
            - [1.4.3.6. IBASGetEnv](#1436-ibasgetenv)
    - [1.5. ����ת����API�ӿ�](#15-����ת����api�ӿ�)
        - [1.5.1. ���׷�����](#151-���׷�����)
            - [1.5.1.1. IBMSGVSendRequestAndReceiveResponse_JSON](#1511-ibmsgvsendrequestandreceiveresponse_json)
            - [1.5.1.2. IBMSGVRequester_JSON](#1512-ibmsgvrequester_json)
            - [1.5.1.3. IBMSGVCall_JSON](#1513-ibmsgvcall_json)
        - [1.5.2. ���׽�����](#152-���׽�����)
            - [1.5.2.1. IBMSGVReceiver_JSON](#1521-ibmsgvreceiver_json)
            - [1.5.2.2. IBMSGVReceiver_JSON_SendResponseAhead](#1522-ibmsgvreceiver_json_sendresponseahead)
    - [1.6. ���׹����API�ӿ�](#16-���׹����api�ӿ�)
        - [1.6.1. �ֽ׶�ģ����](#161-�ֽ׶�ģ����)
            - [1.6.1.1. IBTSExecuteSchedule_BT_PC_BP_AP_AT](#1611-ibtsexecuteschedule_bt_pc_bp_ap_at)
            - [1.6.1.2. IBTSRecursiveSchedule_BT_PC_BP_AP_AT](#1612-ibtsrecursiveschedule_bt_pc_bp_ap_at)
            - [1.6.1.3. IBTSExecuteSchedule_BT_PC_RI_BP_AP_AT](#1613-ibtsexecuteschedule_bt_pc_ri_bp_ap_at)
            - [1.6.1.4. IBTSRecursiveSchedule_BT_PC_BP_RI_AP_AT](#1614-ibtsrecursiveschedule_bt_pc_bp_ri_ap_at)
            - [1.6.1.5. IBTSExecuteSchedule_BT_PC_BP_AT__AP](#1615-ibtsexecuteschedule_bt_pc_bp_at__ap)
            - [1.6.1.6. IBTSRecursiveSchedule_BT_PC_BP_AP_AT](#1616-ibtsrecursiveschedule_bt_pc_bp_ap_at)
        - [1.6.2. �õ�������Ϣ��](#162-�õ�������Ϣ��)
            - [1.6.2.1. IBTMGetFuncParaPtr](#1621-ibtmgetfuncparaptr)
        - [1.6.3. ������Ӧ��Ϣ��](#163-������Ӧ��Ϣ��)
            - [1.6.3.1. IBTMFormatResponseCode](#1631-ibtmformatresponsecode)
            - [1.6.3.2. IBTMFormatResponseCode](#1632-ibtmformatresponsecode)
            - [1.6.3.3. IBTMFormatResponseDesc](#1633-ibtmformatresponsedesc)
            - [1.6.3.4. IBTMFormatResponseInfo](#1634-ibtmformatresponseinfo)
        - [1.6.4. �ṹ������](#164-�ṹ������)
            - [1.6.4.1. IBTMAppendStructBlock](#1641-ibtmappendstructblock)
            - [1.6.4.2. IBTMGetStructBlock](#1642-ibtmgetstructblock)
            - [1.6.4.3. IBTMAppendGetStructBlock](#1643-ibtmappendgetstructblock)
        - [1.6.5. ��̬�ṹ����](#165-��̬�ṹ����)
            - [1.6.5.1. DS_NEW](#1651-ds_new)
            - [1.6.5.2. DS_ADD](#1652-ds_add)
            - [1.6.5.3. DS_SET](#1653-ds_set)
            - [1.6.5.4. DS_GET](#1654-ds_get)
        - [1.6.6. ���ݿ������](#166-���ݿ������)
            - [1.6.6.1. OpenDatabaseSessions](#1661-opendatabasesessions)
            - [1.6.6.2. CloseDatabaseSessions](#1662-closedatabasesessions)
            - [1.6.6.3. BeginDatabaseTransaction](#1663-begindatabasetransaction)
            - [1.6.6.4. CommitDatabaseTransaction](#1664-commitdatabasetransaction)
            - [1.6.6.5. RollbackDatabaseTransaction](#1665-rollbackdatabasetransaction)
- [2. ����ʾ��](#2-����ʾ��)
    - [2.1. ����API](#21-����api)
        - [2.1.1. ������ʱ�ļ�](#211-������ʱ�ļ�)
    - [2.2. ͨѶ�ͻ���API](#22-ͨѶ�ͻ���api)
        - [2.2.1. ����ͨѶ�����в㣩](#221-����ͨѶ�����в�)
        - [2.2.2. ����ͨѶ�����в㣩�������ļ���](#222-����ͨѶ�����в㸽���ļ�)
        - [2.2.3. ����ͨѶ���󣨵Ͳ㣩](#223-����ͨѶ����Ͳ�)
    - [2.3. ͨѶ�����API](#23-ͨѶ�����api)
        - [2.3.1. �������](#231-�������)
        - [2.3.2. ������񣨸����ļ���](#232-������񸽴��ļ�)
    - [2.4. ����ת��API](#24-����ת��api)
    - [2.5. ��̬�ṹ����](#25-��̬�ṹ����)
    - [2.6. �ֽ׶ι����API](#26-�ֽ׶ι����api)

<!-- /TOC -->

# 1. API�ӿ�

## 1.1. ����API�ӿ�

### 1.1.1. �ļ���

#### 1.1.1.1. IBPCreateTempFile

| | |
| ---:| --- |
| ����ԭ�ͣ� | FILE *IBPCreateTempFile( char *file_id , char *filename , char *pathfilename , char *mode ); |
| ���������� | ��������Ψһ������ʱ�ļ� |
| ����˵���� | char *file_id �ļ�ID������ǰ��̨��������ļ�ʱָ���ļ���<br />char *filename �����ļ���������������char filename[ IBP_MAXLEN_FILENAME + 1 ] ;���������ΪNULL����������ʱ�����<br />char *pathfilename ��·���ĸ����ļ���������������char filename[ IBP_MAXLEN_FILENAME + 1 ] ;���������ΪNULL����������ʱ�����<br />char *mode fopen��ģʽ���ı��ļ���"w"���������ļ���"b" |
| ����ֵ�� | ���ط�NULL��ʾ�ɹ���ֵΪ��FILEָ�룻����NULL��ʾʧ�� |
| | |

## 1.2. ע�����API�ӿ�

### 1.2.1. ������

#### 1.2.1.1. IBMAOpenConfigSpace

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct IbmaConfigSpace *IBMAOpenConfigSpace( char *config_filename ); |
| ���������� | �����ù����ڴ� |
| ����˵���� | ��ע������������ļ�config_filename�õ����ù����ڴ�key���������ù����ڴ��������ڴ棬�����ù����ڴ棬���ظþ��ָ�롣<br />��config_filenameΪNULLʱȡȱʡֵ"ibma.conf"��<br />config_filename����·����д��·����"$HOME/etc"�� |
| ����ֵ�� | ���ط�NULL��ʾ�ɹ���ֵΪ�򿪾��ָ�룻����NULL��ʾʧ�� |
| | |

#### 1.2.1.2. IBMACheckConfigSpaceAttaching

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMACheckConfigSpaceAttaching( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | ����Ƿ����¹��������ù����ڴ棬��������л����¹����� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ����� |
| ����ֵ�� | ����1��ʾ�л����ù����ڴ棻0��ʾ�ɹ�����0��ʾʧ�� |
| | |

#### 1.2.1.3. IBMACloseConfigSpace

| | |
| ---:| --- |
| ����ԭ�ͣ� | void IBMACloseConfigSpace( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �ر����ù����ڴ�򿪾�� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | ���ޣ� |
| | |

#### 1.2.1.4. IBMAGetConfigSpaceAttaching

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct ConfigSpaceAttaching *IBMAGetConfigSpaceAttaching( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ����ÿռ������ṹָ�� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | ���ÿռ������ṹ��ַ��ֻ���� |
| | |

#### 1.2.1.5. IBMAGetThisNodePtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetThisNodePtr( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ��Լ�ͨѶ�ڵ��� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | �����Լ�ͨѶ�ڵ�����ֻ���� |
| | |

#### 1.2.1.6. IBMAGetRetryConnectTimeval

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetRetryConnectTimeval( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ��ݽ�ʱ������ |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | �����ݽ�ʱ�����ã�ֻ���� |
| | |

#### 1.2.1.7. IBMAGetMinCompressSize

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetMinCompressSize( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ���Сѹ�����ݴ�С |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | ������Сѹ�����ݴ�С��ֻ��������HTTP�����ݴ��ڵ��ڸ�����ֵʱ�ż���ѹ�� |
| | |

#### 1.2.1.8. IBMAGetIbmsServerIp

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetIbmsServerIp( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ�ע������IP |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | ����ע������IP��ֻ���� |
| | |

#### 1.2.1.9. IBMAGetIbmsServerPort

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetIbmsServerPort( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ�ע������PORT |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | ����ע������PORT��ֻ���� |
| | |

### 1.2.2. ͨѶ�ڵ���

#### 1.2.2.1. IBMAGetNodeCount

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetNodeCount( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ��������ø����е�ͨѶ�ڵ������������Լ��� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | ����ͨѶ�ڵ����� |
| | |

#### 1.2.2.2. IBMAGetThisNode

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct NodeSpaceUnit *IBMAGetThisNode( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ��Լ�ͨѶ�ڵ�ṹ��Ϣ����Ҫͨ������������ȡ���� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | �����Լ�ͨѶ�ڵ�ṹ��Ϣ��ֻ���� |
| | |

#### 1.2.2.3. IBMATravelNodes

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct NodeSpaceUnit *IBMATravelNodes( struct IbmaConfigSpace *ibma_config_space , struct NodeSpaceUnit *p_node_unit ); |
| ���������� | �����������ø���������ͨѶ�ڵ�ṹ��Ϣ����Ҫͨ������������ȡ���� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />struct NodeSpaceUnit *p_node_unit ��һ�α���ֵ����һ������ΪNULL |
| ����ֵ�� | ����ÿ�α�����ͨѶ�ڵ�ṹ��Ϣ��ֻ���� |
| | |

#### 1.2.2.4. IBMAQueryNode

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct NodeSpaceUnit *IBMAQueryNode( struct IbmaConfigSpace *ibma_config_space , char *node ); |
| ���������� | ��ѯ�������ø�����ָ�����ֵ�ͨѶ�ڵ�ṹ��Ϣ����Ҫͨ������������ȡ���� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />char *node ָ��ͨѶ�ڵ��� |
| ����ֵ�� | ����ָ�����ֵ�ͨѶ�ڵ�ṹ��Ϣ��ֻ���� |
| | |

#### 1.2.2.5. IBMAGetNodePtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetNodePtr( struct NodeSpaceUnit *p_node_unit ); |
| ���������� | ��ͨѶ�ڵ�ṹ��Ϣ�л�ȡ�ڵ��� |
| ����˵���� | struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ |
| ����ֵ�� | ���ؽڵ�����ֻ���� |
| | |

#### 1.2.2.6. IBMAGetNodeInvalid

| | |
| ---:| --- |
| ����ԭ�ͣ� | char IBMAGetNodeInvalid( struct NodeSpaceUnit *p_node_unit ); |
| ���������� | ��ͨѶ�ڵ�ṹ��Ϣ�л�ȡ�ڵ��Ƿ񱻽��� |
| ����˵���� | struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ |
| ����ֵ�� | ����0��ʾ�ýڵ���ã����ط�0��ʾ�ýڵ���� |
| | |

#### 1.2.2.7. IBMAGetNodeHostCount

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetNodeHostCount( struct NodeSpaceUnit *p_node_unit ); |
| ���������� | ��ͨѶ�ڵ�ṹ��Ϣ�л�ȡ�ڵ��������Ⱥ���� |
| ����˵���� | struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ |
| ����ֵ�� | ����������Ⱥ���� |
| | |

#### 1.2.2.8. IBMAGetNodeEncryptKeyExpPtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetNodeEncryptKeyExpPtr( struct NodeSpaceUnit *p_node_unit ) |
| ���������� | ��ͨѶ�ڵ�ṹ��Ϣ�л�ȡ�ڵ��ͨѶ�ڵ���Կ |
| ����˵���� | struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ |
| ����ֵ�� | ����ͨѶ�ڵ���Կ |
| | |

#### 1.2.2.9. IBMAGetNodeOldKeyDisableTimestamp

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetNodeOldKeyDisableTimestamp( struct NodeSpaceUnit *p_node_unit ) |
| ���������� | ��ͨѶ�ڵ�ṹ��Ϣ�л�ȡ�ڵ�ľ���ԿʧЧʱ��� |
| ����˵���� | struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ |
| ����ֵ�� | ���ؾ���ԿʧЧʱ��� |
| | |

#### 1.2.2.10. IBMAGetNodeNewKeyEnableTimestamp

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetNodeNewKeyEnableTimestamp( struct NodeSpaceUnit *p_node_unit ) |
| ���������� | ��ͨѶ�ڵ�ṹ��Ϣ�л�ȡ�ڵ������Կ��Чʱ��� |
| ����˵���� | struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ |
| ����ֵ�� | ��������Կ��Чʱ��� |
| | |

### 1.2.3. ͨѶ�ڵ�������Ⱥ��

#### 1.2.3.1. IBMATravelNodeHosts

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct HostSpaceUnit *IBMATravelNodeHosts( struct IbmaConfigSpace *ibma_config_space , struct NodeSpaceUnit *p_node_unit , struct HostSpaceUnit *p_host_unit ); |
| ���������� | �����������ø����е�ָ��ͨѶ�ڵ��������Ϣ |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ<br />struct HostSpaceUnit *p_host_unit ��һ��������Ϣ�ṹָ�룬��һ������ΪNULL |
| ����ֵ�� | ����ָ��ͨѶ�ڵ��������Ϣ |
| | |

#### 1.2.3.2. IBMAQueryNodeHost

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct HostSpaceUnit *IBMAQueryNodeHost( struct IbmaConfigSpace *ibma_config_space , struct NodeSpaceUnit *p_node_unit , char *ip , int port ); |
| ���������� | ��ѯָ��ͨѶ�ڵ��������Ϣ�ṹ |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />struct NodeSpaceUnit *p_node_unit ͨѶ�ڵ�ṹ��Ϣ<br />char *ip ����IP<br />int port ����PORT |
| ����ֵ�� | ��ѯָ��ͨѶ�ڵ��������Ϣ |
| | |

#### 1.2.3.3. IBMAGetHostIpPtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetHostIpPtr( struct HostSpaceUnit *p_host_unit ); |
| ���������� | �õ�������Ϣ�ṹ�е�IP |
| ����˵���� | struct HostSpaceUnit *p_host_unit�����ṹ��Ϣ |
| ����ֵ�� | ������Ϣ�ṹIP |
| | |

#### 1.2.3.4. IBMAGetHostPort

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetHostPort( struct HostSpaceUnit *p_host_unit ); |
| ���������� | �õ�������Ϣ�ṹ�е�PORT |
| ����˵���� | struct HostSpaceUnit *p_host_unit �����ṹ��Ϣ |
| ����ֵ�� | ������Ϣ�ṹPORT |
| | |

#### 1.2.3.5. IBMAGetHostLoad

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetHostLoad( struct HostSpaceUnit *p_host_unit ); |
| ���������� | �õ�������Ϣ�ṹ�еĵ�ǰ���� |
| ����˵���� | struct HostSpaceUnit *p_host_unit �����ṹ��Ϣ |
| ����ֵ�� | ������Ϣ�ṹ��ǰ���� |
| | |

#### 1.2.3.6. IBMASetHostLoad

| | |
| ---:| --- |
| ����ԭ�ͣ� | void IBMASetHostLoad( struct HostSpaceUnit *p_host_unit , int load , int loop ); |
| ���������� | ����������Ϣ�ṹ�еĵ�ǰ���� |
| ����˵���� | struct HostSpaceUnit *p_host_unit �����ṹ��Ϣ<br />int load     ����ֵ<br />int loop     �Ƿ�ѭ����־ |
| ����ֵ�� | ����������Ϣ�ṹ�ĸ��� |
| | |

#### 1.2.3.7. IBMAGetHostInvalid

| | |
| ---:| --- |
| ����ԭ�ͣ� | char IBMAGetHostInvalid( struct HostSpaceUnit *p_host_unit ); |
| ���������� | �õ�������Ϣ�ṹ�е���Ч�� |
| ����˵���� | struct HostSpaceUnit *p_host_unit �����ṹ��Ϣ |
| ����ֵ�� | ������Ϣ�ṹ��Ч�� |
| | |

#### 1.2.3.8. IBMAGetHostRetryConnectTimestamp

| | |
| ---:| --- |
| ����ԭ�ͣ� | time_t IBMAGetHostRetryConnectTimestamp( struct HostSpaceUnit *p_host_unit ); |
| ���������� | �õ���������ʱ��� |
| ����˵���� | struct HostSpaceUnit *p_host_unit �����ṹ��Ϣ |
| ����ֵ�� | ��������ʱ��� |
| | |

### 1.2.4. ��������Ϣ��

#### 1.2.4.1. IBMAGetAppCount

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetAppCount( struct IbmaConfigSpace *ibma_config_space ); |
| ���������� | �õ��������ø����еĽ����������������Լ��� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ��� |
| ����ֵ�� | ���ؽ��������� |
| | |

#### 1.2.4.2. IBMATravelApps

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct AppSpaceUnit *IBMATravelApps( struct IbmaConfigSpace *ibma_config_space , struct AppSpaceUnit *p_app_unit ); |
| ���������� | �����������ø��������н�����ṹ��Ϣ����Ҫͨ������������ȡ���� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />struct AppSpaceUnit *p_app_unit ��һ�α���ֵ����һ������ΪNULL |
| ����ֵ�� | ����ÿ�α����Ľ�����ṹ��Ϣ��ֻ���� |
| | |

#### 1.2.4.3. IBMAQueryApp

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct AppSpaceUnit *IBMAQueryApp( struct IbmaConfigSpace *ibma_config_space , char *app ); |
| ���������� | ��ѯ�������ø�����ָ�����ֵĽ�����ṹ��Ϣ����Ҫͨ������������ȡ���� |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />char *app ָ�������� |
| ����ֵ�� | ����ָ�����ֵĽ�����ṹ��Ϣ��ֻ���� |
| | |

#### 1.2.4.4. IBMAGetAppPtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetAppPtr( struct AppSpaceUnit *p_app_unit ); |
| ���������� | �õ���������Ϣ�ṹ�е�IP |
| ����˵���� | struct AppSpaceUnit *p_app_unit ��������Ϣ�ṹ |
| ����ֵ�� | ��������Ϣ�ṹ�еĽ����� |
| | |

#### 1.2.4.5. IBMAGetAppDescPtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetAppDescPtr( struct AppSpaceUnit *p_app_unit ); |
| ���������� | �õ���������Ϣ�ṹ�е����� |
| ����˵���� | struct AppSpaceUnit *p_app_unit ��������Ϣ�ṹ |
| ����ֵ�� | ��������Ϣ�ṹ�е����� |
| | |

#### 1.2.4.6. IBMAGetAppBinPtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetAppBinPtr( struct AppSpaceUnit *p_app_unit ); |
| ���������� | �õ���������Ϣ�ṹ�е�Ӧ�ð��� |
| ����˵���� | struct AppSpaceUnit *p_app_unit ��������Ϣ�ṹ |
| ����ֵ�� | ��������Ϣ�ṹ�е�Ӧ�ð��� |
| | |

#### 1.2.4.7. IBMAGetAppTimeout

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetAppTimeout( struct AppSpaceUnit *p_app_unit ); |
| ���������� | �õ���������Ϣ�ṹ�еĳ�ʱֵ |
| ����˵���� | struct AppSpaceUnit *p_app_unit ��������Ϣ�ṹ |
| ����ֵ�� | ��������Ϣ�ṹ�еĳ�ʱֵ<br /> |
| | |

#### 1.2.4.8. IBMAGetAppTimeout2

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetAppTimeout2( struct AppSpaceUnit *p_app_unit ); |
| ���������� | �õ���������Ϣ�ṹ�е�timeout2ֵ |
| ����˵���� | struct AppSpaceUnit *p_app_unit ��������Ϣ�ṹ |
| ����ֵ�� | ��������Ϣ�ṹ�е�timeout2ֵ |
| | |

#### 1.2.4.9. IBMAGetAppServerNodePtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetAppServerNodePtr( struct AppSpaceUnit *p_app_unit ); |
| ���������� | �õ���������Ϣ�ṹ�еķ���ڵ� |
| ����˵���� | struct AppSpaceUnit *p_app_unit ��������Ϣ�ṹ |
| ����ֵ�� | ��������Ϣ�ṹ�еķ���ڵ� |
| | |

### 1.2.5. Ӧ���Զ���KV������

#### 1.2.5.1. IBMATravelNodeKvs

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct KvSpaceUnit *IBMATravelNodeKvs( struct IbmaConfigSpace *ibma_config_space , struct KvSpaceUnit *p_kv_unit ); |
| ���������� | �����������ø����еı��ڵ��key-value��Ϣ |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />struct KvSpaceUnit * p_kv_unit ��һ��key-value��Ϣ�ṹָ�룬��һ������ΪNULL |
| ����ֵ�� | �������ڵ��key-value��Ϣ |
| | |

#### 1.2.5.2. IBMAQueryNodekv

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct KvSpaceUnit *IBMAQueryNodekv( struct IbmaConfigSpace *ibma_config_space , char *p_kv_key ); |
| ���������� | ��ѯ���ڵ��key-value��Ϣ�ṹ |
| ����˵���� | struct IbmaConfigSpace *ibma_config_space ���ù����ڴ���<br />char *p_kv_key  key-value��key��Ϣ |
| ����ֵ�� | ��ѯ���ڵ��key-value��Ϣ |
| | |

#### 1.2.5.3. IBMAGetKvKeyPtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetKvKeyPtr( struct KvSpaceUnit *p_kv_unit ); |
| ���������� | �õ�key-value��Ϣ�ṹ�е�key |
| ����˵���� | struct KvSpaceUnit * p_kv_unit   key-value�ṹ��Ϣ |
| ����ֵ�� | key-value�ṹ�е�key |
| | |

#### 1.2.5.4. IBMAGetKvValuePtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBMAGetKvValuePtr( struct KvSpaceUnit *p_kv_unit ); |
| ���������� | �õ�key-value��Ϣ�ṹ�е�value |
| ����˵���� | struct KvSpaceUnit * p_kv_unit   key-value�ṹ��Ϣ |
| ����ֵ�� | key-value�ṹ�е�value |
| | |

#### 1.2.5.5. IBMAGetNodeKvCount

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMAGetNodeKvCount( struct NodeSpaceUnit *p_node_unit ); |
| ���������� | �õ��������ø����е�key-value�����������Լ��� |
| ����˵���� | struct NodeSpaceUnit *p_node_unitͨѶ�ڵ�ṹ��Ϣ |
| ����ֵ�� | ���ر��ڵ�key-value��Ϣ |
| | |

## 1.3. ͨѶ�ͻ���API�ӿ�

### 1.3.1. ������

#### 1.3.1.1. IBACCreateEnvirment

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct IbacApiEnv *IBACCreateEnvirment( char *config_filename ); |
| ���������� | ����ͨѶ�ͻ���API���� |
| ����˵���� | char *config_filename ע������������ļ� |
| ����ֵ�� | �ɹ��򷵻�ͨѶ�ͻ���API������ʧ���򷵻�NULL |
| | |

#### 1.3.1.2. IBACDestroyEnvirment

| | |
| ---:| --- |
| ����ԭ�ͣ� | void IBACDestroyEnvirment( struct IbacApiEnv *p_env ); |
| ���������� | ����ͨѶ�ͻ���API���� |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ���API�����ṹ |
| ����ֵ�� | ���ޣ� |
| | |

#### 1.3.1.3. IBACCreateMultiEnvirments

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct IbacMultiEnvs *IBACCreateMultiEnvirments( char *config_filename , int count ); |
| ���������� | ����ͨѶ�ͻ��˲��н���API���� |
| ����˵���� | char *config_filename ע������������ļ�<br />int count ���н������� |
| ����ֵ�� | �ɹ��򷵻�ͨѶ�ͻ��˲��н���API������ʧ���򷵻�NULL |
| | |

#### 1.3.1.4. IBACDestroyMultiEnvirments

| | |
| ---:| --- |
| ����ԭ�ͣ� | void IBACDestroyMultiEnvirments( struct IbacMultiEnvs *p_multi_envs ); |
| ���������� | ����ͨѶ�ͻ��˲��н���API���� |
| ����˵���� | struct IbacMultiEnvs *p_multi_env ͨѶ�ͻ��˲��н���API�����ṹ |
| ����ֵ�� | ���ޣ� |
| | |

### 1.3.2. �����ࣨ�в㣩

#### 1.3.2.1. IBACRequester

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBACRequester( struct IbacApiEnv *p_env , char *node , char *app , char **pp_msg , int *p_msg_len , ... ); |
| ���������� | ���ӷ���ˣ����ͽ��ս��ף��Ͽ����� |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ��˻����ṹ<br />char *node �����ͨѶ�ڵ���<br />char *app ������<br />char **pp_msg ����ʱָ���������׵�ַ��ָ�룬���ʱָ����Ӧ�����׵�ַ��ָ��<br />int *p_msg_len ����ʱ��������Ĵ�С�����ʱ�����Ӧ���Ĵ�С<br />... �����ļ����ַ����б����Ӧ�ļ����ַ����б���������Ӧ�ļ�ʱ��"NULL,NULL"����һ�������ļ�����Ӧ�ļ�ʱ��"req_pathfilename,NULL,NULL"���������ļ���һ����Ӧ�ļ�ʱ��"NULL,rsp_pathfilename,NULL"��ͬʱ��������Ӧ�ļ�ʱ��"req_pathfilename,NULL,rsp_pathfilename,NULL"��������ַ���Ϊ�������� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

### 1.3.3. �����ࣨ�Ͳ㣩

#### 1.3.3.1. IBACConnect

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBACConnect( struct IbacApiEnv *ibac_api_env , char *node ); |
| ���������� | ���ӷ�������� |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ��˻����ṹ<br />char *node �����ͨѶ�ڵ��� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.3.3.2. IBACSendRequestAndReceiveResponse

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBACSendRequestAndReceiveResponse( struct IbacApiEnv *ibac_api_env , char *app , char **pp_msg , int *p_msg_len , ... ); |
| ���������� | �������󵽷����������ͬ��������Ӧ |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ��˻����ṹ<br />char *app ������<br />char **pp_msg ����ʱָ���������׵�ַ��ָ�룬���ʱָ����Ӧ�����׵�ַ��ָ��<br />int *p_msg_len ����ʱ��������Ĵ�С�����ʱ�����Ӧ���Ĵ�С<br />... �����ļ����ַ����б����Ӧ�ļ����ַ����б���������Ӧ�ļ�ʱ��"NULL,NULL"����һ�������ļ�����Ӧ�ļ�ʱ��"req_pathfilename,NULL,NULL"���������ļ���һ����Ӧ�ļ�ʱ��"NULL,rsp_pathfilename,NULL"��ͬʱ��������Ӧ�ļ�ʱ��"req_pathfilename,NULL,rsp_pathfilename,NULL"��������ַ���Ϊ�������� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.3.3.3. IBACDisconnect

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBACDisconnect( struct IbacApiEnv *ibac_api_env ); |
| ���������� | �Ͽ���������� |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ��˻����ṹ |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.3.3.4. IBACMultiConnect

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBACMultiConnect( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters ); |
| ���������� | ��������ͨѶ����� |
| ����˵���� | struct IbacMultiEnvs *p_multi_envsͨѶ�ͻ��˲��н���API�����ṹ<br />struct IbacMultiRequesters *multi_requesters ���н������� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.3.3.5. IBACMultiSendRequestsAndReceiveResponses

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBACMultiSendRequestsAndReceiveResponses( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters ); |
| ���������� | ���Ͳ��н������󲢽�����Ӧ |
| ����˵���� | struct IbacMultiEnvs *p_multi_envsͨѶ�ͻ��˲��н���API�����ṹ<br />struct IbacMultiRequesters *multi_requesters ���н������� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.3.3.6. IBACMultiSendCommitOrRollbackAndReceiveResponses

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBACMultiSendCommitOrRollbackAndReceiveResponses( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters , int commit_or_rollback_flag ); |
| ���������� | ���Ͷ��׶��ύ��ع����󲢽�����Ӧ |
| ����˵���� | struct IbacMultiEnvs *p_multi_envsͨѶ�ͻ��˲��н���API�����ṹ<br />struct IbacMultiRequesters *multi_requesters ���н�������<br />int commit_or_rollback_flag �����ύ��IBAC_MULTI_COMMIT_DATABASE �� ���лع���IBAC_MULTI_ROLLBACK_DATABASE |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.3.3.7. IBACMultiDisconnect

| | |
| ---:| --- |
| ����ԭ�ͣ� | void IBACMultiDisconnect( struct IbacMultiEnvs *p_multi_envs , struct IbacMultiRequesters *multi_requesters ); |
| ���������� | ���жϿ�ͨѶ����� |
| ����˵���� | struct IbacMultiEnvs *p_multi_envsͨѶ�ͻ��˲��н���API�����ṹ<br />struct IbacMultiRequesters *multi_requesters ���н������� |
| ����ֵ�� | ���ޣ� |
| | |

## 1.4. ͨѶ�����API�ӿ�

### 1.4.1. ��Ϣ��ѯ��

#### 1.4.1.1. IBASGetThisNode

| | |
| ---:| --- |
| ����ԭ�ͣ� | const char *IBASGetThisNode( struct IbasEnv *p_env ); |
| ���������� | �õ���ͨѶ�ڵ��� |
| ����˵���� | struct IbasEnv *p_env ͨѶ����˻����ṹ |
| ����ֵ�� | ��ͨѶ�ڵ�����ֻ���� |
| | |

#### 1.4.1.2. IBASGetThisApp

| | |
| ---:| --- |
| ����ԭ�ͣ� | const char *IBASGetThisApp( struct IbasEnv *p_env ); |
| ���������� | �õ���ǰ������ |
| ����˵���� | struct IbasEnv *p_env ͨѶ����˻����ṹ |
| ����ֵ�� | ��ǰ�����루ֻ���� |
| | |

#### 1.4.1.3. IBASSendResponseAhead

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASSendResponseAhead(); |
| ���������� | ��ǰ������Ӧ |
| ����˵���� | ���ޣ� |
| ����ֵ�� | 0��ʾ�ɹ�����0��ʾʧ�� |
| | |

#### 1.4.1.4. IBASGetClientNode

| | |
| ---:| --- |
| ����ԭ�ͣ� | const char *IBASGetClientNode(); |
| ���������� | �õ��ͻ��˽ڵ� |
| ����˵���� | ���ޣ� |
| ����ֵ�� | �ͻ��˽ڵ� |
| | |

#### 1.4.1.5. IBASGetClientIp

| | |
| ---:| --- |
| ����ԭ�ͣ� | const char *IBASGetClientIp(); |
| ���������� | �õ��ͻ���IP |
| ����˵���� | ���ޣ� |
| ����ֵ�� | �ͻ��˽ڵ� |
| | |

#### 1.4.1.6. IBASGetClientPort

| | |
| ---:| --- |
| ����ԭ�ͣ� | const int  IBASGetClientPort() |
| ���������� | �õ��ͻ��˷��ʶ˿� |
| ����˵���� | ���ޣ� |
| ����ֵ�� | �ͻ��˷��ʶ˿� |
| | |

#### 1.4.1.7. IBASGetCommJnlsno

| | |
| ---:| --- |
| ����ԭ�ͣ� | const char *IBASGetCommJnlsno(); |
| ���������� | �õ��ͻ�����ˮ�� |
| ����˵���� | ���ޣ� |
| ����ֵ�� | �ͻ�����ˮ�� |
| | |

#### 1.4.1.8. IBASGetThisAppCommTimeout

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASGetThisAppCommTimeout(); |
| ���������� | �õ��ͻ���ͨѶ��ʱʱ�� |
| ����˵���� | ���ޣ� |
| ����ֵ�� | ͨѶ��ʱʱ�� |
| | |

#### 1.4.1.9. IBASGetThisAppTimeout

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASGetThisAppTimeout(); |
| ���������� | �õ����׳�ʱʱ�� |
| ����˵���� | ���ޣ� |
| ����ֵ�� | ���׳�ʱʱ�� |
| | |

#### 1.4.1.10. IBASGetWorkerIndex

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASGetWorkerIndex(); |
| ���������� | �õ������������ |
| ����˵���� | ���ޣ� |
| ����ֵ�� | ����������� |
| | |

#### 1.4.1.11. IBASGetWorkerProcessCount

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASGetWorkerProcessCount(); |
| ���������� | �õ�����������Ŀ |
| ����˵���� | ���ޣ� |
| ����ֵ�� | ����������Ŀ |
| | |

#### 1.4.1.12. IBASGetResponseBody

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct HttpBuffer *IBASGetResponseBody(); |
| ���������� | �õ���Ӧ������ |
| ����˵���� | ���ޣ� |
| ����ֵ�� | ��Ӧ������ |
| | |

### 1.4.2. ������

#### 1.4.2.1. IBASGetHttpEnv

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct HttpEnv *IBASGetHttpEnv( struct IbasEnv *p_env ); |
| ���������� | �õ�HTTPЭ�黷�� |
| ����˵���� | struct IbasEnv *p_env ͨѶ����˻����ṹ |
| ����ֵ�� | HTTPЭ�黷�� |
| | |

#### 1.4.2.2. IBASSetTransactionAddonInfo

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASSetTransactionAddonInfo( char *busi_channel , char *busi_jnlsno , char *busi_transaction_code , long response_code , char *addon_text ); |
| ���������� | ���ý�����Ӧ��Ϣ |
| ����˵���� | char *busi_channel   ������<br />char *busi_jnlsno     ��ˮ��<br />char *busi_transaction_code  ҵ������<br />long response_code ��Ӧ��<br />char *addon_text ������Ϣ |
| ����ֵ�� | ���ý�����Ӧ��Ϣ |
| | |

### 1.4.3. �����ļ���

#### 1.4.3.1. IBASGetRequestFileCount

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASGetRequestFileCount( struct IbasAddonFiles *addon_files ); |
| ���������� | �õ����󸽴��ļ����� |
| ����˵���� | struct IbasAddonFiles *addon_files �����ļ������� |
| ����ֵ�� | ���󸽴��ļ����� |
| | |

#### 1.4.3.2. IBASGetRequestFileById

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBASGetRequestFileById( struct IbasAddonFiles *addon_files , char *file_id ); |
| ���������� | �õ�ָ���ļ�ID�����󸽴��ļ��� |
| ����˵���� | struct IbasAddonFiles *addon_files �����ļ�������<br />char *file_id |
| ����ֵ�� | ָ���ļ�ID�����󸽴��ļ��� |
| | |

#### 1.4.3.3. IBASGetResponseFileCount

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASGetResponseFileCount( struct IbasAddonFiles *addon_files ); |
| ���������� | �õ���Ӧ�����ļ����� |
| ����˵���� | struct IbasAddonFiles *addon_files �����ļ������� |
| ����ֵ�� | ��Ӧ�����ļ����� |
| | |

#### 1.4.3.4. IBASPutResponseFile

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBASPutResponseFile( struct IbasAddonFiles *addon_files , char *filename ); |
| ���������� | ѹ����Ӧ�����ļ��� |
| ����˵���� | struct IbasAddonFiles *addon_files �����ļ�������<br />char *file_id |
| ����ֵ�� | 0��ʾ�ɹ�����0��ʾʧ�� |
| | |

#### 1.4.3.5. IBASGetPathFilename

| | |
| ---:| --- |
| ����ԭ�ͣ� | void IBASGetPathFilename( char *filename , char *pathfilename , int sizeof_pathfilename ); |
| ���������� | ���������ļ���������׷�Ӿ���·���ĸ����ļ��� |
| ����˵���� | char *filename �����ļ���<br />char *pathfilename ׷�Ӿ���·���ĸ����ļ���<br />int sizeof_pathfilename ׷�Ӿ���·���ĸ����ļ�����������С |
| ����ֵ�� | ���ޣ� |
| | |

#### 1.4.3.6. IBASGetEnv

| | |
| ---:| --- |
| ����ԭ�ͣ� | struct IbasEnv *IBASGetEnv(); |
| ���������� | �õ�ibas�������ṹ |
| ����˵���� | ���ޣ� |
| ����ֵ�� | ibas�������ṹ |
| | |

## 1.5. ����ת����API�ӿ�

### 1.5.1. ���׷�����

#### 1.5.1.1. IBMSGVSendRequestAndReceiveResponse_JSON

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMSGVSendRequestAndReceiveResponse_JSON( struct IbacEnv *p_env , char *app , void *pv_req_st , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , ... ); |
| ���������� | ���JSON���ģ����ͽ���ͨѶ���ģ����JSON���� |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ��˻����ṹ<br />char *app ������<br />void *pv_req_st ����ṹ��<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func���JSON���ĺ���<br />void *pv_rsp_st ��Ӧ�ṹ��<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func ���JSON���ĺ���<br />... �����ļ����ַ����б����Ӧ�ļ����ַ����б������ͨѶ�ͻ���API�� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.5.1.2. IBMSGVRequester_JSON

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMSGVRequester_JSON( struct IbacApiEnv *p_env , char *node , char *app , void *pv_req_st , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , ... ); |
| ���������� | ���ӷ���ˣ����JSON���ģ����ͽ���ͨѶ���ģ����JSON���ģ��Ͽ����� |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ��˻����ṹ<br />char *node �����ͨѶ�ڵ���<br />char *app ������<br />void *pv_req_st ����ṹ��<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func���JSON���ĺ���<br />void *pv_rsp_st ��Ӧ�ṹ��<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func ���JSON���ĺ���<br />... �����ļ����ַ����б����Ӧ�ļ����ַ����б������ͨѶ�ͻ���API�� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.5.1.3. IBMSGVCall_JSON

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMSGVCall_JSON( struct IbacApiEnv *ibac_api_env , char *app , void *pv_req_st , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , ... ); |
| ���������� | ����ͨѶ�ͻ���API���������ӷ���ˣ����JSON���ģ����ͽ���ͨѶ���ģ����JSON���ģ��Ͽ���������ͨѶ�ͻ���API���� |
| ����˵���� | struct IbacApiEnv *p_env ͨѶ�ͻ��˻����ṹ<br />char *app ������<br />void *pv_req_st ����ṹ��<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func���JSON���ĺ���<br />void *pv_rsp_st ��Ӧ�ṹ��<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func ���JSON���ĺ���<br />... �����ļ����ַ����б����Ӧ�ļ����ַ����б������ͨѶ�ͻ���API�� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0<br /> |
| | |

### 1.5.2. ���׽�����

#### 1.5.2.1. IBMSGVReceiver_JSON

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMSGVReceiver_JSON( struct HttpBuffer *req_buf , DSCDESERIALIZE_JSON_xxx_V *p_unpack_func , void *pv_req_st , struct HttpBuffer *rsp_buf , DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st , funcIbmsgvTransmain *p_transmain_func , struct IbasAddonFiles *addon_files ); |
| ���������� | ���JSON���ģ����ûص�����transmain�����JSON���� |
| ����˵���� | struct HttpBuffer *req_buf �����Ļ�����<br />DSCDESERIALIZE_JSON_xxx_V *p_unpack_func ���JSON���ĺ���<br />void *pv_req_st ����ṹ��<br />struct HttpBuffer *rsp_buf ��Ӧ���Ļ�����<br />DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func ���JSON���ĺ���<br />void *pv_rsp_st ��Ӧ�ṹ��<br />funcIbmsgvTransmain *p_transmain_func ���ײ���ڻص�����<br />struct IbasAddonFiles *addon_files �������Ӧ�����ļ���������ͨ��ibas_api������ȡ |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0 |
| | |

#### 1.5.2.2. IBMSGVReceiver_JSON_SendResponseAhead

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBMSGVReceiver_JSON_SendResponseAhead<br />( DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func , void *pv_rsp_st ); |
| ���������� | ���JSON���ģ�ͨѶ������Ӧ |
| ����˵���� | DSCSERIALIZE_JSON_DUP_xxx_V *p_pack_func ���JSON���ĺ���<br />void *pv_rsp_st ��Ӧ�ṹ�� |
| ����ֵ�� | �ɹ���0��ʧ���򷵻ط�0<br /> |
| | |

## 1.6. ���׹����API�ӿ�

### 1.6.1. �ֽ׶�ģ����

#### 1.6.1.1. IBTSExecuteSchedule_BT_PC_BP_AP_AT

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTSExecuteSchedule_BT_PC_BP_AP_AT( char *req_msg_name , int sizeof_req_msg , void *p_req_st , char *rsp_msg_name , int sizeof_rsp_msg , void *p_rsp_st , struct IbasAddonFiles *addon_files , char *trans_code , char *response_code , int response_code_bufsize , char *response_desc , int response_desc_bufsize , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList ,  struct TransSchedule_BT_PC_BP_AP_AT *p_ts ); |
| ���������� | ���ݿ����񣨽���ǰ��������������������׺�����<br />���ݿ����񣨹�����飩����������������׺�����<br />���ݿ�����ҵ���顢ҵ��������������������������׺�����<br />���ݿ����񣨽��׺������������������� |
| ����˵���� | char *req_msg_name ����ṹ������<br />int sizeof_req_msg ����ṹ���С<br />void *p_req_st ����ṹ��<br />char *rsp_msg_name ��Ӧ�ṹ������<br />int sizeof_rsp_msg ��Ӧ�ṹ���С<br />void *p_rsp_st ��Ӧ�ṹ��<br />struct IbasAddonFiles *addon_files �������Ӧ�����ļ�������<br />char *trans_code ҵ������<br />char *response_code ��Ӧ�뻺����<br />int response_code_bufsize ��Ӧ�뻺������С<br />char *response_desc ��Ӧ����������<br />int response_desc_bufsize ��Ӧ������������С<br />TransFunc  *TF_HeaderMapping  ���translist�ṹ����(ע: IB2��IB1���TF_BT_InsertTransListHeaderMapping���ɣ�IB1�Զ���)<br />TransFunc  *TF_InsertTransList  �Ǽ�ҵ����ˮ����<br />TransFunc  *TF_UpdateTransList  ����ҵ����ˮ����<br />struct TransSchedule_BT_PC_BP_AP_AT *p_ts �ֽ׶�ģ������ |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.1.2. IBTSRecursiveSchedule_BT_PC_BP_AP_AT

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTSRecursiveSchedule_BT_PC_BP_AP_AT( struct TransEnv *p_te , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList , struct TransSchedule_BT_PC_BP_AP_AT *p_ts );<br />	<br />	  |
| ���������� | �ݹ��ӽ��׷ֽ׶�ģ�� |
| ����˵���� | struct TransEnv *p_te ���׻����ṹ<br />struct TransSchedule_BT_PC_BP_AP_AT *p_ts �ֽ׶�ģ������<br />TransFunc  *TF_HeaderMapping  ���translist�ṹ����(ע: IB2��IB1���TF_BT_InsertTransListHeaderMapping���ɣ�IB1�Զ���)<br />TransFunc  *TF_InsertTransList  �Ǽ�ҵ����ˮ����<br />TransFunc  *TF_UpdateTransList  ����ҵ����ˮ����<br /> |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.1.3. IBTSExecuteSchedule_BT_PC_RI_BP_AP_AT

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTSExecuteSchedule_BT_PC_BP_RI_AP_AT( char *req_msg_name , int sizeof_req_msg , void *p_req_st , char *rsp_msg_name , int sizeof_rsp_msg , void *p_rsp_st , struct IbasAddonFiles *addon_files , char *trans_code , char *response_code , int response_code_bufsize , char *response_desc , int response_desc_bufsize , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList , struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts ); |
| ���������� | ���ݿ����񣨽���ǰ��������������������׺�����<br />���ݿ����񣨹�����飩����������������׺�����<br />���ݿ�����ҵ���顢�����������ס�ҵ��������������������������׺�����<br />���ݿ����񣨽��׺������������������� |
| ����˵���� | char *req_msg_name ����ṹ������<br />int sizeof_req_msg ����ṹ���С<br />void *p_req_st ����ṹ��<br />char *rsp_msg_name ��Ӧ�ṹ������<br />int sizeof_rsp_msg ��Ӧ�ṹ���С<br />void *p_rsp_st ��Ӧ�ṹ��<br />struct IbasAddonFiles *addon_files �������Ӧ�����ļ�������<br />char *trans_code ҵ������<br />char *response_code ��Ӧ�뻺����<br />int response_code_bufsize ��Ӧ�뻺������С<br />char *response_desc ��Ӧ����������<br />int response_desc_bufsize ��Ӧ������������С<br />TransFunc  *TF_HeaderMapping  ���translist�ṹ����(ע: IB2��IB1���TF_BT_InsertTransListHeaderMapping���ɣ�IB1�Զ���)<br />TransFunc  *TF_InsertTransList  �Ǽ�ҵ����ˮ����<br />TransFunc  *TF_UpdateTransList  ����ҵ����ˮ����<br />struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts �ֽ׶�ģ������ |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.1.4. IBTSRecursiveSchedule_BT_PC_BP_RI_AP_AT

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTSRecursiveSchedule_BT_PC_BP_RI_AP_AT( struct TransEnv *p_te  , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList , struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts ); |
| ���������� | �ݹ��ӽ��׷ֽ׶�ģ�� |
| ����˵���� | struct TransEnv *p_te ���׻����ṹ<br />struct TransSchedule_BT_PC_BP_RI_AP_AT *p_ts �ֽ׶�ģ������<br />TransFunc  *TF_HeaderMapping  ���translist�ṹ����(ע: IB2��IB1���TF_BT_InsertTransListHeaderMapping���ɣ�IB1�Զ���)<br />TransFunc  *TF_InsertTransList  �Ǽ�ҵ����ˮ����<br />TransFunc  *TF_UpdateTransList  ����ҵ����ˮ���� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.1.5. IBTSExecuteSchedule_BT_PC_BP_AT__AP

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTSExecuteSchedule_BT_PC_BP_AT_AP( char *req_msg_name , int sizeof_req_msg , void *p_req_st , char *rsp_msg_name , int sizeof_rsp_msg , void *p_rsp_st , struct IbasAddonFiles *addon_files , char *trans_code , char *response_code , int response_code_bufsize , char *response_desc , int response_desc_bufsize , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList ,  struct TransSchedule_BT_PC_BP_AT_AP *p_ts ); |
| ���������� | ���ݿ����񣨽���ǰ��������������������׺�����<br />���ݿ����񣨹�����飩����������������׺�����<br />���ݿ����񣨽��׺���������������������<br />���ݿ�����ҵ���顢ҵ�������������������������� |
| ����˵���� | char *req_msg_name ����ṹ������<br />int sizeof_req_msg ����ṹ���С<br />void *p_req_st ����ṹ��<br />char *rsp_msg_name ��Ӧ�ṹ������<br />int sizeof_rsp_msg ��Ӧ�ṹ���С<br />void *p_rsp_st ��Ӧ�ṹ��<br />struct IbasAddonFiles *addon_files �������Ӧ�����ļ�������<br />char *trans_code ҵ������<br />char *response_code ��Ӧ�뻺����<br />int response_code_bufsize ��Ӧ�뻺������С<br />char *response_desc ��Ӧ����������<br />int response_desc_bufsize ��Ӧ������������С<br />TransFunc  *TF_HeaderMapping  ���translist�ṹ����(ע: IB2��IB1���TF_BT_InsertTransListHeaderMapping���ɣ�IB1�Զ���)<br />TransFunc  *TF_InsertTransList  �Ǽ�ҵ����ˮ����<br />TransFunc  *TF_UpdateTransList  ����ҵ����ˮ����<br />struct TransSchedule_BT_PC_BP_AT_AP *p_ts �ֽ׶�ģ������ |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.1.6. IBTSRecursiveSchedule_BT_PC_BP_AP_AT

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTSRecursiveSchedule_BT_PC_BP_AT_AP( struct TransEnv *p_te , TransFunc  *TF_HeaderMapping , TransFunc  *TF_InsertTransList , TransFunc  *TF_UpdateTransList ,  struct TransSchedule_BT_PC_BP_AT_AP *p_ts ); |
| ���������� | �ݹ��ӽ��׷ֽ׶�ģ�� |
| ����˵���� | struct TransEnv *p_te ���׻����ṹ<br />struct TransSchedule_BT_PC_BP_AT_AP *p_ts �ֽ׶�ģ������<br />TransFunc  *TF_HeaderMapping  ���translist�ṹ����(ע: IB2��IB1���TF_BT_InsertTransListHeaderMapping���ɣ�IB1�Զ���)<br />TransFunc  *TF_InsertTransList  �Ǽ�ҵ����ˮ����<br />TransFunc  *TF_UpdateTransList  ����ҵ����ˮ���� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

### 1.6.2. �õ�������Ϣ��

#### 1.6.2.1. IBTMGetFuncParaPtr

| | |
| ---:| --- |
| ����ԭ�ͣ� | char *IBTMGetFuncParaPtr( struct TransEnv *p_te ); |
| ���������� | �õ������������еĺ������� |
| ����˵���� | struct TransEnv *p_te ���׻��� |
| ����ֵ�� | ���غ����������еĺ������� |
| | |

### 1.6.3. ������Ӧ��Ϣ��

#### 1.6.3.1. IBTMFormatResponseCode

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTMFormatResponseCode( struct TransEnv *p_te , int response_code ); |
| ���������� | ������Ӧ�뵽���׻����е���Ӧ���ֶΣ����÷ֽ׶�ִ������ָ������ |
| ����˵���� | struct TransEnv *p_te ���׻���<br />int response_code ��Ӧ�� |
| ����ֵ�� | �����������response_code��ֵ |
| | |

#### 1.6.3.2. IBTMFormatResponseCode

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTMFormatResponseCode( struct TransEnv *p_te , int response_code ); |
| ���������� | ������Ӧ�뵽���׻����е���Ӧ���ֶΣ����÷ֽ׶�ִ������ָ������ |
| ����˵���� | struct TransEnv *p_te ���׻���<br />int response_code ��Ӧ�� |
| ����ֵ�� | �����������response_code��ֵ |
| | |

#### 1.6.3.3. IBTMFormatResponseDesc

| | |
| ---:| --- |
| ����ԭ�ͣ� | void IBTMFormatResponseDesc( struct TransEnv *p_te , char *response_desc_format , ... ); |
| ���������� | ������Ӧ���������׻����е���Ӧ���ֶΣ����÷ֽ׶�ִ������ָ������ |
| ����˵���� | struct TransEnv *p_te ���׻���<br />char *response_desc_format , ... ��Ӧ�����ɱ�����б� |
| ����ֵ�� | ���ޣ� |
| | |

#### 1.6.3.4. IBTMFormatResponseInfo

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTMFormatResponseInfo( struct TransEnv *p_te , int response_code , char *response_desc_format , ... ); |
| ���������� | ������Ӧ�����Ӧ���������׻����е���Ӧ���ֶΣ����÷ֽ׶�ִ������ָ������ |
| ����˵���� | struct TransEnv *p_te ���׻���<br />int response_code ��Ӧ��<br />char *response_desc_format , ... ��Ӧ�����ɱ�����б� |
| ����ֵ�� | �����������response_code��ֵ |
| | |

### 1.6.4. �ṹ������

#### 1.6.4.1. IBTMAppendStructBlock

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTMAppendStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem ); |
| ���������� | �ҽ�һ���ṹ�嵽�ṹ������ |
| ����˵���� | struct TransEnv *p_te ���׻���<br />char *name �ṹ�����֣��64�ַ���<br />long struct_size �ṹ���С<br />void **ppmem ���(*ppmem)==NULL���Զ������ڴ����Դ�Ÿýṹ�� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.4.2. IBTMGetStructBlock

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTMGetStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem ); |
| ���������� | �ӽṹ�����л�ȡһ���ṹ�� |
| ����˵���� | struct TransEnv *p_te ���׻���<br />char *name �ṹ�����֣��64�ַ���<br />long struct_size �ṹ���С<br />void **ppmem ���سɹ�ʱ��(*ppmem)ָ��ýṹ�� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.4.3. IBTMAppendGetStructBlock

| | |
| ---:| --- |
| ����ԭ�ͣ� | int IBTMAppendGetStructBlock( struct TransEnv *tpe , char *name , long struct_size , void **ppmem ); |
| ���������� | �ӽṹ�����л�ȡһ���ṹ�壬���û�о͹ҽ�һ�� |
| ����˵���� | struct TransEnv *p_te ���׻���<br />char *name �ṹ�����֣��64�ַ���<br />long struct_size �ṹ���С<br />void **ppmem���(*ppmem)==NULL���Զ������ڴ����Դ�Ÿýṹ�� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

### 1.6.5. ��̬�ṹ����

#### 1.6.5.1. DS_NEW

| | |
| ---:| --- |
| ��ʹ��ʾ���� | DS      *ds = DS_NEW( "struct_name" ) ; |
| ���������� | ����һ����̬�ṹ�塣��̬�ṹ��������Ӧ��ģ��֮�䰲ȫ�Ľ������� |
| ����˵���� | ��̬�ṹ������ |
| ����ֵ�� | �ɹ��򷵻ض�̬�ṹ�壬ʧ���򷵻�NULL |
| | |

#### 1.6.5.2. DS_ADD

| | |
| ---:| --- |
| ��ʹ��ʾ���� | DS_TRY(ds)<br />{       <br />        DS_ADD( ds , char , char_field , 0x30 ); <br />        DS_ADD( ds , int , int_field , 123 );<br />        DS_ADD( ds , long , long_field , 45678 );<br />        DS_ADD( ds , float , float_field , 123.0 );<br />        DS_ADD( ds , double , double_field , 456.789 );<br />        DS_ADD( ds , char* , string_field , "hello" );<br />}       <br />DS_CATCH(ds)<br />{       <br />        ERRORLOGG( "DS_ADD failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) )<br />        DS_DELETE ( ds );<br />        return -1;<br />}       |
| ���������� | ����̬�ṹ������ӱ����ֶβ�ֱ�Ӹ�ֵ |
| ����˵���� | ��̬�ṹ�塢�������͡�������������ֵ |
| ����ֵ�� | ȫ��ADD�ɹ�������DS_CATCH���棬��һ��ADDʧ��������DS_CATCH���� |
| | |

#### 1.6.5.3. DS_SET

| | |
| ---:| --- |
| ��ʹ��ʾ���� | DS_TRY(ds)<br />{       <br />        DS_SET( ds , char , char_field , 0x30 ); <br />        DS_SET( ds , int , int_field , 123 );<br />        DS_SET( ds , long , long_field , 45678 );<br />        DS_SET( ds , float , float_field , 123.0 );<br />        DS_SET( ds , double , double_field , 456.789 );<br />        DS_SET( ds , char* , string_field , "hello" );<br />}       <br />DS_CATCH(ds)<br />{       <br />        ERRORLOGG( "DS_SET failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) )<br />        DS_DELETE( ds );<br />        return -1;<br />} |
| ���������� | ����ֵ����̬�ṹ���еı����ֶ��� |
| ����˵���� | ��̬�ṹ�塢�������͡�������������ֵ |
| ����ֵ�� | ȫ��SET�ɹ�������DS_CATCH���棬��һ��SETʧ��������DS_CATCH���� |
| | |

#### 1.6.5.4. DS_GET

| | |
| ---:| --- |
| ��ʹ��ʾ���� | DS_TRY(ds)<br />{       <br />        DS_GET( ds , char , char_field , ch ); <br />        DS_GET( ds , int , int_field , i );<br />        DS_GET( ds , long , long_field , l );<br />        DS_GET( ds , float , float_field , f );<br />        DS_GET( ds , double , double_field , d );<br />        DS_GET( ds , char* , string_field , buf , sizeof(buf) );<br />}       <br />DS_CATCH(ds)<br />{       <br />        ERRORLOGG( "DS_GET failed , LINE[%d] FIELD_NAME[%s] ERROR[%d]" , DSGetLastSourceLine(ds) , DSGetFieldName(ds) , DSGetLastError(ds) )<br />        DS_DELETE( ds );<br />        return -1;<br />} |
| ���������� | �Ӷ�̬�ṹ���еı����ֶ�����ȡֵ���� |
| ����˵���� | ��̬�ṹ�塢�������͡�������������ֵ<br />������Ϊ�ַ���ʱ�������Ҫ�ټ�һ���������������������С |
| ����ֵ�� | ȫ��GET�ɹ�������DS_CATCH���棬��һ��GETʧ��������DS_CATCH����<br /> |
| | |

### 1.6.6. ���ݿ������

#### 1.6.6.1. OpenDatabaseSessions

| | |
| ---:| --- |
| ����ԭ�ͣ� | int OpenDatabaseSessions(); |
| ���������� | �����ݿ� |
| ����˵���� | �� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.6.2. CloseDatabaseSessions

| | |
| ---:| --- |
| ����ԭ�ͣ� | int CloseDatabaseSessions(); |
| ���������� | �ر����ݿ� |
| ����˵���� | �� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.6.3. BeginDatabaseTransaction

| | |
| ---:| --- |
| ����ԭ�ͣ� | int BeginDatabaseTransaction(); |
| ���������� | ��ʼ���ݿ����� |
| ����˵���� | �� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.6.4. CommitDatabaseTransaction

| | |
| ---:| --- |
| ����ԭ�ͣ� | int CommitDatabaseTransaction(); |
| ���������� | �ύ���ݿ����� |
| ����˵���� | �� |
| ����ֵ�� | �ɹ��򷵻�0��ʧ���򷵻ط�0 |
| | |

#### 1.6.6.5. RollbackDatabaseTransaction

| | |
| ---:| --- |
| ����ԭ�ͣ� | int RollbackDatabaseTransaction(); |
| ���������� | �ύ�ع����ݿ����� |
| ����˵���� | �� |

# 2. ����ʾ��

## 2.1. ����API

### 2.1.1. ������ʱ�ļ�

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

## 2.2. ͨѶ�ͻ���API

### 2.2.1. ����ͨѶ�����в㣩

test/test_ibpclient/ibp_test_echo/ibp_test_echo.c

```
#include "ibac_api.h"

int ibp_test_echo_IBACRequester( char *node , char *app , char *msg )
{
	struct IbacEnv		*p_env = NULL ;
	
	char			*p_msg = NULL ;
	int			msg_len ;
	
	int			nret = 0 ;
	
	/* ����ͨѶ�ͻ��˻��� */
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
	
	/* ����ͨѶ����ˣ��������󣬽�����Ӧ���Ͽ�ͨѶ����� */
	/* ��ڵ�node������app��p_msgָ�������ģ�������ɺ���Ӧ���Ĵ����ͨѶ�ͻ��˻����У�p_msgָ���� */
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
	
	/* ����ͨѶ�ͻ��˻��� */
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
# ���ļ���makeobj.sh�Զ�����
############################################################
# ��Ŀ�� : 
# ģ���� : 
# ��  ע : 
############################################################

###### Դ�ļ�������
#@ c_FILE
c_FILE		=	\
			ibp_test_echo.c \

###### Ŀ���ļ�����װĿ¼������
include makeinstall
BIN		=	ibp_test_echo
BININST		=	$(_BININST)

###### ����ѡ��
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \

###### ����ѡ��
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libac_api

###### ����궨����
CLEAN_ADDITION	=

###### ����mktplģ���
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_BININST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_BININST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### Ŀ���ļ�������ϵ
ibp_test_echo		:	$(c_FILE_o)
	$(CC) -o $@ $(c_FILE_o) $(LFLAGS)
```

### 2.2.2. ����ͨѶ�����в㣩�������ļ���

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
	
	/* ����ͨѶ�ͻ��˻��� */
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
	
	/* ����������ʱ�ļ�1 */
	/* �Ǹ����ļ� */
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
	
	/* ����������ʱ�ļ�2 */
	/* �ļ���СΪ1���ֽ� */
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
	
	/* ����������ʱ�ļ�3 */
	/* �ļ���СΪ1024���ֽ� */
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
	
	/* ����������ʱ�ļ�4 */
	/* �ļ���СΪ1024*1024���ֽ� */
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
	
	/* ��ʼ����Ӧ��ʱ�ļ������������������Ӧ��ʱ�ļ������ͻ�������� */
	memset( tmp_rsp_filename1 , 0x00 , sizeof(tmp_rsp_filename1) );
	memset( tmp_rsp_filename2 , 0x00 , sizeof(tmp_rsp_filename2) );
	memset( tmp_rsp_filename3 , 0x00 , sizeof(tmp_rsp_filename3) );
	memset( tmp_rsp_filename4 , 0x00 , sizeof(tmp_rsp_filename4) );
	
	/* ����ͨѶ����ˣ��������󣬽�����Ӧ���Ͽ�ͨѶ����� */
	/* ��ڵ�node������app��p_msgָ�������ģ�������ɺ���Ӧ���Ĵ����ͨѶ�ͻ��˻����У�p_msgָ���� */
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
	
	/* ����ͨѶ�ͻ��˻��� */
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

### 2.2.3. ����ͨѶ���󣨵Ͳ㣩

test/test_ibpclient/ibp_test_echo/ibp_test_echo.c

```
#include "ibac_api.h"

int ibp_test_echo_IBACSendRequestAndReceiveResponse( char *node , char *app , char *msg )
{
	struct IbacEnv		*p_env = NULL ;
	
	char			*p_msg = NULL ;
	int			msg_len ;
	
	int			nret = 0 ;
	
	/* ����ͨѶ�ͻ��˻��� */
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
	
	/* ����ͨѶ����� */
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
	
	/* �������󣬽�����Ӧ */
	/* ��ڵ�node������app��p_msgָ�������ģ�������ɺ���Ӧ���Ĵ����ͨѶ�ͻ��˻����У�p_msgָ���� */
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
	
	/* �Ͽ�ͨѶ����� */
	IBACDisconnect( p_env );
	printf( "IBACDisconnect ok\n" );
	
	/* ����ͨѶ�ͻ��˻��� */
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

## 2.3. ͨѶ�����API

### 2.3.1. �������

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
	
	/* ���������� */
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
# ���ļ���makeobj.sh�Զ�����
############################################################
# ��Ŀ�� : 
# ģ���� : 
# ��  ע : 
############################################################

###### Դ�ļ�������
#@ c_FILE
c_FILE		=	\
			ibp_test_echo.c \

###### Ŀ���ļ�����װĿ¼������
include makeinstall
LIB		=	ibp_test_echo.so
LIBINST		=	$(_LIBINST)

###### ����ѡ��
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \

###### ����ѡ��
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libas_api \

###### ����궨����
CLEAN_ADDITION	=

###### ����mktplģ���
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_LIBINST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_LIBINST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### Ŀ���ļ�������ϵ
ibp_test_echo.so		:	$(c_FILE_o)
	$(CC) -o $@ $(c_FILE_o) $(SOFLAGS) $(LFLAGS)
	ibpcheckso $@ -r
```

### 2.3.2. ������񣨸����ļ���

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
	
	/* ���������� */
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
	
	/* ���ļ�IDȡ�����ļ��� */
	p_filename = IBASGetRequestFileById( addon_files , "BFILE" ) ;
	if( p_filename )
	{
		INFOLOGG( "IBASGetRequestFile ok , [%s]" , p_filename );
	}
	
	/* �������������ļ� */
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

## 2.4. ����ת��API

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
# ���ļ���makeobj.sh�Զ�����
############################################################
# ��Ŀ�� : 
# ģ���� : 
# ��  ע : 
############################################################

###### Դ�ļ�������
#@ c_FILE
c_FILE		=	\
			ibp_test_ts1.c \

###### Ŀ���ļ�����װĿ¼������
include makeinstall
BIN		=	ibp_test_ts1
BININST		=	$(_BININST)

###### ����ѡ��
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \
			-I../../test_ibpserver/ibp_test_ts1 \

###### ����ѡ��
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libmsgv_api \

###### ����궨����
CLEAN_ADDITION	=

###### ����mktplģ���
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_BININST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_BININST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### Ŀ���ļ�������ϵ
ibp_test_ts1		:	$(c_FILE_o) IDL_test_ibpts1_request.dsc.o IDL_test_ibpts1_response.dsc.o
	$(CC) -o $@ $(c_FILE_o) IDL_test_ibpts1_request.dsc.o IDL_test_ibpts1_response.dsc.o $(LFLAGS)
```

## 2.5. ��̬�ṹ����

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

## 2.6. �ֽ׶ι����API

test/test_ibpserver/ibp_test_ts1/IDL_test_ibpts1_request.dsc

```
STRUCT	test_ibpts1_request			# ����ѯ ����
{
	INCLUDE IDL_test_request_header.dsc
	
	STRUCT	test_ibpts1
	{
		STRING	40	account_no	# �˺�
		STRING	16	password	# ����
	}
}
```

test/test_ibpserver/ibp_test_ts1/IDL_test_ibpts1_response.dsc

```
STRUCT	test_ibpts1_response		# ����ѯ ��Ӧ
{
	INCLUDE IDL_test_response_header.dsc
	
	STRUCT	test_ibpts1
	{
		STRING	40	account_no		# �˺�
		NUMERIC	16,2	balance			# ���
	}
}
	test/test_ibpserver/ibp_test_ts1/IDL_test_request_header.dsc
	STRUCT	test_request_header		# ���󹫹�ͷ
	{
		STRING 10	sender_date	# ��������
		STRING 8	sender_time	# ����ʱ��
		STRING 20	sender_trans_no	# ������ˮ��
		STRING 6	channel_code	# ��������
		STRING 10	branch_no	# ��������
		STRING 12	oper_no		# ���׹�Ա
		STRING 32	login_session	# ǩ���Ự
		STRING 20	trans_code	# ������
	}
	test/test_ibpserver/ibp_test_ts1/IDL_test_response_header.dsc
	STRUCT	test_response_header			# ��Ӧ����ͷ
	{
		STRING 10	sender_date		# ��������
		STRING 8	sender_time		# ����ʱ��
		STRING 20	sender_trans_no		# ������ˮ��
		STRING 10	receiver_date		# ���շ�����
		STRING 8	receiver_time		# ���շ�ʱ��
		STRING 20	receiver_trans_no	# ���շ���ˮ��
		STRING 10	response_code		# ���׽��
		STRING 128	response_desc		# ���׽������
		STRING 128	response_message	# ������Ϣ
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
		FUNC( "����ǰ����1" , TF_BT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_PC_CH_TESTTPS1[] =
	{
		FUNC( "�����������" , TF_PC_CH_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_PC_OP_TESTTPS1[] =
	{
		FUNC( "����Ա�������" , TF_PC_OP_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_PC_OG_TESTTPS1[] =
	{
		FUNC( "�����������" , TF_PC_OG_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_MD_TESTTPS1[] =
	{
		FUNC( "���ʲ�ҵ����" , TF_BC_MD_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_AT_TESTTPS1[] =
	{
		FUNC( "�˻���ҵ����" , TF_BC_AT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_CT_TESTTPS1[] =
	{
		FUNC( "�ͻ���ҵ����" , TF_BC_CT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BC_BS_TESTTPS1[] =
	{
		FUNC( "ҵ����麯��1" , TF_BC_BS_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_MD_TESTTPS1[] =
	{
		FUNC( "���ʲ�ҵ����" , TF_BP_MD_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_AT_TESTTPS1[] =
	{
		FUNC( "�˻���ҵ����" , TF_BP_AT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_CT_TESTTPS1[] =
	{
		FUNC( "�ͻ���ҵ����" , TF_BP_CT_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_BP_BS_TESTTPS1[] =
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

struct TransFuncArray	TFA_AP_TESTTPS1[] =
	{
		FUNC( "������" , TF_AP_TESTTPS1 )
		RETURN
	} ;

struct TransFuncArray	TFA_AT_TESTTPS1[] =
	{
		FUNC( "���׺���" , TF_AT_TESTTPS1 )
		RETURN
	} ;

struct TransSchedule_BT_PC_BP_AP_AT	TS_TESTTPS1 =
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
	return IBTMFormatResponseInfo( p_te , -1 , "�޴˿���[%s]" , "603367123412341234" );
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
		FUNC( "ҵ���ҵ����0" , TF_BP_BS_TESTTPS1_F0 )
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
		FUNC( "ҵ���ҵ����2" , TF_BP_BS_TESTTPS1_F2 )
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
		FUNC( "ҵ���ҵ����6" , TF_BP_BS_TESTTPS1_F6 )
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
# ���ļ���makeobj.sh�Զ�����
############################################################
# ��Ŀ�� : 
# ģ���� : 
# ��  ע : 
############################################################

###### Դ�ļ�������
#@ c_FILE
c_FILE		=	\
			IDL_test_ibpts1_request.dsc.c \
			IDL_test_ibpts1_response.dsc.c \
			somain.c \
			transmain.c \

###### Ŀ���ļ�����װĿ¼������
include makeinstall
LIB		=	ibp_test_ts1.so
LIBINST		=	$(_LIBINST)

###### ����ѡ��
CFLAGS		=	$(_CFLAGS) \
			-std=gnu99 \
			-I$(HOME)/include/ibp \

###### ����ѡ��
LFLAGS		=	$(_LFLAGS) \
			-rdynamic \
			-L$(HOME)/lib \
			-libmsgv_api \
			-libtm_api \
			-libts_api \

###### ����궨����
CLEAN_ADDITION	=

###### ����mktplģ���
#@ make_all
#@ make_clean
#@ make_install
#@ make_install_LIBINST
#@ make_install_DFTHDERINST
#@ make_uninstall
#@ make_uninstall_LIBINST
#@ make_uninstall_DFTHDERINST
include $(MKTPLDIR)/makeobj_$(MKTPLOS).inc

###### Ŀ���ļ�������ϵ
ibp_test_ts1.so		:	$(c_FILE_o)
	$(CC) -o $@ $(c_FILE_o) $(SOFLAGS) $(LFLAGS)
	ibpcheckso $@ -r
```
