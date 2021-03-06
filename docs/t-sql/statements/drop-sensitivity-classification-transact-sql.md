---
title: DROP SENSITIVITY CLASSIFICATION(Transact-SQL) | Microsoft Docs
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- DROP SENSITIVITY CLASSIFICATION
- DROP_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SENSITIVITY CLASSIFICATION statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 075615be9adac78aa59e6dfad1934fc4d7993bf3
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52392988"
---
# <a name="drop-sensitivity-classification-transact-sql"></a>DROP SENSITIVITY CLASSIFICATION(Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

하나 이상의 데이터베이스 열에서 민감도 분류 메타데이터를 삭제합니다.

## <a name="syntax"></a>구문

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    <object_name> [, ...n ]

<object_name> ::=
{
    [schema_name.]table_name.column_name
}
```  

## <a name="arguments"></a>인수  

*object_name*([schema_name.]table_name.column_name)

분류를 제거할 데이터베이스 열의 이름입니다. 현재는 열 분류만 지원됩니다.
    - *schema_name*(선택 사항) - 분류된 열이 속한 스키마의 이름입니다.
    - *table_name* - 분류된 열이 속한 테이블의 이름입니다.
    - *column_name* - 분류를 삭제할 열의 이름입니다.

## <a name="remarks"></a>Remarks  

- 여러 개체 분류는 단일 'DROP SENSITIVITY CLASSIFICATION' 문을 사용하여 삭제할 수 있습니다.

## <a name="permissions"></a>Permissions  

ALTER ANY SENSITIVITY CLASSIFICATION 권한이 필요합니다. ALTER ANY SENSITIVITY CLASSIFACTION은 데이터베이스 권한 ALTER 또는 서버 권한 CONTROL SERVER에 포함됩니다.


## <a name="examples"></a>예  


### <a name="a-dropping-classification-from-a-single-column"></a>1. 단일 열에서 분류 삭제

다음 예제에서는 `dbo.sales.price` 열에서 분류를 제거합니다.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price
```

### <a name="b-dropping-classification-from-multiple-columns"></a>2. 여러 열에서 분류 삭제

다음 예제에서는 `dbo.sales.price`, `dbo.sales.discount` 및 `SalesLT.Customer.Phone` 열에서 분류를 제거합니다.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price, dbo.sales.discount, SalesLT.Customer.Phone  
```

## <a name="see-also"></a>참고 항목  

[ADD SENSITIVITY CLASSIFICATION(Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications(Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[SQL Information Protection 시작](https://aka.ms/sqlip)
