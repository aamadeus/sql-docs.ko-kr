---
title: "분산 가용성 그룹(Always On 가용성 그룹) 구성 | Microsoft Docs"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 97c42036e08fa8d1d8e7152b7fb89908472efe6b
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---

# <a name="configure-distributed-availability-group"></a>분산 가용성 그룹 구성  

분산 가용성 그룹을 만들려면 각 WSFC(Windows Server 장애 조치 클러스터)에서 가용성 그룹 및 수신기를 만들어야 합니다. 그런 다음 이러한 분산형 가용성 그룹으로 결합해야 합니다. 다음 단계는 TRANSACT-SQL에서의 기본 예제를 제공합니다. 이 예제에서는 가용성 그룹 및 수신기를 만드는 데 관련된 자세한 내용을 다루지 않는 대신 주요 요구 사항을 집중적으로 다루고 있습니다. 

분산 가용성 그룹에 대한 기술적 개요는 [분산 가용성 그룹](distributed-availability-groups.md)을 참조하세요.   

## <a name="prerequisites"></a>필수 구성 요소

### <a name="set-the-endpoint-listeners-to-listen-to-all-ip-addresses"></a>모든 IP 주소를 수신 대기하도록 끝점 수신기를 설정합니다.

끝점에서 분배 가용성 그룹의 서로 다른 가용성 그룹 간에 통신할 수 있는지 확인합니다. 하나의 가용성 그룹이 끝점의 특정 네트워크로 설정되면 분산 AG가 제대로 작동하지 않습니다. 분산 가용성 그룹에서 복제본을 호스팅할 각 서버에서 수신기를 `LISTENER_IP = ALL`로 구성합니다. 

#### <a name="create-a-listener-to-listen-to-all-ip-addresses"></a>모든 IP 주소를 수신 대기하도록 수신기 만들기

예를 들어 다음 스크립트에서는 모든 IP 주소에서 수신 대기하는 5022 TCP 포트에 수신기 끝점을 만듭니다.  

```tsql
CREATE ENDPOINT [aodns-hadr] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
FOR DATA_MIRRORING (
   ROLE = ALL, 
   AUTHENTICATION = WINDOWS NEGOTIATE,
   ENCRYPTION = REQUIRED ALGORITHM AES
)
GO
```

#### <a name="alter-a-listener-to-listen-to-all-ip-addresses"></a>모든 IP 주소를 수신 대기하도록 수신기 변경

예를 들어 다음 스크립트에서는 모든 IP 주소에서 수신 대기하도록 수신기 끝점을 변경합니다.  

```tsql
ALTER ENDPOINT [aodns-hadr] 
    AS TCP (LISTENER_IP = ALL)
GO
```

## <a name="create-first-availability-group"></a>첫 번째 가용성 그룹 만들기

### <a name="create-the-primary-availability-group-on-the-first-cluster"></a>첫 번째 클러스터에 주 가용성 그룹 만들기  
첫 WSFC에 주 가용성 그룹을 만듭니다.   이 예제에서 `ag1` 데이터베이스에 대한 가용성 그룹 이름은 `db1`입니다.      
  
```tsql  
CREATE AVAILABILITY GROUP [ag1]   
FOR DATABASE db1   
REPLICA ON N'server1' WITH (ENDPOINT_URL = N'TCP://server1.contoso.com:5022',  
    FAILOVER_MODE = AUTOMATIC,  
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server2' WITH (ENDPOINT_URL = N'TCP://server2.contoso.com:5022',   
    FAILOVER_MODE = AUTOMATIC,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
  
```  
  
이 예제에서는 직접 시드를 사용하고 여기에서 복제본 및 분산형 가용성 그룹 모두에서 **SEEDING_MODE** 는 **AUTOMATIC** 으로 설정됩니다. 즉, 설정되면 수동으로 백업하고 주 데이터베이스를 복구할 필요 없이 보조 복제본과 보조 가용성 그룹이 자동으로 채워집니다.  
  
### <a name="join-the-secondary-replicas-to-the-primary-availability-group"></a>보조 복제본을 주 가용성 그룹에 조인  
모든 보조 복제본은 **JOIN** 옵션으로 **ALTER AVAILABILITY GROUP** 이(가) 있는 가용성 그룹에 조인되어야 합니다. 이 예제에서는 직접 시딩이 사용되었지 때문에  **GRANT CREATE ANY DATABASE** 옵션으로 **ALTER AVAILABILITY GROUP** 도 호출해야 합니다. 이를 통해 가용성 그룹이 데이터베이스를 만들고 주 복제본에서 자동으로 시딩을 시작할 수 있습니다.  
  
