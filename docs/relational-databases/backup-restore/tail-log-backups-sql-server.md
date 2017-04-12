---
title: "비상 로그 백업(SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "백업 [SQL Server], 비상 로그"
  - "트랜잭션 로그 백업 [SQL Server], 비상 로그 백업"
  - "NO_TRUNCATE 절"
  - "백업 [SQL Server], 로그 백업"
  - "비상 로그 백업"
  - "백업 [SQL Server], 비상 로그 백업"
ms.assetid: 313ddaf6-ec54-4a81-a104-7ffa9533ca58
caps.latest.revision: 55
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 55
---
# 비상 로그 백업(SQL Server)
  이 항목에서는 전체 또는 대량 로그 복구 모델을 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 백업 및 복원과 관련된 내용을 다룹니다.  
  
 *비상 로그 백업*에서는 아직 백업되지 않은 로그 레코드를 캡처하여(*비상 로그*) 캡처하여 작업 손실을 방지하고 로그 체인을 그대로 유지합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 마지막 시점으로 복구하려면 트랜잭션 비상 로그를 백업해야 합니다. 비상 로그 백업은 데이터베이스에 대한 복구 계획의 마지막 백업입니다.  
  
> **참고:** 모든 복원 시나리오에서 비상 로그 백업이 필요한 것은 아닙니다. 복구 시점이 이전 로그 백업에 포함될 경우에는 비상 로그 백업이 필요하지 않습니다. 데이터베이스를 이동 또는 대체(덮어쓰기)하며 가장 최근 백업 이후의 시점으로 이를 복원할 필요가 없을 경우에도 비상 로그 백업이 필요하지 않습니다.  
  
   ##  <a name="TailLogScenarios"></a> 비상 로그 백업이 필요한 시나리오  
 다음과 같은 경우에는 비상 로그 백업을 수행하는 것이 좋습니다.  
  
-   데이터베이스가 온라인이며 데이터베이스에서 복원 작업을 수행하려는 경우 먼저 비상 로그를 백업합니다. 온라인 데이터베이스에 대한 오류를 방지하려면 다음을 사용해야 합니다. [BACKUP](../../t-sql/statements/backup-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 WITH NORECOVERY 옵션입니다.  
  
-   데이터베이스가 오프라인이고 시작되지 않아서 데이터베이스를 복원해야 할 경우 먼저 비상 로그를 백업합니다. 이 시점에서는 트랜잭션이 발생할 수 없으므로 WITH NORECOVERY 옵션의 사용은 선택 사항입니다.  
  
-   데이터베이스가 손상된 경우 BACKUP 문의 WITH CONTINUE_AFTER_ERROR 옵션을 사용하여 비상 로그 백업을 수행합니다.  
  
     손상된 데이터베이스에 대한 비상 로그 백업은 로그 파일이 손상되지 않고, 데이터베이스가 비상 로그 백업을 지원하는 상태에 있고, 데이터베이스에 대량 로깅된 변경 내용이 없는 경우에만 성공할 수 있습니다. 배상 로그 백업을 만들 수 없는 경우 마지막 로그 백업 이후에 커밋된 모든 트랜잭션은 손실됩니다.  
  
 다음 표에는 BACKUP NORECOVERY 및 CONTINUE_AFTER_ERROR 옵션이 요약되어 있습니다.  
  
|BACKUP LOG 옵션|설명|  
|-----------------------|--------------|  
|NORECOVERY|데이터베이스에서 복원 작업을 계속하려는 경우 NORECOVERY를 사용합니다. NORECOVERY는 데이터베이스를 복원 중인 상태로 만듭니다. 이렇게 하면 비상 로그 백업 후 데이터베이스가 변경되지 않습니다. NO_TRUNCATE 옵션 또는 COPY_ONLY 옵션을 함께 지정하지 않으면 로그가 잘립니다.<br /><br /> **\*\* 중요 \*\*** 데이터베이스가 손상된 경우가 아니면 NO_TRUNCATE는 사용하지 마세요.|  
|CONTINUE_AFTER_ERROR|손상된 데이터베이스의 비상 로그를 백업하는 경우에만 CONTINUE_AFTER_ERROR를 사용합니다.<br /><br /> 손상된 데이터베이스에서 비상 로그 백업을 사용하는 경우에는 일반적으로 로그 백업에서 캡처되는 메타데이터 일부를 사용할 수 없을 수 있습니다. 자세한 내용은 이 항목의 [완전하지 않은 백업 메타데이터가 포함된 비상 로그 백업](#IncompleteMetadata)을 참조하세요.|  
  
##  <a name="IncompleteMetadata"></a> 완전하지 않은 백업 메타데이터가 포함된 비상 로그 백업  
 비상 로그 백업은 데이터베이스가 오프라인이거나 손상되었거나 데이터 파일이 없는 경우에도 비상 로그를 캡처합니다. 이로 인해 복원 정보 명령과 **msdb**의 메타데이터가 완전하지 않을 수 있습니다. 그러나 메타데이터가 완전하지 않은 경우에도 캡처된 로그는 완전한 상태이며 사용 가능합니다.  
  
 비상 로그 백업에 완전하지 않은 메타데이터가 있으면 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md) 테이블의 **has_incomplete_metadata**가 **1**로 설정됩니다. 또한 [RESTORE HEADERONLY](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)출력에서 **HasIncompleteMetadata** 는 **1**로 설정됩니다.  
  
 비상 로그 백업의 메타데이터가 완전하지 않으면 [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md) 테이블은 비상 로그 백업 당시 파일 그룹에 대한 대부분의 정보를 잃게 됩니다. 대부분의 **backupfilegroup** 테이블 열은 NULL이 되며 다음 열만 의미를 갖습니다.  
  
-   **backup_set_id**  
  
-   **filegroup_id**  
  
-   **유형**  
  
-   **type_desc**  
  
-   **is_readonly**  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
 비상 로그 백업을 만들려면 [데이터베이스가 손상된 경우 트랜잭션 로그 백업&#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)을 참조하세요.  
  
 트랜잭션 로그 백업을 복원하려면 [트랜잭션 로그 백업 복원&#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)을 참조하세요.  
    
## 관련 항목:  
 [BACKUP&#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [RESTORE&#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [SQL Server 데이터베이스 백업 및 복원](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [복사 전용 백업&#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [트랜잭션 로그 백업&#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)   
 [트랜잭션 로그 백업 적용&#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)  
  
  