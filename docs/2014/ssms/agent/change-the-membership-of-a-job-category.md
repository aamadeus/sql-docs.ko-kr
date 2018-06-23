---
title: 작업 범주의 멤버 자격 변경 | Microsoft 문서
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
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb8bb0ade433b6c72f41409ba1cd247fb983b50d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36090374"
---
# <a name="change-the-membership-of-a-job-category"></a>Change the Membership of a Job Category
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 SQL Server 관리 개체를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 작업 범주의 멤버 자격을 변경하는 방법에 대해 설명합니다.  
  
 작업 범주를 사용하면 작업을 쉽게 필터링하고 그룹화할 수 있게 구성할 수 있습니다. 사용자 고유의 작업 범주를 만들 수 있습니다. 또한 작업 범주에서 Microsoft SQL Server 에이전트 작업 멤버 자격을 변경할 수도 있습니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **작업 범주의 멤버 자격을 변경하려면:**  
  
     다른 도구는 [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 관리 개체](#SMO)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
 자세한 내용은 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)을 참조하세요.  
  
##  <a name="SSMS"></a> SQL Server Management Studio 사용  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>작업 범주의 멤버를 변경하려면  
  
1.  **개체 탐색기**에서 더하기 기호를 클릭하여 작업 범주를 편집하려는 서버를 확장합니다.  
  
2.  더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.  
  
3.  **작업** 폴더를 마우스 오른쪽 단추로 클릭하고 **작업 범주 관리**를 선택합니다.  
  
4.  **작업 범주 관리***server_name* 대화 상자에서 편집하려는 작업 범주를 선택한 다음, **작업 보기**를 클릭합니다.  
  
5.  **모든 작업 표시** 확인란을 선택합니다.  
  
6.  범주에 작업을 추가하려면 주 표 형태의 **선택** 열에서 해당 작업에 대한 확인란을 선택합니다. 범주에서 작업을 제거하려면 해당 확인란의 선택을 취소합니다. 완료되었으면 **확인**을 클릭합니다.  
  
7.  **작업 범주 관리***server_name* 대화 상자를 닫습니다.  
  
##  <a name="TSQL"></a> Transact-SQL 사용  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>작업 범주의 멤버를 변경하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 자세한 내용은 참조 [sp_update_job &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)합니다.  
  
##  <a name="SMO"></a> SQL Server Management Objects를 사용 하 여  
 **작업 범주의 멤버를 변경하려면**  
  
 사용 하 여 `JobCategory` Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용 하 여 클래스입니다.  
  
  