이 예제에서는 보조 복제본 `server2`에서 다음 명령이 실행되어 가용성 그룹 `ag1` 에 조인됩니다. 그런 다음 가용성 그룹이 보조 가용성 그룹에 데이터베이스를 만들 수 있습니다.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  
  
### <a name="create-a-listener-for-the-primary-availability-group"></a>주 가용성 그룹에 대한 수신기 만들기  

그런 다음 첫 번째 WSFC에 주 가용성 그룹에 대한 수신기를 추가합니다. 이 예제에서 수신기 이름은 `ag1-listener`입니다. 수신기를 만드는 방법은 [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)을 참조하세요.  
  
```  
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  

## <a name="create-second-availability-group"></a>두 번째 가용성 그룹 만들기  
 그런 다음 두 번째 WSFC에서 두 번째 가용성 그룹인 `ag2`을(를) 만듭니다. 이 경우 주 가용성 그룹에서 자동으로 시딩되므로 데이터베이스를 지정하지 않습니다.  
  
```tsql  
CREATE AVAILABILITY GROUP [ag2]   
FOR   
REPLICA ON N'server3' WITH (ENDPOINT_URL = N'TCP://server3.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server4' WITH (ENDPOINT_URL = N'TCP://server4.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
```  
  
> [!NOTE]  
>  보조 가용성 그룹은 동일한 데이터베이스 미러링 끝점(이 예제에서는 5022 포트)을 사용해야 합니다. 그렇지 않으면 로컬 장애 조치(failover) 후 복제가 중지됩니다.  
  
### <a name="join-the-secondary-replicas-to-the-secondary-availability-group"></a>보조 복제본을 보조 가용성 그룹에 조인  
 이 예제에서는 보조 복제본 `server4`에서 다음 명령이 실행되어 가용성 그룹 `ag2` 에 조인됩니다. 그런 다음 가용성 그룹은 보조 가용성 그룹에 데이터베이스를 만들어 직접 시딩을 지원할 수 있습니다.  
  
```tsql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### <a name="create-a-listener-for--the-secondary-availability-group"></a>보조 가용성 그룹에 대한 수신기 만들기  
 그런 다음 두 번째 WSFC에 보조 가용성 그룹에 대한 수신기를 추가합니다. 이 예제에서 수신기 이름은 `ag2-listener`입니다. 수신기를 만드는 방법은 [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)을 참조하세요.  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
## <a name="create-distributed-availability-group-on-first-cluster"></a>첫 번째 클러스터에 분산 가용성 그룹 만들기  
 첫 번째 WSFC에서 분산형 가용성 그룹(이 예제에서의 이름은 `distributedag` )을 만듭니다. **DISTRIBUTED** 옵션으로 **CREATE AVAILABILITY GROUP** 명령을 사용합니다. **AVAILABILITY GROUP ON** 매개 변수는 멤버 가용성 그룹인 `ag1` 및 `ag2`를 지정합니다.  
  
```tsql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  **LISTENER_URL** 은 가용성 그룹의 데이터베이스 미러링 끝점과 함께 각 가용성 그룹에 대한 수신기를 지정합니다. 이 예제에서 수신기는 `5022` 포트(수신기를 만드는 데 사용된 `60173` 포트 아님)입니다.  
  
## <a name="join-distributed-availability-group-on-second-cluster"></a>두 번째 클러스터에 분산 가용성 그룹 조인  
 그런 다음 두 번째 WSFC에 분산형 가용성 그룹을 조인합니다.  
  
```tsql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

  
## <a name="failover-to-a-secondary-availability-group"></a>보조 가용성 그룹에 대한 장애 조치(failover)  
이 경우에는 수동 장애 조치(failover)만 지원됩니다. 다음 Transact-SQL 문은 `distributedag`라는 이름의 분산형 가용성 그룹에 장애 조치(failover)를 강제로 적용합니다.  


1. 보조 가용성 그룹에 대해 가용성 모드를 동기 커밋으로 설정합니다. 
    
      ```tsql  
      ALTER AVAILABILITY GROUP [distributedag] 
      MODIFY 
      AVAILABILITY GROUP ON
      'ag1' WITH  
         ( 
          LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',  
          AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = MANUAL, 
          SEEDING_MODE = MANUAL 
          ), 
      'ag2' WITH  
        ( 
        LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022', 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
        FAILOVER_MODE = MANUAL, 
        SEEDING_MODE = MANUAL 
        );  
       
      ```  
  
1. 분산 가용성 그룹의 상태가 `SYNCHRONIZED`으로 변경될 때까지 대기합니다. 기본 가용성 그룹의 주 복제본을 호스트하는 SQL Server에서 다음 쿼리를 실행합니다. 
    
      ```tsql  
      SELECT ag.name
             , drs.database_id
             , drs.group_id
             , drs.replica_id
             , drs.synchronization_state_desc
             , drs.end_of_log_lsn 
        FROM sys.dm_hadr_database_replica_states drs,
        sys.availability_groups ag
          WHERE drs.group_id = ag.group_id;      
      ```  

    가용성 그룹 **synchronization_state_desc** 가 `SYNCHRONIZED`가 되면 계속합니다. **synchronization_state_desc** 가 `SYNCHRONIZED`가 아니면 변경될 때까지 5초 마다 명령을 실행합니다. **synchronization_state_desc** = `SYNCHRONIZED`가 될 때까지 진행하지 마세요. 

1. 기본 가용성 그룹의 주 복제본을 호스트하는 SQL Server에서 분산 가용성 그룹 역할을 `SECONDARY`로 설정합니다. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
      ```  

   >[참고] 이 시점에서 분산 가용성 그룹은 사용할 수 없습니다.

1. 장애 조치(failover) 준비를 테스트합니다. 다음 쿼리를 실행합니다.

      ```tsql
      SELECT ag.name, 
             drs.database_id, 
             drs.group_id, 
             drs.replica_id, 
             drs.synchronization_state_desc, 
             drs.end_of_log_lsn 
      FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
      WHERE drs.group_id = ag.group_id; 
      ```  
    **synchronization_state_desc** 가 `SYNCHRONIZED` 이고, **end_of_log_lsn** 이 두 가용성 그룹에 대해 동일할 경우 가용성 그룹은 장애 조치(failover)할 준비가 됩니다. 

1. 주 가용성 그룹에서 보조 가용성 그룹으로 장애 조치(failover)합니다. 보조 가용성 그룹의 주 복제본을 호스트하는 SQL Server에서 다음 명령을 실행합니다. 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
      ```  

   >[참고] 이 단계가 완료되면 분산 가용성 그룹을 사용할 수 있게 됩니다.
      
위의 단계를 완료한 후 분산 가용성 그룹은 데이터 손실없이 장애 조치(failover)됩니다. 가용성 그룹이 지연이 발생하는 지리적 거리 위치에 있는 경우에는 가용성 모드를 다시 ASYNCHRONOUS_COMMIT으로 변경하는 것이 좋습니다. 
  
## <a name="remove-a-distributed-availability-group"></a>분산형 가용성 그룹 제거  
 다음 Transact-SQL 문은 `distributedag`라는 이름의 분산형 가용성 그룹을 삭제합니다.  
  
```tsql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## <a name="create-distributed-availability-group-on-failover-cluster-instances"></a>장애 조치 클러스터 인스턴스에 분산 가용성 그룹 만들기

FCI(장애 조치 클러스터 인스턴스)에서 가용성 그룹을 사용하여 분산 가용성 그룹을 만들 수 있습니다. 이 경우 가용성 그룹 수신기가 필요 없습니다. FCI 인스턴스의 주 복제본에 VNN(가상 네트워크 이름)을 사용합니다. 다음 예제에서는 SQLFCIDAG 라는 분산 가용성 그룹을 보여 줍니다. 가용성 그룹으로 SQLFCIAG가 하나 있으며, SQLFCIAG에는 FCI 복제본이 2개 있습니다. 주 FCI 복제본의 VNN은 SQLFCIAG-1이며 보조 FCI 복제본의 VNN은 SQLFCIAG-2입니다. 재해 복구를 위해 분산 가용성 그룹에는 재해 복구를 위해 SQLAG-DR도 포함됩니다.

![배포되는 Always On 가용성 그룹](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 다음 DDL에서 이 분산 가용성 그룹을 만듭니다. 

```tsql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

>[참고] 수신기 URL은 주 FCI 인스턴스의 VNN입니다.

## <a name="manually-fail-over-fci-in-distributed-availability-group"></a>분산 가용성 그룹에서 FCI 수동 장애 조치

FCI 가용성 그룹을 수동으로 장애 조치하려면 수신기 URL의 변경 내용을 반영하도록 분산 가용성 그룹을 업데이트합니다. 예를 들어 SQLFCIAG의 기본 AG와 보조 AG에서 다음 DDL을 실행합니다.

```tsql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2.contoso.com:5022'
    )
```  
  
## <a name="next-steps"></a>다음 단계

 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  