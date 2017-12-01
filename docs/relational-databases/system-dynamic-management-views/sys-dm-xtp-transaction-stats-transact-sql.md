---
title: sys.dm_xtp_transaction_stats (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
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
- dm_xtp_transaction_stats_TSQL
- dm_xtp_transaction_stats
- sys.dm_xtp_transaction_stats_TSQL
- sys.dm_xtp_transaction_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_xtp_transaction_stats dynamic management view
ms.assetid: 9389f48d-0de5-47bd-9821-4db8f04504e4
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d45bce18823edbaeeb0025ed3edd237fa3174a4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmxtptransactionstats-transact-sql"></a>sys.dm_xtp_transaction_stats(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  서버를 시작한 후 실행된 트랜잭션에 대한 통계를 보고합니다.  
  
 자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|메모리 내 OLTP 데이터베이스 엔진에서 실행된 총 트랜잭션 수입니다.|  
|read_only_count|**bigint**|읽기 전용 트랜잭션 수입니다.|  
|total_aborts|**bigint**|사용자 또는 시스템 중단을 통해 중단된 트랜잭션 총 수입니다.|  
|user_aborts|**bigint**|시스템에서 시작된 중단 수입니다. 예를 들어 쓰기 충돌, 유효성 검사 오류 또는 종속성 오류로 인한 것입니다.|  
|validation_failures|**bigint**|유효성 검사 오류로 인해 트랜잭션이 중단된 횟수입니다.|  
|dependencies_taken|**bigint**|내부적으로만 사용됩니다.|  
|dependencies_failed|**bigint**|종속된 트랜잭션 중단으로 인해 트랜잭션이 중단된 횟수입니다.|  
|savepoint_create|**bigint**|만들어진 저장점 수입니다. 새로운 저장점은 모든 원자 블록에 대해 만들어집니다.|  
|savepoint_rollbacks|**bigint**|이전 저장점으로의 롤백 수입니다.|  
|savepoint_refreshes|**bigint**|내부적으로만 사용됩니다.|  
|log_bytes_written|**bigint**|메모리 내 OLTP 로그 레코드에 기록된 전체 바이트 수입니다.|  
|log_IO_count|**bigint**|로그 IO를 필요로 하는 총 트랜잭션 수입니다. 내구성 테이블의 트랜잭션만 고려합니다.|  
|phantom_scans_started|**bigint**|내부적으로만 사용됩니다.|  
|phatom_scans_retries|**bigint**|내부적으로만 사용됩니다.|  
|phantom_rows_touched|**bigint**|내부적으로만 사용됩니다.|  
|phantom_rows_expiring|**bigint**|내부적으로만 사용됩니다.|  
|phantom_rows_expired|**bigint**|내부적으로만 사용됩니다.|  
|phantom_rows_expired_removed|**bigint**|내부적으로만 사용됩니다.|  
|scans_started|**bigint**|내부적으로만 사용됩니다.|  
|scans_retried|**bigint**|내부적으로만 사용됩니다.|  
|rows_returned|**bigint**|내부적으로만 사용됩니다.|  
|rows_touched|**bigint**|내부적으로만 사용됩니다.|  
|rows_expiring|**bigint**|내부적으로만 사용됩니다.|  
|rows_expired|**bigint**|내부적으로만 사용됩니다.|  
|rows_expired_removed|**bigint**|내부적으로만 사용됩니다.|  
|rows_inserted|**bigint**|내부적으로만 사용됩니다.|  
|rows_updated|**bigint**|내부적으로만 사용됩니다.|  
|rows_deleted|**bigint**|내부적으로만 사용됩니다.|  
|write_conflicts|**bigint**|내부적으로만 사용됩니다.|  
|unique_constraint_violations|**bigint**|고유한 제약 조건 위반 총 수입니다.|  
  
## <a name="permissions"></a>Permissions  
 을 실행하려면 서버에 대해 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [메모리 액세스에 최적화 된 테이블 동적 관리 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  