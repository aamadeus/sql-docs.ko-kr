---
title: DROP SYNONYM(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b4704b1fdb9181e8abd9f800da7c57a7973d2090
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701241"
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  지정한 스키마에서 동의어를 제거합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>인수  
 *IF EXISTS*  
**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ~ [현재 버전](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 이미 있는 경우에만 동의어를 조건부로 삭제합니다.  
  
 *schema*  
 동의어가 존재하는 스키마를 지정합니다. 스키마를 지정하지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 현재 사용자의 기본 스키마를 사용합니다.  
  
 *synonym_name*  
 삭제할 동의어의 이름입니다.  
  
## <a name="remarks"></a>Remarks  
 동의어에 대한 참조는 스키마 바운드가 아니므로 언제든 동의어를 삭제할 수 있습니다. 삭제한 동의어에 대한 참조는 런타임에만 발견할 수 있습니다.  
  
 동의어는 동적 SQL에서 생성, 삭제 및 참조할 수 있습니다.  
  
## <a name="permissions"></a>Permissions  
 동의어를 삭제하려면 사용자가 적어도 다음 조건 중 하나를 충족시켜야 합니다.  
  
-   동의어의 현재 사용자  
  
-   동의어에 대한 CONTROL을 보유하는 피부여자  
  
-   포함하는 스키마에 대한 ALTER SCHEMA 권한을 보유하는 피부여자  
  
## <a name="examples"></a>예  
 다음 예에서는 우선 동의어인 `MyProduct`를 만든 다음 그 동의어를 삭제하는 방법을 보여 줍니다.  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA&#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
