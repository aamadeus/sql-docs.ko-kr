---
title: "SQL Server 개체의 정책 기반 관리 패싯 보기 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "정책 기반 관리, 패싯 보기"
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# SQL Server 개체의 정책 기반 관리 패싯 보기
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 특정 SQL Server 개체에 적용되는 모든 정책 기반 관리 패싯을 보는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전에:**  
  
     [보안](#Security)  
  
-   **다음을 사용하여 개체의 모든 패싯을 보려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 사용 권한  
 msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### 개체의 모든 패싯을 보려면  
  
1.  개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스, 인스턴스 개체, 데이터베이스 또는 데이터베이스 개체를 마우스 오른쪽 단추로 클릭한 다음 **패싯**을 클릭합니다.  
  
2.  **패싯 보기 –***object_name* 대화 상자의 **패싯** 목록에서 해당 속성을 볼 패싯을 선택합니다. 이 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [View Facets Dialog Box](../../relational-databases/policy-based-management/view-facets-dialog-box.md)를 참조하세요.  
  
3.  완료되었으면 **확인**을 클릭합니다.  
  
  