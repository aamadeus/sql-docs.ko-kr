---
title: sys.column_store_segments (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 12/30/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a23388dd2333694f779b9f78de81dd9659916b49
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Columnstore 인덱스의 각 열 세그먼트에 대해 한 행을 반환합니다. 행 그룹당 최대 열당 하나의 열 세그먼트가 있습니다. 예를 들어 10 개의 rowgroup 및 34 열이 있는 테이블 340 행을 반환합니다. 
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|파티션 ID를 나타냅니다. 데이터베이스 내에서 고유합니다.|  
|**hobt_id**|**bigint**|이 Columnstore 인덱스를 가진 테이블의 B-트리 인덱스(hobt) 또는 힙의 ID입니다.|  
|**column_id**|**int**|Columnstore 열의 ID입니다.|  
|**segment_id**|**int**|행 그룹의 ID입니다. 이전 버전과 호환성에 대 한 열 이름을 계속 행 그룹 ID입니다. 있더라도 segment_id를 호출할 수 사용 하 여 세그먼트를 고유 하 게 식별할 수 있습니다 \<hobt_id, partition_id, column_id >, < segment_id > 합니다.|  
|**version**|**int**|열 세그먼트 형식의 버전입니다.|  
|**encoding_type**|**int**|해당 세그먼트에 대해 사용 되는 인코딩 유형:<br /><br /> 1 = VALUE_BASED-문자열/이진이 아님으로 사용 가능한 사전 (매우 비슷합니다 일부 내부 변형이 4)<br /><br /> 2 = VALUE_HASH_BASED-사전에 공통 값과 문자열/이진이 아닌 열<br /><br /> 3 = STRING_HASH_BASED-사전에 공통 값과 문자열/이진 열<br /><br /> 4 = STORE_BY_VALUE_BASED-문자열/이진이 아님으로 없는 사전 사용 하 여<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED-문자열/이항 없는 사전 사용 하 여<br /><br /> 모든 인코딩을 활용 가능한 경우 비트 압축 및 실행 길이 인코딩.|  
|**row_count**|**int**|행 그룹의 행 수입니다.|  
|**has_nulls**|**int**|열 세그먼트에 Null 값이 있으면 1입니다.|  
|**않으면 base_id**|**bigint**|인코딩 유형 1 기준 값 id는 사용 중입니다.  인코딩 유형 1은 사용 되지 않으면 base_id가 1로 설정 됩니다.|  
|**크기**|**float**|인코딩 유형 1 경우 magnitude는 사용 중입니다.  인코딩 유형 1은 사용 되지 크기가 1로 설정 됩니다.|  
|**primary_dictionary_id**|**int**|값이 0에는 전역 사전을 나타냅니다. -1 값이이 열에 대해 만든 글로벌 사전이 없습니다 임을 나타냅니다.|  
|**secondary_dictionary_id**|**int**|0이 아닌 값이이 열에 현재 세그먼트 (즉, 행)에 대 한 로컬 사전을를 가리킵니다. -1 값이이 세그먼트에 대 한 사전이 없습니다 로컬 임을 나타냅니다.|  
|**min_data_id**|**bigint**|열 세그먼트의 최소 데이터 ID입니다.|  
|**max_data_id**|**bigint**|열 세그먼트의 최대 데이터 ID입니다.|  
|**반환**|**bigint**|Null을 나타내는 데 사용되는 값입니다.|  
|**on_disk_size**|**bigint**|세그먼트의 크기(바이트)입니다.|  
  
## <a name="remarks"></a>주의  
 다음 쿼리는 columnstore 인덱스의 세그먼트에 대한 정보를 반환합니다.  
  
```tsql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 모든 열에 필요 이상 **VIEW DEFINITION** 테이블에 대 한 합니다. 해당 사용자에 게 하지 않는 한 다음과 같은 열은 null을 반환 **선택** 권한: has_nulls, 않으면 base_id, 크기, min_data_id, max_data_id, 및 반환 합니다.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목:  
 [개체 카탈로그 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server 시스템 카탈로그 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Columnstore 인덱스 가이드](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  
