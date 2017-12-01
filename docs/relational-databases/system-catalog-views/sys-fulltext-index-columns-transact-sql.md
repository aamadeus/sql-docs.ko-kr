---
title: sys.fulltext_index_columns (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fulltext_index_columns
- fulltext_index_columns
- sys.fulltext_index_columns_TSQL
- fulltext_index_columns_TSQL
dev_langs: TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], columns
- sys.fulltext_index_columns catalog view
- full-text indexes [SQL Server], properties
ms.assetid: c34b8625-e53c-4281-ace6-d46230d5cb84
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea0b235c347f9d06f0ea87462c62e5d02629ccd7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysfulltextindexcolumns-transact-sql"></a>sys.fulltext_index_columns(Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  전체 텍스트 인덱스의 일부인 각 열에 대한 행을 포함합니다.    
 
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|이 열이 속한 개체의 ID입니다.|  
|**column_id**|**int**|전체 텍스트 인덱스의 일부인 열의 ID입니다.|  
|**type_column_id**|**int**|지정된 행의 문서에 대한 사용자 제공 문서 파일 확장명("doc", "xls" 등)을 저장하는 유형 열의 ID입니다. 유형 열은 전체 텍스트 인덱싱 중에 해당 데이터를 필터링해야 하는 열에 대해서만 지정됩니다. 적용되지 않는 경우 NULL입니다. 자세한 내용은 [고급 분석 확장 구성 및 관리](../../relational-databases/search/configure-and-manage-filters-for-search.md)를 참조하세요.|  
|**language_id**|**int**|단어 분리기에서 이 전체 텍스트 열을 인덱싱하는 데 사용하는 언어의 LCID입니다.<br /><br /> 0 = 중립입니다.<br /><br /> 자세한 내용은 참조 [sys.fulltext_languages&#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).|  
|**statistical_semantics**|**int**|1 = 이 열에 전체 텍스트 인덱싱 외에도 통계 의미 체계를 사용하도록 설정되어 있습니다.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>관련 항목:  
 [개체 카탈로그 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  