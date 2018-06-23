---
title: 저장 프로시저의 정의 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-stored-procs
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
caps.latest.revision: 29
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3b63ca5ff5b5373ea56c0df355c519d23054d07f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093039"
---
# <a name="view-the-definition-of-a-stored-procedure"></a>저장 프로시저의 정의 보기
    
##  <a name="Top"></a>[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 개체 탐색기 메뉴 옵션을 사용하거나 쿼리 편집기에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 저장 프로시저의 정의를 볼 수 있습니다. 이 항목에서는 의 개체 탐색기를 사용하거나 시스템 저장 프로시저, 시스템 함수 및 쿼리 편집기의 개체 카탈로그 뷰를 사용하여 프로시저 정의를 보는 방법에 대해 설명합니다.  
  
-   **시작하기 전 주의 사항:**  [보안](#Security)  
  
-   **프로시저 정의를 보려면:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 시스템 저장 프로시저: `sp_helptext`  
 **public** 역할의 멤버 자격이 필요합니다. 시스템 개체 정의는 공개적으로 표시됩니다. 개체 소유자나 ALTER, CONTROL, TAKE OWNERSHIP 또는 VIEW DEFINITION 권한 중 하나를 부여받은 사람은 사용자 개체의 정의를 볼 수 있습니다.  
  
 시스템 함수: `OBJECT_DEFINITION`  
 시스템 개체 정의는 공개적으로 표시됩니다. 개체 소유자나 ALTER, CONTROL, TAKE OWNERSHIP 또는 VIEW DEFINITION 권한 중 하나를 부여받은 사람은 사용자 개체의 정의를 볼 수 있습니다. 이 권한은 **db_owner**, **db_ddladmin**및 **db_securityadmin** 고정 데이터베이스 역할의 멤버가 암시적으로 보유합니다.  
  
 개체 카탈로그 뷰: `sys.sql_modules`  
 사용자가 소유하고 있거나 사용 권한을 부여 받은 보안 개체에 대해서만 카탈로그 뷰의 메타데이터를 볼 수 있습니다. 자세한 내용은 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)을 참조하세요.  
  
##  <a name="Procedures"></a> 저장 프로시저의 정의를 보는 방법  
 다음 중 하나를 사용할 수 있습니다.  
  
-   다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 **개체 탐색기에서 프로시저 정의를 보려면**  
  
1.  개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.  
  
2.  **데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.  
  
3.  **저장 프로시저**를 확장하고 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **저장 프로시저 스크립팅**을 클릭하고 **Create To**, **Alter To**또는 **Drop and Create To**중 하나를 클릭합니다.  
  
4.  **새 쿼리 편집기 창**을 선택합니다. 프로시저 정의가 표시됩니다.  
  
###  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 **쿼리 편집기에서 저장 프로시저의 정의를 보려면**  
  
 시스템 저장 프로시저: `sp_helptext`  
 1.  개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스에 연결합니다.  
  
2.  도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  쿼리 창에서 사용 하는 다음 문을 입력는 `sp_helptext` 시스템 저장 프로시저입니다. 원하는 데이터베이스와 저장 프로시저를 참조하도록 데이터베이스 이름과 저장 프로시저 이름을 변경합니다.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 시스템 함수: `OBJECT_DEFINITION`  
 1.  개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스에 연결합니다.  
  
2.  도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  쿼리 창에서 `OBJECT_DEFINITION` 시스템 함수를 사용하는 다음 문을 입력합니다. 원하는 데이터베이스와 저장 프로시저를 참조하도록 데이터베이스 이름과 저장 프로시저 이름을 변경합니다.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 개체 카탈로그 뷰: `sys.sql_modules`  
 1.  개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스에 연결합니다.  
  
2.  도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  쿼리 창에서 사용 하는 다음 문을 입력는 `sys.sql_modules` 카탈로그 뷰에 있습니다. 원하는 데이터베이스와 저장 프로시저를 참조하도록 데이터베이스 이름과 저장 프로시저 이름을 변경합니다.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>관련 항목  
 [저장 프로시저 만들기](create-a-stored-procedure.md)   
 [저장 프로시저 수정](modify-a-stored-procedure.md)   
 [저장 프로시저 삭제](delete-a-stored-procedure.md)   
 [저장 프로시저 이름 바꾸기](rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION&#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)   
 [sys.sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sp_helptext&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)   
 [OBJECT_ID&#40;Transact-SQL&#41;](/sql/t-sql/functions/object-id-transact-sql)  
  
  