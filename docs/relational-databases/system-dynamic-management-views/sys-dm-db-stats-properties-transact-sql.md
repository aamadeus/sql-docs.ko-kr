---
title: sys.dm_db_stats_properties (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_db_stats_properties_TSQL
- sys.dm_db_stats_properties
- dm_db_stats_properties_TSQL
- dm_db_stats_properties
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_stats_properties
ms.assetid: 8a54889d-e263-4881-9fcb-b1db410a9453
caps.latest.revision: "13"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e2a1ebc3301372b490de9ec631c3cdb0743f264b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbstatsproperties-transact-sql"></a>sys.dm_db_stats_properties(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 지정한 데이터베이스 개체(테이블 또는 인덱싱된 뷰)에 대한 통계 속성을 반환합니다. 분할 된 테이블에 대 한 참조는 비슷한 [sys.dm_db_incremental_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)합니다. 
 
## <a name="syntax"></a>구문  
  
```  
sys.dm_db_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>인수  
 *object_id*  
 해당 통계 중 하나의 속성이 요청되는 현재 데이터베이스에 포함된 개체의 ID입니다. *object_id* 는 **int**입니다.  
  
 *stats_id*  
 지정된 *object_id*통계의 ID입니다. 통계 ID는 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) 동적 관리 뷰에서 얻을 수 있습니다. *stats_id* 는 **int**입니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|통계 개체의 속성을 반환하는 개체(테이블 또는 인덱싱된 뷰)의 ID입니다.|  
|stats_id|**int**|통계 개체의 ID입니다. 테이블 또는 인덱싱된 뷰 내에서 고유합니다. 자세한 내용은 [sys.stats&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)를 참조하세요.|  
|last_updated|**datetime2**|통계 개체가 마지막으로 업데이트된 날짜와 시간입니다.|  
|rows|**bigint**|통계가 마지막으로 업데이트되었을 때 테이블 또는 인덱싱된 뷰의 전체 행 수입니다. 통계가 필터링되거나 필터링된 인덱스에 해당하는 경우 행 수가 테이블의 행 수보다 적을 수 있습니다.|  
|rows_sampled|**bigint**|통계 계산을 위해 샘플링된 전체 행 수입니다.|  
|단계|**int**|히스토그램의 총 단계 수입니다. 자세한 내용은 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)의 RTM 버전에는 이 보기가 포함되지 않습니다.|  
|unfiltered_rows|**bigint**|필터링된 통계의 필터 식을 적용하기 전 테이블의 전체 행 수입니다. 통계가 필터링되지 않으면 unfiltered_rows는 행 열에서 반환된 값과 동일합니다.|  
|modification_counter|**bigint**|통계를 마지막으로 업데이트한 이후 선행 통계 열(히스토그램이 작성된 열)의 총 수정 개수입니다.<br /><br /> 메모리 액세스에 최적화 된 테이블: 시작 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 및 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 이 열에 포함: 통계가 마지막으로 업데이트 된 되거나 데이터베이스를 다시 시작한 이후 테이블에 대 한 수정 작업의 총 수입니다.|  
|persisted_sample_percent|**float**|샘플링 비율을 명시적으로 지정 하지 않는 통계 업데이트에 사용 되는 샘플 비율을 유지 합니다. 값이 0 이면 없음 지속형된 샘플 비율이이 통계에 대해 설정 됩니다.<br /><br /> **적용 대상:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4|  
  
## <a name="remarks"></a>주의  
 **sys.dm_db_stats_properties** 다음 조건에서 빈 행 집합을 반환 합니다.  
  
-   **object_id** 또는 **stats_id** 은 NULL입니다.  
  
-   지정한 개체를 찾을 수 없거나 지정한 개체가 테이블 또는 인덱싱된 뷰에 해당되지 않습니다.  
  
-   지정한 통계 ID가 특정 개체 ID의 기존 통계에 해당되지 않습니다.  
  
-   현재 사용자에게 통계 개체를 볼 수 있는 권한이 없습니다.  
  
 이 동작을 통해 안전 하 게 **sys.dm_db_stats_properties** 교차 적용 될 때 뷰의 행에에서 같은 **sys.objects** 및 **sys.stats**합니다.  
  
## <a name="permissions"></a>Permissions  
 사용자가 통계 열에 대한 select 권한이 있거나 테이블을 소유하거나 `sysadmin` 고정 서버 역할, `db_owner` 고정 데이터베이스 역할, 또는 `db_ddladmin` 고정 데이터베이스 역할의 멤버여야 합니다.  
  
## <a name="examples"></a>예  

### <a name="a-simple-example"></a>1. 간단한 예
에 대 한 통계를 반환 하는 다음 예제는 `Person.Person` AdventureWorks 데이터베이스의 테이블입니다.

```
SELECT * FROM sys.dm_db_stats_properties (object_id('Person.Person'), 1);
``` 
  
### <a name="b-returning-all-statistics-properties-for-a-table"></a>2. 테이블의 모든 통계 속성 반환  
 다음 예에서는 테이블 TEST에 있는 모든 통계의 속성을 반환합니다.  
  
```  
SELECT sp.stats_id, name, filter_definition, last_updated, rows, rows_sampled, steps, unfiltered_rows, modification_counter   
FROM sys.stats AS stat   
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE stat.object_id = object_id('TEST');  
```  
  
### <a name="c-returning-statistics-properties-for-frequently-modified-objects"></a>3. 빈번하게 수정되는 개체의 통계 속성 반환  
 다음 예는 마지막 통계 업데이트 이후 1000번 넘게 수정된 선행 열에 대한 현재 데이터베이스의 모든 테이블, 인덱싱된 뷰 및 통계를 반환합니다.  
  
```  
SELECT obj.name, obj.object_id, stat.name, stat.stats_id, last_updated, modification_counter  
FROM sys.objects AS obj   
INNER JOIN sys.stats AS stat ON stat.object_id = obj.object_id  
CROSS APPLY sys.dm_db_stats_properties(stat.object_id, stat.stats_id) AS sp  
WHERE modification_counter > 1000;  
```  
  
## <a name="see-also"></a>관련 항목:  
 [DBCC SHOW_STATISTICS&#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [개체 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
 [sys.dm_db_incremental_stats_properties (Transact SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-incremental-stats-properties-transact-sql.md)  
 [sys.dm_db_stats_histogram (Transact SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  
