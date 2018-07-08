---
title: 테이블의 종속성 보기 | Microsoft 문서
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
- table dependencies [SQL Server]
- dependencies [SQL Server], tables
- displaying dependences
- viewing dependencies
ms.assetid: c4351ef5-e7d0-46e7-8367-88695e9974f8
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ecccfad7179d7b043939515b12453ed3d9cc566f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082221"
---
# <a name="view-the-dependencies-of-a-table"></a>테이블의 종속성 보기
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 테이블 종속성을 볼 수 있습니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **테이블의 종속성을 보려면**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 데이터베이스에 대한 VIEW DEFINITION 권한과 데이터베이스의 sys.sql_expression_dependencies에 대한 SELECT 권한이 필요합니다. 기본적으로 SELECT 권한은 db_owner 고정 데이터베이스 역할의 멤버에게만 부여됩니다. SELECT와 VIEW DEFINITION 권한을 다른 사용자에게 부여하면 피부여자는 데이터베이스의 모든 종속성을 볼 수 있습니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-view-the-dependencies-of-a-table"></a>테이블의 종속성을 보려면  
  
1.  **개체 탐색기**에서 **데이터베이스**를 확장하고, 특정 데이터베이스를 확장한 후 **테이블**을 확장합니다.  
  
2.  테이블을 마우스 오른쪽 단추로 클릭한 다음 **종속성 보기**를 클릭합니다.  
  
3.  **개체 종속성***\<개체 이름>* 대화 상자에서 *\<개체 이름>* **에 종속된 개체** 또는  *****\<개체 이름>*** 이 종속된 개체**를 선택합니다.  
  
4.  **종속성** 표에서 개체를 선택합니다. 개체 유형(예: "트리거" 또는 "저장 프로시저")이 **유형** 상자에 표시됩니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-view-the-objects-that-depend-on-a-table"></a>테이블에 종속된 개체를 보려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referencing_id = OBJECT_ID(N'Production.vProductAndDescription');   
    GO  
  
    ```  
  
#### <a name="to-view-the-objects-on-which-a-table-depends"></a>테이블이 종속된 개체를 보려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예에서는 `Production.Product`테이블에 종속된 개체를 반환합니다. 다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    SELECT * FROM sys.sql_expression_dependencies  
    WHERE referenced_id = OBJECT_ID(N'Production.Product');   
    GO  
  
    ```  
  
 자세한 내용은 [sys.sql_expression_dependencies&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)를 참조하세요.  
  
  