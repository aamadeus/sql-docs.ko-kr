---
title: sys.dm_db_log_space_usage (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sys.dm_db_log_space_usage
- sys.dm_db_log_space_usage_TSQL
- dm_db_log_space_usage
- dm_db_log_space_usage_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_log_space_usage dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
caps.latest.revision: "4"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f4dfc548cdc7c2ece756e86f753a8bc21513f158
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdblogspaceusage-transact-sql"></a>sys.dm_db_log_space_usage (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  공간 데이터베이스 로그에 대 한 사용량 정보를 반환 합니다. (모든 로그 파일 결합 됩니다.) 
  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|데이터베이스 ID입니다.|  
|total_log_size_in_bytes |**bigint** |로그의 크기  |
|used_log_space_in_bytes |**bigint** |이미 사용 중인된 로그의 크기  |     
|used_log_space_in_percent |**real** |이미 사용 중인된 총 로그 크기의 백분율로 로그 크기 |
|log_space_in_bytes_since_last_backup |**bigint** |마지막 로그 백업 이후에 사용 되는 공간의 양 <br />**적용 대상:** [!INCLUDE[sssql14-md](../../includes/sssql14-md.md)] 통해 [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]합니다.|
    
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 필요 `VIEW SERVER STATE` 서버에 대 한 권한이 있습니다.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 프리미엄 계층 필요는 `VIEW DATABASE STATE` 데이터베이스에는 권한이 있습니다. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 표준 및 기본 계층 필요는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 관리자 계정.  
  
## <a name="examples"></a>예  
  
### <a name="a-determine-the-amount-of-free-log-space-in-tempdb"></a>1. Tempdb에 가능한 로그 양 공간 확인   
다음 쿼리에서 메가바이트 (MB) tempdb에서 사용할 수 있는의 총 사용 가능한 로그 공간을 반환합니다.

```tsql
USE tempdb;  
GO  

SELECT (total_log_size_in_bytes - used_log_space_in_bytes)*1.0/1024/1024 AS [free log space in MB]  
FROM sys.dm_db_log_space_usage;  
```
  
## <a name="see-also"></a>관련 항목:  
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [데이터베이스 관련된 동적 관리 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_file_space_usage](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)    
 [sys.dm_db_task_space_usage&#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_session_space_usage&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  
[sys.dm_db_log_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-info-transact-sql.md) 


