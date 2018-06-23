---
title: 테이블 별칭으로 ORDER BY 절의 열 별칭을 붙일 수 없습니다 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aliases [SQL Server], columns
ms.assetid: fee7328f-6e8d-4005-930b-56fb6f17e0b2
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 18c65604efb2d1b0ff93d09b8d03f7ee6cb213cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36089894"
---
# <a name="column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias"></a>ORDER BY 절의 열 별칭에 접두사로 테이블 별칭을 붙일 수 없습니다.
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서는 ORDER BY 절의 열 별칭에 접두사로 테이블 별칭을 붙일 수 없습니다.  
  
## <a name="component"></a>구성 요소  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 예를 들어 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 다음 쿼리가 실행되지만 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서는 오류가 반환됩니다.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.l  
```  
  
 [!INCLUDE[ssDEversion10](../../includes/ssdeversion10-md.md)]은 `p.l` 절의 `ORDER BY`을 테이블의 유효한 열에 일치시키지 않습니다.  
  
### <a name="exception"></a>예외  
 ORDER BY 절에 지정되어 있으며 접두사가 있는 열 별칭이 지정된 테이블의 유효한 열 이름이면 쿼리가 오류 없이 실행됩니다. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 문의 의미 체계가 다를 수 있습니다. 예를 들어 다음 문에 지정된 열 별칭(`id`)은 `sysobjects` 테이블의 유효한 열 이름입니다. [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]에서는 문을 실행하면 결과 집합이 정렬된 후에 `CAST` 작업이 수행됩니다. 즉, `name` 열이 정렬 작업에 사용됩니다. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서는 `CAST` 작업이 정렬 작업보다 먼저 발생합니다. 즉, 테이블의 `id` 열이 정렬 작업에 사용되고 결과 집합을 예기치 않은 순서로 반환합니다.  
  
```  
SELECT CAST (o.name AS char(128)) AS id  
FROM sysobjects AS o  
ORDER BY o.id;  
```  
  
## <a name="corrective-action"></a>수정 동작  
 다음 방법 중 하나로 ORDER BY 절의 테이블 별칭이 접두사로 지정된 열 별칭을 사용하는 쿼리를 수정합니다.  
  
-   가능하면 ORDER BY 절의 열 별칭에 접두사를 지정하지 않습니다.  
  
-   열 별칭을 열 이름으로 대체합니다.  
  
 예를 들어 다음 두 쿼리는 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 오류 없이 실행됩니다.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY l  
  
USE AdventureWorks2012;  
GO  
SELECT FirstName AS f, LastName AS l  
FROM Person.Contact p  
ORDER BY p.LastName  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 엔진 업그레이드 문제](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 업그레이드 관리자 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  