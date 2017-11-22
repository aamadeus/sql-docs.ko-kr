---
title: sys.dm_db_incremental_stats_properties (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server 2014
f1_keywords:
- sys.dm_db_incremental_stats_properties
- sys.dm_db_incremental_stats_properties_TSQL
- dm_db_incremental_stats_properties
- dm_db_incremental_stats_properties_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_incremental_stats_properties
ms.assetid: aa0db893-34d1-419c-b008-224852e71307
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ce7ab395a01f3b1ab6d35edb3c260f1f4338044e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbincrementalstatsproperties-transact-sql"></a>sys.dm_db_incremental_stats_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 지정한 데이터베이스 개체(테이블)에 대한 증분 통계 속성을 반환합니다. `sys.dm_db_incremental_stats_properties` 사용은(파티션 번호 포함) 비증분 통계에 사용되는 `sys.dm_db_stats_properties` 와 비슷합니다. 
  
  이 함수에 도입 된 [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)] 서비스 팩 2 및 [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] 서비스 팩 1입니다.
  
 
## <a name="syntax"></a>구문  
  
```  
sys.dm_db_incremental_stats_properties (object_id, stats_id)  
```  
  
## <a name="arguments"></a>인수  
 *object_id*  
 증분 통계 중 하나의 속성이 요청되는 현재 데이터베이스에 포함된 개체의 ID입니다. *object_id* 는 **int**입니다.  
  
 *stats_id*  
 지정된 *object_id*통계의 ID입니다. 통계 ID는 [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) 동적 관리 뷰에서 얻을 수 있습니다. *stats_id* 는 **int**입니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|통계 개체의 속성을 반환하는 개체(테이블)의 ID입니다.|  
|stats_id|**int**|통계 개체의 ID입니다. 테이블 내에서 고유합니다. 자세한 내용은 [sys의 RTM 버전에는 이 보기가 포함되지 않습니다.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)의 RTM 버전에는 이 보기가 포함되지 않습니다.|
|partition_number|**int**|테이블의 일부를 포함하는 파티션 수입니다.|  
|last_updated|**datetime2**|통계 개체가 마지막으로 업데이트된 날짜와 시간입니다.|  
|rows|**bigint**|통계가 마지막으로 업데이트되었을 때 테이블의 전체 행 수입니다. 통계가 필터링되거나 필터링된 인덱스에 해당하는 경우 행 수가 테이블의 행 수보다 적을 수 있습니다.|  
|rows_sampled|**bigint**|통계 계산을 위해 샘플링된 전체 행 수입니다.|  
|단계|**int**|히스토그램의 총 단계 수입니다. 자세한 내용은 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)의 RTM 버전에는 이 보기가 포함되지 않습니다.|  
|unfiltered_rows|**bigint**|필터링된 통계의 필터 식을 적용하기 전 테이블의 전체 행 수입니다. 통계가 필터링되지 않으면 unfiltered_rows는 행 열에서 반환된 값과 동일합니다.|  
|modification_counter|**bigint**|통계를 마지막으로 업데이트한 이후 선행 통계 열(히스토그램이 작성된 열)의 총 수정 개수입니다.<br /><br /> 이 열은 메모리 최적화 테이블에 대한 정보를 포함하지 않습니다.|  
  
## <a name="remarks"></a>주의  
 `sys.dm_db_incremental_stats_properties`는 다음과 같은 경우 빈 행 집합을 반환합니다.  
  
-   `object_id` 또는 `stats_id`가 NULL입니다.   
-   지정한 개체를 찾을 수 없거나 지정한 개체가 증분 통계를 사용하는 테이블에 해당되지 않습니다.  
-   지정한 통계 ID가 특정 개체 ID의 기존 통계에 해당되지 않습니다.  
-   현재 사용자에게 통계 개체를 볼 수 있는 권한이 없습니다.

 
 이 동작은 `sys.dm_db_incremental_stats_properties` 및 `sys.objects` 와 같은 뷰의 행에 교차 적용될 때 `sys.stats`를 안전하게 사용할 수 있습니다. 이 메서드는 각 파티션에 해당하는 통계에 대한 속성을 반환할 수 있습니다. 모든 파티션에서 결합되어 병합된 통계에 대한 속성을 보려면 sys.dm_db_stats_properties를 대신 사용합니다. 
  
## <a name="permissions"></a>Permissions  
 사용자가 통계 열에 대한 select 권한이 있거나 테이블을 소유하거나 `sysadmin` 고정 서버 역할, `db_owner` 고정 데이터베이스 역할, 또는 `db_ddladmin` 고정 데이터베이스 역할의 멤버여야 합니다.  
  
## <a name="examples"></a>예  

### <a name="a-simple-example"></a>1. 간단한 예
다음 예제에서는 `PartitionTable` 분할된 테이블 및 인덱스 만들기 [항목에서 설명하는](../../relational-databases/partitions/create-partitioned-tables-and-indexes.md)테이블에 대한 통계를 반환합니다.

```
SELECT * FROM sys.dm_db_incremental_stats_properties (object_id('PartitionTable'), 1);
``` 

추가 사용 제안 방법은  [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)를 참조하세요.
  
  
## <a name="see-also"></a>관련 항목:  
 [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [DBCC SHOW_STATISTICS&#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sys.stats&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [개체 관련 동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)   
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
