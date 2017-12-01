---
title: sys.dm_exec_procedure_stats (TRANSACT-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: f935b0e9a4c150830a03ecb2ea1f67a4cd270d3f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecprocedurestats-transact-sql"></a>sys.dm_exec_procedure_stats(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  캐시된 저장 프로시저에 대한 집계 성능 통계를 반환합니다. 이 뷰에는 캐시된 각 저장 프로시저 계획에 대해 하나의 행이 반환되며 행의 유효 기간은 저장 프로시저가 캐시에 남아 있는 기간과 같습니다. 캐시에서 저장 프로시저가 제거되면 이 뷰에서도 해당 행이 제거됩니다. 이때 Performance Statistics SQL 추적 이벤트가 발생 비슷합니다 **sys.dm_exec_query_stats**합니다.  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]에서 동적 관리 뷰는 데이터베이스 포함에 영향을 줄 수 있는 정보 또는 사용자가 액세스할 수 있는 다른 데이터베이스 정보를 노출할 수 없습니다. 이러한 정보 노출을 방지하기 위해 연결된 테넌트에 속하지 않는 데이터가 포함된 행은 모두 필터링됩니다.  
  
> **참고:** 의 초기 쿼리 **sys.dm_exec_procedure_stats** 중인 서버에서 현재 실행 중인 작업이 있을 경우 부정확 한 결과가 나올 수 있습니다. 쿼리를 다시 실행하면 보다 정확한 결과를 확인할 수 있습니다.  
  
> **Azure SQL 데이터 웨어하우스에 대 한 참고!** 이 메서드를 호출 하려면 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 또는 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], 이름을 사용 하 여 **sys.dm_pdw_nodes_exec_procedure_stats**합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|이 저장 프로시저가 있는 데이터베이스의 ID입니다.|  
|**object_id**|**int**|이 저장 프로시저의 개체 ID입니다.|  
|**유형**|**char(2)**|개체의 유형입니다.<br /><br /> P = SQL 저장 프로시저<br /><br /> PC = 어셈블리(CLR) 저장 프로시저<br /><br /> X = 확장 저장 프로시저|  
|**type_desc**|**nvarchar (60)**|개체 유형에 대한 설명:<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary(64)**|이 쿼리는 상관 관계를 사용할 수 있습니다 **sys.dm_exec_query_stats** 이 저장된 프로시저 내에서 실행 된 합니다.|  
|**plan_handle**|**varbinary(64)**|메모리 내 계획의 식별자입니다. 이 식별자는 일시적이며 계획이 캐시에 있는 동안에만 일정하게 유지됩니다. 이 값을 함께 사용할 수 있습니다는 **sys.dm_exec_cached_plans** 동적 관리 뷰.<br /><br /> 고유하게 컴파일된 저장 프로시저에서 메모리 최적화 테이블을 쿼리하는 경우 항상 0x000입니다.|  
|**cached_time**|**datetime**|이 저장 프로시저가 캐시에 추가된 시간입니다.|  
|**last_execution_time**|**datetime**|이 저장 프로시저가 마지막으로 실행된 시간입니다.|  
|**execution_count**|**bigint**|이 저장 프로시저가 마지막으로 컴파일된 이후 실행된 횟수입니다.|  
|**total_worker_time**|**bigint**|이 저장 프로시저가 컴파일된 이후 실행되는 데 사용된 총 CPU 시간(마이크로초)입니다.<br /><br /> 고유하게 컴파일된 저장 프로시저의 경우 1초 미만이 소요되는 실행이 많으면 **total_worker_time** 이 정확하지 않을 수 있습니다.|  
|**last_worker_time**|**bigint**|이 저장 프로시저가 마지막으로 실행될 때 사용된 CPU 시간(마이크로초)입니다. <sup>1</sup>|  
|**min_worker_time**|**bigint**|단일 실행 중 이 저장 프로시저에 사용된 최소 CPU 시간(마이크로초)입니다. <sup>1</sup>|  
|**max_worker_time**|**bigint**|단일 실행 중 이 저장 프로시저에 사용된 최대 CPU 시간(마이크로초)입니다. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|이 저장 프로시저가 컴파일된 이후 실행될 때 수행된 총 물리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**last_physical_reads**|**bigint**|이 저장 프로시저가 마지막으로 실행될 때 수행된 물리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**min_physical_reads**|**bigint**|단일 실행 중 이 저장 프로시저가 수행한 최소 물리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**max_physical_reads**|**bigint**|단일 실행 중 이 저장 프로시저가 수행한 최대 물리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**total_logical_writes**|**bigint**|이 저장 프로시저가 컴파일된 이후 실행될 때 수행된 총 논리적 쓰기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**last_logical_writes**|**bigint**|계획이 마지막으로 실행될 때 변경된 버퍼 풀 페이지 수입니다. 페이지가 이미 변경된(수정된) 경우에는 쓰기 수가 계산되지 않습니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**min_logical_writes**|**bigint**|단일 실행 중 이 저장 프로시저가 수행한 최소 논리적 쓰기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**max_logical_writes**|**bigint**|단일 실행 중 이 저장 프로시저가 수행한 최대 논리적 쓰기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**total_logical_reads**|**bigint**|이 저장 프로시저가 컴파일된 이후 실행될 때 수행된 총 논리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**last_logical_reads**|**bigint**|이 저장 프로시저가 마지막으로 실행될 때 수행된 논리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**min_logical_reads**|**bigint**|단일 실행 중 이 저장 프로시저가 수행한 최소 논리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**max_logical_reads**|**bigint**|단일 실행 중 이 저장 프로시저가 수행한 최대 논리적 읽기 수입니다.<br /><br /> 메모리 최적화 테이블을 쿼리하는 경우 항상 0입니다.|  
|**total_elapsed_time**|**bigint**|이 저장 프로시저의 실행을 완료하는 데 소요된 총 경과 시간(마이크로초)입니다.|  
|**last_elapsed_time**|**bigint**|가장 최근에 이 저장 프로시저의 실행을 완료하는 데 소요된 경과 시간(마이크로초)입니다.|  
|**min_elapsed_time**|**bigint**|이 저장 프로시저의 실행을 완료하는 데 소요된 최소 경과 시간(마이크로초)입니다.|  
|**max_elapsed_time**|**bigint**|이 저장 프로시저의 실행을 완료하는 데 소요된 최대 경과 시간(마이크로초)입니다.|  
|**pdw_node_id**|**int**|**적용 대상**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 이 배포에 있는 노드에 대 한 식별자입니다.|  
  
 <sup>1</sup> 고유 하 게 컴파일된 저장된 프로시저에 대 한 통계 컬렉션을 설정 하면 작업자 시간이 밀리초 단위로 수집 합니다. 쿼리가 밀리초 미만 단위로 실행되는 경우 값은 0이 됩니다.  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요 `VIEW SERVER STATE` 권한.   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 프리미엄 계층 필요는 `VIEW DATABASE STATE` 데이터베이스에는 권한이 있습니다. [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] 표준 및 기본 계층 필요는 **서버 관리자** 또는 **Azure Active Directory 관리자** 계정. 
  
## <a name="remarks"></a>주의  
 저장 프로시저의 실행이 완료되면 뷰에 있는 통계가 업데이트됩니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 평균 경과 시간으로 식별된 상위 10개의 저장 프로시저에 대한 정보를 반환합니다.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>관련 항목:  
 [실행 관련 동적 관리 뷰 및 함수 &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
  

