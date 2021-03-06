---
title: sp_depends (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_depends
- sp_depends_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_depends
ms.assetid: d9934590-c6ae-4936-91c3-146055ef2c57
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f20945b6c4dc8fc1dda398c3dc9e721ff8b44d07
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724641"
---
# <a name="spdepends-transact-sql"></a>sp_depends(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  테이블 또는 뷰에 종속되는 뷰 및 프로시저, 뷰 또는 프로시저에 종속되는 테이블 및 뷰와 같은 데이터베이스 개체 종속성에 대한 정보를 표시합니다. 현재 데이터베이스 외부의 개체에 대한 참조는 보고되지 않습니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 사용 하 여 [sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md) 하 고 [sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) 대신 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_depends [ @objname = ] '<object>'   
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name.  
    object_name  
}  
```  
  
## <a name="arguments"></a>인수  
 *database_name*  
 데이터베이스의 이름입니다.  
  
 *schema_name*  
 개체가 속한 스키마의 이름입니다.  
  
 *object_name*  
 종속성을 검사할 데이터베이스 개체입니다. 개체는 테이블, 뷰, 저장 프로시저, 사용자 정의 함수 또는 트리거일 수 있습니다. o*bject_name* 됩니다 **nvarchar(776)**, 기본값은 없습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
 **sp_depends** 두 개의 결과 집합이 표시 됩니다.  
  
 다음 결과 집합에 있는 개체를 보여 줍니다  *\<개체 >* 달라 집니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|종속성이 있는 항목의 이름입니다.|  
|**type**|**nvarchar(16)**|항목의 유형입니다.|  
|**업데이트**|**nvarchar(7)**|항목의 업데이트 여부를 결정합니다.|  
|**선택**|**nvarchar(8)**|SELECT 문에서 항목의 사용 여부를 결정합니다.|  
|**column**|**sysname**|종속성이 있는 열 또는 매개 변수입니다.|  
  
 다음 결과 집합에 종속 된 개체를 보여 줍니다  *\<개체 >* 합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|종속성이 있는 항목의 이름입니다.|  
|**type**|**nvarchar(16)**|항목의 유형입니다.|  
  
## <a name="permissions"></a>사용 권한  
 **public** 역할의 멤버 자격이 필요합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-listing-dependencies-on-a-table"></a>1. 테이블에 대한 종속성 나열  
 다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 `Sales.Customer` 테이블에 종속된 데이터베이스 개체를 나열합니다. 스키마 이름 및 테이블 이름 모두를 지정합니다.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_depends @objname = N'Sales.Customer' ;  
```  
  
### <a name="b-listing-dependencies-on-a-trigger"></a>2. 트리거에 대한 종속성 나열  
 다음 예에서는 `iWorkOrder` 트리거가 종속된 데이터베이스 개체를 나열합니다.  
  
```  
EXEC sp_depends @objname = N'AdventureWorks2012.Production.iWorkOrder' ;  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 엔진 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [EXECUTE&#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [sp_help&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sql_dependencies &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
