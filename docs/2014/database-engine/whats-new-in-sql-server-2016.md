---
title: 새로운&#39;s (데이터베이스 엔진) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- what's new [SQL Server Database Engine]
- Database Engine [SQL Server], what's new
ms.assetid: 8f625d5a-763c-4440-97b8-4b823a6e2439
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ac9a6a1b2d4107d420bab68659b6d05f25805a38
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067033"
---
# <a name="what39s-new-database-engine"></a>새로운&#39;s (데이터베이스 엔진)
  [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]의 최신 릴리스에는 데이터 저장소 시스템을 디자인, 개발 및 유지 관리하는 설계자, 개발자 및 관리자의 작업 효율성과 생산성을 증대시키는 새로운 기능과 향상된 기능이 추가되었습니다. 다음은 [!INCLUDE[ssDE](../includes/ssde-md.md)]에서 향상된 기능에 대한 설명입니다.  
  
##  <a name="Feature"></a> 데이터베이스 엔진의 향상 된 기능  
  
###  <a name="MemoryOpt"></a> 메모리 최적화 테이블  
 메모리 내 OLTP는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 엔진에 통합된 메모리 최적화 데이터베이스 엔진이며 OLTP용으로 최적화되어 있습니다. 자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
 
  
###  <a name="DataFiles"></a> Windows Azure에서 SQL Server 데이터 파일  
 [Windows Azure의 SQL Server 데이터 파일](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md) 에 대 한 네이티브 지 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 파일을 Windows Azure Blob으로 저장 합니다. 이 기능을 통해 Microsoft Azure BLOB 저장소의 데이터에 대한 전용 저장소 위치와 함께 온-프레미스 또는 Microsoft Azure의 가상 머신에서 실행 중인 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 데이터베이스를 만들 수 있습니다.  
  
  
###  <a name="AzureVM"></a> Windows의 SQL Server 데이터베이스를 호스팅할 Azure 가상 머신  
 사용 된 [Windows Azure 가상 컴퓨터에 SQL Server 데이터베이스 배포](http://msdn.microsoft.com/library/dn195938\(v=sql.120\).aspx) 인스턴스에서 데이터베이스를 호스트 하는 마법사를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows Azure 가상 컴퓨터에서.  
  
  
###  <a name="Backup"></a> 백업 및 복원 향상  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서는 다음과 같이 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 백업 및 복원 기능이 향상되었습니다.  
  
-   **URL에 대한 SQL Server 백업**  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], PowerShell 및 SMO에서만 지원되는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] SP1 CU2에 [!INCLUDE[tsql](../includes/tsql-md.md)] URL 백업이 도입되었습니다. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 Windows Azure BLOB 저장소 서비스로 백업하거나 이 서비스에서 복원할 수 있습니다. 새로운 옵션은 백업 태스크와 유지 관리 계획에 사용할 수 있습니다. 자세한 내용은 [Using Backup Task in SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#BackupTaskSSMS)를 [SQL Server Backup to URL Using Maintenance Plan Wizard](../relational-databases/backup-restore/sql-server-backup-to-url.md#MaintenanceWiz), 및 [Windows Azure storage에서 복원를 사용 하 여 SQL Server Management Studio](../relational-databases/backup-restore/sql-server-backup-to-url.md#RestoreSSMS)합니다.  
  
-   **Windows Azure에 대한 SQL Server 관리되는 백업**  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] URL 백업을 기반으로 하는 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]는 데이터베이스 및 로그 백업을 관리하고 예약하기 위해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 제공하는 서비스입니다. 이 릴리스에서는 Windows Azure 저장소에 대한 백업만 지원됩니다. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]은 데이터베이스 수준뿐만 아니라 인스턴스 수준에서도 구성될 수 있으므로 데이터베이스 수준의 세부 제어와 인스턴스 수준의 자동화를 활용할 수 있도록 합니다. [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]는 온-프레미스로 실행되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스와 Windows Azure 가상 컴퓨터에서 실행되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에서 구성할 수 있지만, Windows Azure 가상 컴퓨터에서 실행되는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 사용하는 것이 좋습니다. 자세한 내용은 [SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)합니다.  
  
-   **백업 위한 암호화**  
  
     이제 백업 작업 중에 백업 파일을 암호화하도록 선택할 수 있습니다.  AES 128, AES 192, AES 256 및 Triple DES를 비롯한 몇 가지 암호화 알고리즘이 지원됩니다. 인증서나 비대칭 키를 사용하여 백업 중에 암호화를 수행해야 합니다. 자세한 내용은 [백업 암호화](../relational-databases/backup-restore/backup-encryption.md)합니다.  
  
  
