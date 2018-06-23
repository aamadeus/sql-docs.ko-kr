---
title: 운영자에 대한 정보 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, operators
- viewing operators
- operators (users) [Database Engine], viewing with Management Studio
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- displaying operators
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cdabd9ef6382066fad31154dad126e30ced0d8d2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079664"
---
# <a name="view-information-about-an-operator"></a>View Information About an Operator
  이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 운영자에 대한 정보를 보는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **다음을 사용하여 운영자에 대한 정보를 봅니다.**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 기본적으로 **sysadmin** 고정 서버 역할의 멤버는 이 저장 프로시저를 실행할 수 있습니다. 다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-view-information-about-an-operator"></a>운영자에 대한 정보를 보려면  
  
1.  **개체 탐색기**에서 더하기 기호를 클릭하여 보려는 운영자가 들어 있는 서버를 확장합니다.  
  
2.  더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.  
  
3.  더하기 기호를 클릭하여 **운영자** 폴더를 확장합니다.  
  
4.  보려는 운영자를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
     *operator_name***속성** 대화 상자에 포함된 사용 가능한 옵션에 대한 자세한 내용은 다음을 참조하세요.  
  
    -   [New 연산자 및 operator 속성 &#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [운영자 속성: New 연산자 &#40;알림 페이지&#41;](operator-properties-new-operator-notifications-page.md)  
  
    -   [운영자 속성&#40;기록 페이지&#41;](operator-properties-history-page.md)  
  
5.  완료되었으면 **확인**을 클릭합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-view-information-about-an-operator"></a>운영자에 대한 정보를 보려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    -- reports information about operator François Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'François Ajenstat' ;  
    GO  
    ```  
  
 자세한 내용은 참조 [sp_help_operator &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql)합니다.  
  
  