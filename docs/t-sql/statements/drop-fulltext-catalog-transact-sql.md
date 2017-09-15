---
title: DROP FULLTEXT CATALOG (Transact SQL) | Microsoft Docs
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
- DROP_FULLTEXT_CATALOG_TSQL
- DROP FULLTEXT CATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- dropping full-text catalogs
- removing full-text catalogs
- full-text catalogs [SQL Server], removing
- deleting full-text catalogs
- DROP FULLTEXT CATALOG statement
ms.assetid: b54efb0b-400b-49ce-923b-ce20a2a12255
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 32445ba8410673168ffe8e7da61cdd1b37d71afe
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-fulltext-catalog-transact-sql"></a>DROP FULLTEXT CATALOG(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  데이터베이스에서 전체 텍스트 카탈로그를 제거합니다. 카탈로그를 삭제하기 전에 카탈로그와 연관된 모든 전체 텍스트 인덱스를 삭제해야 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
DROP FULLTEXT CATALOG catalog_name  
```  
  
## <a name="arguments"></a>인수  
 *catalog_name*  
 제거할 카탈로그의 이름입니다. 경우 *catalog_name* 존재 하지 않는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 오류를 반환 하 고 DROP 작업을 수행 하지 않습니다. 명령을 제대로 수행하려면 전체 텍스트 카탈로그의 파일 그룹에 OFFLINE 또는 READONLY가 표시되지 않아야 합니다.  
  
## <a name="permissions"></a>Permissions  
 사용자는 전체 텍스트 카탈로그에 대해 DROP 권한이 있거나의 멤버는 **db_owner**, 또는 **db_ddladmin** 고정 데이터베이스 역할입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [sys.fulltext_catalogs &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [ALTER FULLTEXT CATALOG&#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [전체 텍스트 카탈로그 &#40; 만들기 Transact SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [전체 텍스트 검색](../../relational-databases/search/full-text-search.md)  
  
  