###  <a name="CE"></a> 카디널리티 추정에 대 한 새로운 디자인  
 카디널리티 평가기 라고 하는 카디널리티 추정 논리가에서 다시 디자인 되었습니다 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 쿼리 계획의 품질을 향상 시키는 있어 쿼리 성능을 향상 시킵니다. 새로운 카디널리티 평가기는 최신 OLTP 및 데이터 웨어하우징 작업에서 제대로 작동하는 가정 및 알고리즘을 통합합니다. 이 평가기는 최신 작업에 대한 자세한 카디널리티 추정 연구와 SQL Server 카디널리티 평가기를 향상시키기 위해 과거 15년 동안 학습한 지식을 기반으로 합니다. 고객의 의견은 대부분의 쿼리가 변경을 통해 이점을 얻거나 변경되지 않은 채로 유지되는 반면 소수의 쿼리는 이전 카디널리티 평가기와 비교했을 때 회귀를 보여줄 수도 있음을 나타냅니다. 성능 튜닝 및 권장 사항을 테스트에 대 한 참조 [카디널리티 추정 &#40;SQL Server&#41;](../relational-databases/performance/cardinality-estimation-sql-server.md)합니다.  
   
  
###  <a name="Durability"></a> 지연 된 내구성  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에는 일부 또는 모든 트랜잭션을 지연된 내구성을 갖도록 지정하여 대기 시간을 줄이는 기능이 도입되었습니다. 지연된 내구성이 있는 트랜잭션은 트랜잭션 로그 레코드가 디스크에 기록되기 전에 클라이언트에 제어를 반환합니다. 내구성은 데이터베이스 수준, COMMIT 수준 또는 ATOMIC 블록 수준에서 제어할 수 있습니다.  
  
 자세한 내용은 항목을 참조 하세요 [트랜잭션 내구성 제어](../relational-databases/logs/control-transaction-durability.md)입니다.  
  
  
###  <a name="AlwaysOn"></a> 향상 된 AlwaysOn 기능  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에는 AlwaysOn 장애 조치(Failover) 클러스터 인스턴스와 AlwaysOn 가용성 그룹에 대한 다음과 같은 향상된 기능이 포함되어 있습니다.  
  
-   Azure 복제본 추가 마법사는 AlwaysOn 가용성 그룹에 대한 하이브리드 솔루션을 만드는 작업을 단순화합니다. 자세한 내용은 [Azure 복제본 추가 마법사를 사용 하 여 &#40;SQL Server&#41;](availability-groups/windows/use-the-add-azure-replica-wizard-sql-server.md)합니다.  
  
-   보조 복제본의 최대 개수는 4개에서 8개로 증가되었습니다.  
  
-   주 복제본에서 분리될 때 또는 클러스터 쿼럼 손실 중에 읽기 작업을 위해 읽기 가능한 보조 복제본을 계속 사용할 수 있습니다.  
  
-   FCI(장애 조치(Failover) 클러스터 인스턴스)는 이제 CSV(클러스터 공유 볼륨)를 클러스터 공유 디스크로 사용할 수 있습니다. 자세한 내용은 [Always On 장애 조치 클러스터 인스턴스](../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)합니다.  
  
-   새 시스템 함수인 [sys.fn_hadr_is_primary_replica](/sql/relational-databases/system-functions/sys-fn-hadr-is-primary-replica-transact-sql)와 새로운 DMV 인 [sys.dm_io_cluster_valid_path_names](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql), 사용할 수 있습니다.  
  
-   Dmv가 향상 되어 이제 FCI 정보를 반환 합니다. [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)를 [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), 및 [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)합니다.  
  
  
###  <a name="OIR"></a> 파티션 전환 및 인덱싱  
 이제 분할 테이블의 개별 파티션을 다시 작성할 수 있습니다. 자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.  
   
  
###  <a name="Lock"></a> 온라인 작업의 잠금 우선도 관리  
 `ONLINE = ON` 옵션에 포함된 `WAIT_AT_LOW_PRIORITY` 옵션을 통해 다시 작성 프로세스에서 필요한 잠금을 대기해야 하는 시간을 지정할 수 있습니다. `WAIT_AT_LOW_PRIORITY` 옵션에서는 또한 해당 REBUILD 문에 관련된 차단 프로세스 종료를 구성할 수 있습니다. 자세한 내용은 [ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) 및 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요. 새로운 유형의 잠금 상태에 대 한 정보를 문제 해결 하는 것은 영어로 [sys.dm_tran_locks &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql) 하 고 [sys.dm_os_wait_stats &#40;Transact SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).  
 
  
###  <a name="CCI"></a> Columnstore 인덱스  
 이러한 새로운 기능은 columnstore 인덱스에 사용할 수 있습니다.  
  
-   **클러스터형된 columnstore 인덱스**  
  
     클러스터형 columnstore 인덱스를 사용해서 주로 대량 로드 및 읽기 전용 쿼리를 수행하는 데이터 웨어하우징 작업의 데이터 압축 및 쿼리 성능을 향상시킬 수 있습니다. 클러스터형 columnstore 인덱스는 업데이트 가능하므로 해당 작업에서 여러 삽입, 업데이트 및 삭제 작업을 수행할 수 있습니다. 자세한 내용은 [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md) 하 고 [클러스터형 Columnstore 인덱스를 사용 하 여](../relational-databases/indexes/indexes.md)입니다.  
  
-   **실행 계획**  
  
     SHOWPLAN에서는 columnstore 인덱스 정보를 표시합니다. **EstimatedExecutionMode** 및 **ActualExecutionMode** 속성에 가능한 두 개의 값은 **Batch** 또는 **Row**입니다.  **Storage** 속성에 가능한 두 개의 값은 **RowStore** 및 **ColumnStore**입니다.  
  
-   **보관 데이터 압축**  
  
     ALTER INDEX … REBUILD에는 columnstore 인덱스의 지정된 파티션을 추가로 압축하는 새로운 COLUMNSTORE_ARCHIVE 데이터 압축 옵션이 있습니다. 이 옵션을 보관 또는 데이터 저장소 크기를 줄여야 하는 기타 상황에 사용할 수 있으며 저장 및 검색에 더 많은 시간을 이용할 수 있습니다. 자세한 내용은 [ALTER INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)를 참조하세요.  
   
  
###  <a name="Buffer"></a> 버퍼 풀 확장  
 합니다 [버퍼 풀 확장](configure-windows/buffer-pool-extension.md) 는 비휘발성 임의 액세스 메모리 (NvRAM) 확장으로 SSD (반도체 드라이브)의 원활한 통합을 제공 합니다 [!INCLUDE[ssDE](../includes/ssde-md.md)] 버퍼 풀 I/O 처리량을 크게 향상 합니다.  
   
  
###  <a name="Stats"></a> 증분 통계  
 이제 CREATE STATISTICS 및 관련 통계 문이 INCREMENTAL 옵션을 사용한 파티션별 통계 생성을 허용합니다. 관련 문은 증분 통계를 허용 또는 보고합니다. 영향을 받는 구문은 UPDATE STATISTICS, sp_createstats, CREATE INDEX, ALTER INDEX, ALTER DATABASE SET 옵션, DATABASEPROPERTYEX, sys.databases 및 sys.stats입니다. 자세한 내용은 [CREATE STATISTICS&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)를 참조하세요.  
  
  
###  <a name="RG"></a> 물리적 IO 제어를 위한 향상 된 리소스 관리자  
 리소스 관리자를 사용하면 들어오는 응용 프로그램 요청이 리소스 풀에서 사용할 수 있는 CPU, 물리적 IO 및 메모리 양에 대한 제한을 지정할 수 있습니다. [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서는 새로운 MIN_IOPS_PER_VOLUME 및 MAX_IOPS_PER_VOLUME 설정을 사용하여 지정된 리소스 풀의 사용자 스레드에 대해 발생하는 물리적 IO를 제어할 수 있습니다. 자세한 내용은 참조 하세요. [Resource Governor Resource Pool](../relational-databases/resource-governor/resource-governor-resource-pool.md) 하 고 [CREATE RESOURCE POOL &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).  
  
 ALTER RESOURCE GOVENOR의 MAX_OUTSTANDING_IO_PER_VOLUME 설정은 디스크 볼륨당 최대 미해결 I/O 작업을 설정합니다. 이 설정을 사용하여 디스크 볼륨의 IO 특성에 맞게 IO 리소스 관리를 튜닝할 수 있으며 SQL Server 인스턴스 경계에서 발생하는 IO 수를 제한할 수 있습니다. 자세한 내용은 [ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)를 참조하세요.  
  
  
###  <a name="OnlineEvent"></a> Online Index Operation 이벤트 클래스  
 이제 Progress Report: Online Index Operation 이벤트 클래스에 **PartitionId** 및 **PartitionNumber**라는 두 개의 새 데이터 열이 있습니다. 자세한 내용은 [Progress Report: Online Index Operation 이벤트 클래스](../relational-databases/event-classes/progress-report-online-index-operation-event-class.md)합니다.  
  
  
###  <a name="Compat"></a> 데이터베이스 호환성 수준  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서는 호환성 수준 90이 올바르지 않습니다. 자세한 내용은 [ALTER DATABASE 호환성 수준 &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
##  <a name="TSQL"></a> 향상된 Transact-SQL 기능  
  
### <a name="inline-specification-of-clustered-and-nonclustered"></a>CLUSTERED 및 NONCLUSTERED의 인라인 사양  
 `CLUSTERED` 및 `NONCLUSTERED` 인덱스의 인라인 사양은 이제 디스크 기반 테이블에 허용됩니다. 인라인 인덱스를 사용하여 테이블을 만드는 것은 해당 `CREATE INDEX` 문 다음에 테이블 만들기를 실행하는 것과 같습니다. 포함된 열 및 필터 조건은 인라인 인덱스에서는 지원되지 않습니다.  
  
### <a name="select--into"></a>SELECT … INTO  
 `SELECT … INTO` 문이 향상되어 이제 병렬로 실행될 수 있습니다. 데이터베이스 호환성 수준은 110 이상이어야 합니다.  
  
### <a name="includetsqlincludestsql-mdmd-enhancements-for-in-memory-oltp"></a>메모리 내 OLTP에 대한 향상된 [!INCLUDE[tsql](../includes/tsql-md.md)] 기능  
 에 대 한 자세한 합니다 [!INCLUDE[tsql](../includes/tsql-md.md)] 메모리 내 OLTP를 지원 하기 위해 변경 내용 [메모리 내 OLTP에 대 한 TRANSACT-SQL 지원](../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)합니다.  
  
  
##  <a name="SystemTable"></a> 향상된 시스템 뷰 기능  
  
### <a name="sysxmlindexes"></a>sys.xml_indexes  
 [sys.xml_indexes &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-xml-indexes-transact-sql) 새로운 세 개의 열: `xml_index_type`합니다 `xml_index_type_description`, 및 `path_id`.  
  
### <a name="sysdmexecqueryprofiles"></a>sys.dm_exec_query_profiles  
 [sys.dm_exec_query_profiles &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql) 쿼리를 실행 중인 동안 실시간 쿼리 프로세스를 모니터링 합니다.  
  
### <a name="syscolumnstorerowgroups"></a>sys.column_store_row_groups  
 [sys.column_store_row_groups &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql) 관리자가 시스템 관리 의사 결정을 확인 하는 데는 세그먼트 단위 기반의 방식으로 클러스터형된 columnstore 인덱스 정보를 제공 합니다.  
  
### <a name="sysdatabases"></a>sys.databases  
 [sys.databases &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 새로운 세 개의 열: `is_auto_create_stats_incremental_on`합니다 `is_query_store_on`, 및 `resource_pool_id`.  
  
### <a name="system-view-enhancements-for-in-memory-oltp"></a>메모리 내 OLTP에 대한 향상된 시스템 뷰 기능  
 메모리 내 OLTP를 지원 하기 위해 향상 된 시스템 뷰 기능에 대 한 정보를 참조 하세요 [시스템 뷰, 저장 프로시저, Dmv 및 메모리 내 OLTP에 대 한 대기 유형](../../2014/database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)합니다.  
   
  
##  <a name="Security"></a> 향상된 보안 기능  
  
### <a name="connect-any-database-permission"></a>CONNECT ANY DATABASE 권한  
 새로운 서버 수준 사용 권한입니다. 현재 있는 모든 데이터베이스와 향후 만들 수 있는 새로운 데이터베이스에 연결해야 하는 로그인에 **CONNECT ANY DATABASE** 를 부여합니다. 연결을 벗어나는 데이터베이스에서는 사용 권한을 부여하지 않습니다. 결합할 **SELECT ALL USER SECURABLES** 하거나 `VIEW SERVER STATE` 인스턴스의 모든 데이터 또는 모든 데이터베이스 상태 보기를 위한 감사 프로세스를 허용 하도록 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]합니다.  
  
### <a name="impersonate-any-login-permission"></a>IMPERSONATE ANY LOGIN 권한  
 새로운 서버 수준 사용 권한입니다. 허용하면 데이터베이스에 연결할 때 중간 계층 프로세스가 클라이언트 계정을 가장하여 연결할 수 있습니다. 거부하면 높은 권한 로그인이 다른 로그인을 가장하지 못하도록 차단할 수 있습니다. 예를 들어, **CONTROL SERVER** 권한이 있는 로그인이 다른 로그인을 가장하지 못하도록 차단할 수 있습니다.  
  
### <a name="select-all-user-securables-permission"></a>SELECT ALL USER SECURABLES 권한  
 새로운 서버 수준 사용 권한입니다. 허용하면 감사자 등으로 로그인하여 사용자 연결이 가능한 모든 데이터베이스에서 데이터를 볼 수 있습니다.  
  
  
##  <a name="Deployment"></a> 배포 향상  
### <a name="azure-vm"></a>Azure VM
[Microsoft Azure Virtual Machine에 SQL Server 데이터베이스 배포](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md) 배포할 수 있습니다는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows Azure VM에 데이터베이스입니다.  

### <a name="refs"></a>ReFS
ReFS에 데이터베이스 배포 이제 지원 됩니다.   
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 2014 버전에서 지원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
   
