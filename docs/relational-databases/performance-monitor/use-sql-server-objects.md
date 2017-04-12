---
title: "SQL Server 개체 사용 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "서버 성능 [SQL Server], 모니터링용 개체"
  - "데이터베이스 모니터링 [SQL Server], 모니터링용 개체"
  - "차트 [SQL Server]"
  - "시스템 모니터 [SQL Server], 카운터"
  - "카운터 [SQL Server], 나열"
  - "개체 [SQL Server], 성능 모니터링"
  - "개체 [SQL Server], Windows 시스템 모니터"
  - "성능 카운터 [SQL Server], 성능 카운터 정보"
  - "시스템 모니터 [SQL Server], 개체"
  - "성능 카운터 [SQL Server]"
  - "카운터 [SQL Server], 성능 카운터 정보"
  - "데이터베이스 튜닝 [SQL Server], 모니터링용 개체"
  - "데이터베이스 성능 [SQL Server], 모니터링용 개체"
  - "SQL Server, 개체"
  - "모니터링 성능 [SQL Server], 모니터링용 개체"
  - "Windows 시스템 모니터 [SQL Server], 개체"
  - "Windows 시스템 모니터 [SQL Server], 카운터"
  - "카운터 [SQL Server]"
  - "성능 카운터 [SQL Server], 나열"
ms.assetid: bcd731b1-3c4e-4086-b58a-af7a3af904ad
caps.latest.revision: 56
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# SQL Server 개체 사용
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 실행하는 컴퓨터의 작업을 모니터링하기 위해 시스템 모니터에서 사용할 수 있는 개체 및 카운터를 제공합니다. 개체는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 잠금이나 Windows 프로세스와 같은 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스를 말합니다. 각 개체에는 모니터링할 개체의 여러 요소를 결정하는 하나 이상의 카운터가 포함됩니다. 예를 들어 **SQL Server Locks** 개체에는 **Number of Deadlocks/sec** 및 **Lock Timeouts/sec**이라는 카운터가 포함됩니다.  
  
 지정된 유형의 리소스가 컴퓨터에 여러 개 존재할 경우 일부 개체는 여러 인스턴스를 갖습니다. 예를 들어 **Processor** 개체 유형은 시스템에 프로세서가 여러 개 있는 경우 인스턴스를 여러 개 갖게 됩니다. **Databases** 개체 유형은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 각 데이터베이스에 대해 인스턴스를 하나씩 갖습니다. 일부 개체 유형(예: **Memory Manager** 개체)은 인스턴스를 하나만 갖습니다. 개체 유형이 인스턴스를 여러 개 가지는 경우 카운터를 추가해 각 인스턴스의 통계를 추적할 수 있고, 대부분의 경우 모든 인스턴스를 한 번에 추적할 수 있습니다. 기본 인스턴스용 카운터는 **SQLServer:***\<개체 이름>* 형식으로 표시됩니다. 명명된 인스턴스용 카운터는 **MSSQL$***\<인스턴스 이름>***:***\<카운터 이름>* 또는 **SQLAgent$***\<인스턴스 이름>***:***\<카운터 이름>* 형식으로 표시됩니다.  
  
 카운터를 차트에 추가하거나 제거하고 차트 설정을 저장하면 시스템 모니터가 시작될 때 모니터링되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 및 카운터를 지정할 수 있습니다.  
  
 시스템 모니터를 어떤 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 카운터의 통계라도 표시하도록 구성할 수 있습니다. 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 카운터에 대해 임계값을 설정한 다음 카운터가 임계값을 초과할 때 경고를 생성하도록 설정할 수도 있습니다. 경고 설정에 대한 자세한 내용은 [SQL Server 데이터베이스 경고 만들기](../../relational-databases/performance-monitor/create-a-sql-server-database-alert.md)를 참조하세요.  
  
> [!TIP]  
>  [sys.dm_os_performance_counters&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) 동적 관리 뷰를 쿼리하여 성능 카운터 값을 반환할 수도 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 통계는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 설치한 경우에만 표시됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 중지하고 다시 시작하면 통계 표시도 중단되었다가 자동으로 재개됩니다. 또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 실행 중이 아닌 경우에도 시스템 모니터 스냅인에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 카운터가 나타납니다. 클러스터형 인스턴스에서 성능 카운터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행 중인 노드에서만 작동합니다.  
  
 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
