---
title: '@@VERSION (Transact SQL) | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b8367bb24a37996b2956e3107113812a32086fed
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="version---transact-sql-configuration-functions"></a>버전-Transact SQL 구성 함수
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 현재 설치에 대한 시스템 및 빌드 정보를 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@VERSION  
```  
  
## <a name="return-types"></a>반환 형식  
 **nvarchar**  
  
## <a name="remarks"></a>주의  
 @@VERSION 결과 하나의 nvarchar 문자열로 표시 됩니다. 사용할 수는 [SERVERPROPERTY &#40; Transact SQL &#41; ](../../t-sql/functions/serverproperty-transact-sql.md) 개별 속성 값을 검색 하는 함수입니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 경우 다음 정보가 반환됩니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전  
  
-   프로세서 아키텍처  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 빌드 날짜  
  
-   저작권 공지  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전  
  
-   운영 체제 버전  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]의 경우 다음 정보가 반환됩니다.  
  
-   에디션- "Microsoft Azure SQL Database"  
  
-   제품 수준 - "(CTP)" 또는 "(RTM)"  
  
-   제품 버전  
  
-   빌드 날짜  
  
-   저작권 공지  
  
## <a name="examples"></a>예  
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>A: 현재 버전의 반환[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 다음 예에서는 현재 설치의 버전 정보를 반환합니다.  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>예: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 및[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>2. 현재 버전을 반환 합니다.[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>관련 항목:  
 [SERVERPROPERTY&#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

