---
title: sys.system_columns (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- system_columns_TSQL
- system_columns
- sys.system_columns
- sys.system_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.system_columns catalog view
ms.assetid: 4ab1d48a-d57a-4e76-a08c-9627eeaf4588
caps.latest.revision: "46"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f8a710e9575af43cbbe8bfdcaf7d66f09ca26d41
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="syssystemcolumns-transact-sql"></a>sys.system_columns(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  열이 있는 시스템 개체의 각 열당 한 개의 행을 포함합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|이 열이 속한 개체의 ID입니다.|  
|**name**|**sysname**|열의 이름입니다. 개체 내에서 고유합니다.|  
|**column_id**|**int**|열의 ID입니다. 개체 내에서 고유합니다.<br /><br /> 열 ID는 순차적이지 않을 수 있습니다.|  
|**system_type_id**|**tinyint**|열의 시스템 유형 ID입니다.|  
|**user_type_id**|**int**|열의 유형에 대한 사용자 정의 ID입니다.<br /><br /> 형식의 이름을 반환 하려면에 가입는 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) 카탈로그 뷰에서이 열에 있습니다.|  
|**max_length**|**smallint**|열의 최대 길이(바이트)입니다.<br /><br /> -1 = 열 데이터 형식이 **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, 또는 **xml**합니다.<br /><br /> 에 대 한 **텍스트** 열은 **max_length** 값은 16 또는 값 설정 됩니다 **sp_tableoption** 'text in row'.|  
|**전체 자릿수**|**tinyint**|숫자 기반일 경우에는 열의 전체 자릿수이고, 그렇지 않으면 0입니다.|  
|**크기 조정**|**tinyint**|숫자 기반일 경우에는 열의 소수 자릿수이고, 그렇지 않으면 0입니다.|  
|**데이터 정렬 이름**|**sysname**|문자 기반일 경우에는 열의 데이터 정렬 이름이고, 그렇지 않으면 NULL입니다.|  
|**is_nullable**|**bit**|1 = 열이 Null 값을 허용합니다.|  
|**is_ansi_padded**|**bit**|1 = 열이 문자, 이진 또는 variant인 경우 ANSI_PADDING ON 동작을 사용합니다.<br /><br /> 0 = 열이 문자, 이진 또는 variant가 아닙니다.|  
|**is_rowguidcol**|**bit**|1 = 선언된 ROWGUIDCOL 열입니다.|  
|**is_identity**|**bit**|1 = 열에 ID 값이 있습니다.|  
|**is_computed**|**bit**|1 = 열이 계산 열입니다.|  
|**is_filestream**|**bit**|1 = 파일 스트림 저장소를 사용하도록 선언된 열입니다.|  
|**is_replicated**|**bit**|1 = 복제된 열입니다.|  
|**is_non_sql_subscribed**|**bit**|1 = 열에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자가 있습니다.|  
|**is_merge_published**|**bit**|1 = 병합 게시 열입니다.|  
|**is_dts_replicated**|**bit**|1 = [!INCLUDE[ssIS](../../includes/ssis-md.md)]를 사용해 복제된 열입니다.|  
|**is_xml_document**|**bit**|1 = 내용이 완전한 XML 문서입니다.<br /><br /> 0 = 내용이 문서 조각 이거나 열 데이터 형식이 않습니다 **xml**합니다.|  
|**xml_collection_id**|**int**|0이 아닌 열 데이터 형식이 **xml** XML이 입력 하 고 있습니다. 이 값은 열의 유효성 검사 XML 스키마 네임스페이스가 들어 있는 컬렉션의 ID가 됩니다.<br /><br /> 0 = XML 스키마 컬렉션이 없습니다.|  
|**default_object_id**|**int**|독립 실행형 인지에 관계 없이 기본 개체의 ID [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md), 또는 인라인 열 수준 DEFAULT 제약 조건입니다. **parent_object_id** 인라인 열 수준 기본 개체의 열은 테이블 자체에 다시 참조 합니다. 또는 기본값이 없을 경우 0입니다.|  
|**rule_object_id**|**int**|독립 실행형 규칙의 ID를 사용 하 여 열에 바인딩된 **sys.sp_bindrule**합니다.<br /><br /> 0 = 독립 실행형 규칙이 없습니다.<br /><br /> 열 수준 CHECK 제약 조건에 대 한 참조 [sys.check_constraints &#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**bit**|1 = 열이 스파스 열입니다. 자세한 내용은 [스파스 열 사용](../../relational-databases/tables/use-sparse-columns.md)을 참조하세요.|  
|is_column_set|**bit**|1 = 열이 열 집합입니다. 자세한 내용은 [열 집합 사용](../../relational-databases/tables/use-column-sets.md)을 참조하세요.|  
|generated_always_type|**tinyint**|열의 유형을 나타내는 숫자 값입니다.<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar (60)**|열의 유형의 텍스트 설명:<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **적용 대상**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목:  
 [개체 카탈로그 뷰 &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server 시스템 카탈로그 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  