-   [SQL Server 에이전트 성능 개체](#SQLServerAgentPOs)  
  
-   [Service Broker 성능 개체](#ServiceBrokerPOs)  
  
-   [SQL Server 성능 개체](#SQLServerPOs)  
  
-   [SQL Server 복제 성능 개체](#SQLServerReplicationPOs)  
  
-   [SSIS 파이프라인 카운터](#SsisPipelineCounters)  
  
-   [필요한 권한](#RequiredPermissions)  
  
##  <a name="SQLServerAgentPOs"></a> SQL Server 에이전트 성능 개체  
 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 사용하는 성능 개체를 나열합니다.  
  
|성능 개체|설명|  
|------------------------|-----------------|  
|[SQLAgent:Alerts](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 경고에 대한 정보를 제공합니다.|  
|[SQLAgent:Jobs](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에 대한 정보를 제공합니다.|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계에 대한 정보를 제공합니다.|  
|[SQLAgent:Statistics](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에 대한 일반적인 정보를 제공합니다.|  
  
##  <a name="ServiceBrokerPOs"></a> Service Broker 성능 개체  
 다음 표에서는 [!INCLUDE[ssSB](../../includes/sssb-md.md)]에서 사용하는 성능 개체를 나열합니다.  
  
|성능 개체|설명|  
|------------------------|-----------------|  
|[SQLServer:Broker Activation](../../relational-databases/performance-monitor/sql-server-broker-activation-object.md)|[!INCLUDE[ssSB](../../includes/sssb-md.md)]에서 활성화한 태스크에 대한 정보를 제공합니다.|  
|[SQLServer:Broker Statistics](../../relational-databases/performance-monitor/sql-server-broker-statistics-object.md)|일반적인 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 정보를 제공합니다.|  
|[SQLServer:Broker Transport](../../relational-databases/performance-monitor/sql-server-broker-dbm-transport-object.md)|[!INCLUDE[ssSB](../../includes/sssb-md.md)] 네트워킹에 대한 정보를 제공합니다.|  
  
##  <a name="SQLServerPOs"></a> SQL Server 성능 개체  
 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체에 대해 설명합니다.  
  
|성능 개체|설명|  
|------------------------|-----------------|  
|[SQLServer:Access Methods](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 개체의 할당(예: 인덱스 검색 수 또는 인덱스 및 데이터에 할당된 페이지 수)을 검색하고 측정합니다.|  
|[SQLServer:Backup Device](../../relational-databases/performance-monitor/sql-server-backup-device-object.md)|백업 장치의 처리량과 같은 백업 및 복원 작업에 사용되는 백업 장치에 관한 정보를 제공합니다.|  
|[SQLServer:Buffer Manager](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]freememory **및** buffer cache hit ratio **와 같은**에서 사용하는 메모리 버퍼에 관한 정보를 제공합니다.|  
|[SQL Server:Buffer Node](../../relational-databases/performance-monitor/sql-server-buffer-node.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 사용 가능한 페이지를 요청하고 액세스하는 빈도에 대한 정보를 제공합니다.|  
|[SQLServer:CLR](../../relational-databases/performance-monitor/sql-server-clr-object.md)|CLR(공용 언어 런타임)에 대한 정보를 제공합니다.|  
|[SQLServer:Columnstore](../../relational-databases/performance-monitor/sql-server-columnstore-object.md)|**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ~ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> columnstore 인덱스에 대한 rowgroup 및 세그먼트에 대한 정보를 제공합니다.|  
|[SQLServer:Cursor Manager by Type](../../relational-databases/performance-monitor/sql-server-cursor-manager-by-type-object.md)|커서에 대한 정보를 제공합니다.|  
|[SQLServer:Cursor Manager Total](../../relational-databases/performance-monitor/sql-server-cursor-manager-total-object.md)|커서에 대한 정보를 제공합니다.|  
|[SQLServer:Database Mirroring](../../relational-databases/performance-monitor/sql-server-database-mirroring-object.md)|데이터베이스 미러링에 대한 정보를 제공합니다.|  
|[SQLServer:Databases](../../relational-databases/performance-monitor/sql-server-databases-object.md)|사용할 수 있는 로그 공간이나 데이터베이스에서 활성화된 트랜잭션 수와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 관한 정보를 제공합니다. 이 개체에는 인스턴스가 여러 개 있을 수 있습니다.|  
|[SQL Server:Deprecated Features](../../relational-databases/performance-monitor/sql-server-deprecated-features-object.md)|사용되지 않는 기능이 사용된 횟수를 나타냅니다.|  
|[SQLServer:Exec Statistics](../../relational-databases/performance-monitor/sql-server-execstatistics-object.md)|실행 통계에 대한 정보를 제공합니다.|  
|[SQL Server:외부 스크립트](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)|**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ~ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> 외부 스크립트 실행에 대한 정보를 제공합니다.|  
|[SQLServer:General Statistics](../../relational-databases/performance-monitor/sql-server-general-statistics-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 현재 연결된 사용자 수와 같은 일반적인 서버 차원의 작업에 관한 정보를 제공합니다.|  
|[SQL Server:HADR 가용성 복제본](../../relational-databases/performance-monitor/sql-server-availability-replica.md)|현재 할당된 총 잠금 구조 수와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 가용성 복제본에 대한 정보를 제공합니다.|  
|[SQL Server:HADR 데이터베이스 복제본](../../relational-databases/performance-monitor/sql-server-database-replica.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 데이터베이스 복제본에 대한 정보를 제공합니다.|  
|[SQLServer:Latches](../../relational-databases/performance-monitor/sql-server-latches-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용하는 내부 리소스(예: 데이터베이스 페이지)에 있는 래치에 관한 정보를 제공합니다.|  
|[SQLServer:Locks](../../relational-databases/performance-monitor/sql-server-locks-object.md)|잠금 제한 시간 및 교착 상태와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 만든 개별 잠금 요청에 관한 정보를 제공합니다. 이 개체에는 인스턴스가 여러 개 있을 수 있습니다.|  
|[SQLServer:Memory Manager](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)|현재 할당된 총 잠금 구조 수와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 사용에 관한 정보를 제공합니다.|  
|[SQLServer:Plan Cache](../../relational-databases/performance-monitor/sql-server-plan-cache-object.md)|저장 프로시저, 트리거, 쿼리 계획과 같은 개체를 저장할 때 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 캐시에 관한 정보를 제공합니다.|  
|[SQLServer:Query Store](../../relational-databases/performance-monitor/sql-server-query-store-object.md)|쿼리 저장소에 대한 정보를 제공합니다.|  
|[SQLServer:Resource Pool Stats](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)|리소스 관리자 리소스 풀 통계에 대한 정보를 제공합니다.|  
|[SQLServer:SQL Errors](../../relational-databases/performance-monitor/sql-server-sql-errors-object.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류에 대한 정보를 제공합니다.|  
|[SQLServer:SQL Statistics](../../relational-databases/performance-monitor/sql-server-sql-statistics-object.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] 에서 받은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 일괄 처리 수와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]쿼리 상태에 관한 정보를 제공합니다.|  
|[SQLServer:Transactions](../../relational-databases/performance-monitor/sql-server-transactions-object.md)|전체 트랜잭션 수 및 스냅숏 트랜잭션 수와 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 활성 트랜잭션에 대한 정보를 제공합니다.|  
|[SQLServer:User Settable](../../relational-databases/performance-monitor/sql-server-user-settable-object.md)|사용자 지정 모니터링을 수행합니다. 각 카운터는 사용자 지정 저장 프로시저 또는 모니터링할 값을 반환하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 될 수 있습니다.|  
|[SQLServer:Wait Statistics](../../relational-databases/performance-monitor/sql-server-wait-statistics-object.md)|대기 정보를 제공합니다.|  
|[SQLServer:Workload Group Stats](../../relational-databases/performance-monitor/sql-server-workload-group-stats-object.md)|리소스 관리자 작업 그룹 통계에 대한 정보를 제공합니다.|  
  
##  <a name="SQLServerReplicationPOs"></a> SQL Server 복제 성능 개체  
 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제에서 사용되는 성능 개체를 나열합니다.  
  
|성능 개체|설명|  
|------------------------|-----------------|  
|**SQLServer:Replication Agents**<br /><br /> **SQLServer:Replication Snapshot**<br /><br /> **SQLServer:Replication Logreader**<br /><br /> **SQLServer:Replication Dist.**<br /><br /> **SQLServer:Replication Merge**<br /><br /> 자세한 내용은 [Monitoring Replication with System Monitor](../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md)을 참조하세요.|복제 에이전트 작업에 대한 정보를 제공합니다.|  
  
##  <a name="SsisPipelineCounters"></a> SSIS 파이프라인 카운터  
 **SSIS Pipeline** 카운터는 [성능 카운터](../../integration-services/performance/performance-counters.md)를 참조하세요.  
  
##  <a name="RequiredPermissions"></a> 필요한 권한  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLAgent:Alerts **를 제외한**개체의 사용은 Windows 권한에 따라 달라집니다. **SQLAgent:Alerts** 를 사용하려면 **sysadmin**고정 서버 역할의 멤버여야 합니다.  
  
## 참고 항목  
 [성능 개체 사용](../../ssms/agent/use-performance-objects.md)   
 [sys.dm_os_performance_counters&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  