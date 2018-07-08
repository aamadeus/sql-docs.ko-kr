---
title: 행 수준 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- row level security described
- row level security
- access control predicates
- security [SQL Server], predicate based access control
- predicate based security
ms.assetid: 7221fa4e-ca4a-4d5c-9f93-1b8a4af7b9e8
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 61e4d5339822a134981f7fd9708de6791d4549ca
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36184664"
---
# <a name="row-level-security"></a>행 수준 보안
  행 수준 보안(RLS)을 통해 고객은 쿼리(예: 그룹 멤버십 또는 실행 컨텍스트)를 실행하는 사용자의 특징을 기반으로 데이터베이스 테이블의 행에 대한 액세스를 제어할 수 있습니다. 행 수준 보안은 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 합니다. 이 기능에 대한 최신 설명을 보려면 최신 설명서에서 [행 수준 보안](https://msdn.microsoft.com/library/dn765131.aspx) 을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [CREATE SECURITY POLICY &#40;Azure SQL 데이터베이스&#41;](/sql/t-sql/statements/create-security-policy-transact-sql)   
 [ALTER 보안 정책 &#40;Azure SQL 데이터베이스&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql)   
 [DROP 보안 정책 &#40;Azure SQL 데이터베이스&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql)   
 [CREATE FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)   
 [sys.security_policies &#40;Azure SQL 데이터베이스&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql)   
 [sys.security_predicates &#40;Azure SQL 데이터베이스&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql)   
 [사용자 정의 함수 만들기&#40;데이터베이스 엔진&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md)  
  
  