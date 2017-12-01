---
title: sys.dm_db_log_stats (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 05/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_log_stats_TSQL
- sys.dm_db_log_stats
- sys.dm_db_log_stats_TSQL
- dm_db_log_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_stats dynamic management function
ms.assetid: 
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba933bad47beead99ea5f645a910b1783caa280e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdblogstats-transact-sql"></a>sys.dm_db_log_stats (Transact SQL)   
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

데이터베이스의 트랜잭션 로그 파일 요약 수준 속성 및 정보를 반환합니다. 이 정보를 사용 하 여 모니터링 및 진단의 트랜잭션 로그 상태에 대 한 합니다.   
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
 sys.dm_db_log_stats ( database_id )
```  
  
## <a name="arguments"></a>인수  

*database_id* | NULL | **기본값**

데이터베이스의 ID입니다. `database_id`은 `int`입니다. 올바른 입력은 데이터베이스의 ID 번호 `NULL`, 또는 `DEFAULT`합니다. 기본값은 `NULL`입니다. `NULL`및 `DEFAULT` 는 현재 데이터베이스의 컨텍스트에서 동등한 값입니다.  
기본 제공 함수 `DB_ID` 지정할 수 있습니다. 사용 하는 경우 `DB_ID` 데이터베이스 이름을 지정 하지 않고 현재 데이터베이스의 호환성 수준은 90 이상 이어야 합니다.

  
## <a name="tables-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|database_id    |**int**    |데이터베이스 ID |  
|recovery_model |**nvarchar (60)**   |   데이터베이스의 복구 모델입니다. 가능한 값은 다음과 같습니다. <br /> SIMPLE<br /> BULK_LOGGED <br /> FULL |  
|log_min_lsn    |**nvarchar(24)**   |   트랜잭션 로그의 현재 시작 LSN입니다. |  
|log_end_lsn    |**nvarchar(24)**   |   트랜잭션 로그의 마지막 로그 레코드의 LSN입니다. |  
|current_vlf_sequence_number    |**bigint** |   VLF의 현재 시퀀스 번호 시간에 실행 합니다. |  
|current_vlf_size_mb    |**float**  |   현재 VLF 크기 (MB)입니다. |   
|total_vlf_count    |**bigint** |   Vlf 트랜잭션 로그의 총 수입니다. |  
|total_log_size_mb  |**float**  |   총 트랜잭션 로그 크기 (MB)입니다. |  
|active_vlf_count   |**bigint** |   트랜잭션 로그에 활성 상태의 Vlf의 총 수입니다. |  
|active_log_size_mb |**float**  |   총 활성 트랜잭션 로그 크기 (MB)입니다. |  
|log_truncation_holdup_reason   |**nvarchar (60)**   |   로그 잘림은 남기는 이유입니다. 값이 동일 `log_reuse_wait_desc` 열 `sys.databases`합니다.  (이러한 값에 대 한 설명과 자세한 [트랜잭션 로그](../../relational-databases/logs/the-transaction-log-sql-server.md)). <br />가능한 값은 다음과 같습니다. <br />NOTHING<br />CHECKPOINT<br />LOG_BACKUP<br />ACTIVE_BACKUP_OR_RESTORE<br />ACTIVE_TRANSACTION<br />DATABASE_MIRRORING<br />복제<br />DATABASE_SNAPSHOT_CREATION<br />LOG_SCAN<br />AVAILABILITY_REPLICA<br />OLDEST_PAGE<br />XTP_CHECKPOINT<br />기타 일시적 |  
|log_backup_time    |**datetime**   |   마지막 트랜잭션 로그 백업 시간입니다. |   
|log_backup_lsn |**nvarchar(24)**   |   마지막 트랜잭션 로그 백업 LSN입니다. |   
|log_since_last_log_backup_mb   |**float**  |   마지막 트랜잭션 로그 백업 LSN 이후에 로그 크기 (MB)입니다. |  
|log_checkpoint_lsn |**nvarchar(24)**   |   마지막 검사점 LSN입니다. |  
|log_since_last_checkpoint_mb   |**float**  |   마지막 검사점 LSN 이후에 로그 크기 (MB)입니다. |  
|log_recovery_lsn   |**nvarchar(24)**   |   복구 데이터베이스의 LSN입니다. 경우 `log_recovery_lsn` 검사점 LSN 앞에 오는 `log_recovery_lsn` 그렇지 않으면 가장 오래 된 활성 트랜잭션 LSN는 `log_recovery_lsn` 는 검사점 LSN입니다. |  
|log_recovery_size_mb   |**float**  |   로그 복구 LSN 이후의 로그 크기 (MB)입니다. |  
|recovery_vlf_count |**bigint** |   장애 조치 또는 서버 다시 시작 하는 경우 복구 하려면 Vlf의 총 수입니다. |  


## <a name="permissions"></a>Permissions  
필요는 `VIEW DATABASE STATE` 데이터베이스에는 권한이 있습니다.   
  
## <a name="examples"></a>예  

### <a name="a-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-high-number-of-vlfs"></a>1. 데이터베이스를 결정 하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 수많은 vlf 사용 하 여 인스턴스   
다음 쿼리는 로그 파일에 100 개 이상의 vlf 포함 된 데이터베이스를 반환합니다. 많은 수의 Vlf 데이터베이스 시작, 복원 및 복구 시간에 영향을 줄 수입니다.

``` t-sql  
SELECT name AS 'Database Name', total_vlf_count AS 'VLF count' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id) 
WHERE total_vlf_count  > 100;
```   

### <a name="b-determining-databases-in-a-includessnoversionincludesssnoversion-mdmd-instance-with-transaction-log-backups-older-than-4-hours"></a>2. 데이터베이스를 결정 하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 4 시간 보다 오래 된 트랜잭션 로그 백업 사용 하 여 인스턴스   
다음 쿼리는 인스턴스에 있는 데이터베이스에 대 한 마지막 로그 백업 시간을 결정합니다.

``` t-sql  
SELECT name AS 'Database Name', log_backup_time AS 'last log backup time' 
FROM sys.databases AS s
CROSS APPLY sys.dm_db_log_stats(s.database_id); 
```

## <a name="see-also"></a>관련 항목:  
[동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[데이터베이스 관련된 동적 관리 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md)  

  