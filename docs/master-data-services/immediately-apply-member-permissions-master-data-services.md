---
title: "멤버 권한 즉시 적용(Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "멤버 [Master Data Services], 권한 즉시 적용"
  - "권한 [Master Data Services], 멤버 권한 즉시 적용"
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# 멤버 권한 즉시 적용(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버 보안이 일정한 간격으로 적용되기를 기다리는 대신 멤버 권한을 즉시 적용할 수 있습니다.  
  
## 필수 구성 요소  
 이 절차를 수행하려면  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 mdm.udpSecurityMemberProcessRebuildModel 저장 프로시저를 실행할 수 있는 사용 권한이 있어야 합니다. 자세한 내용은 [데이터베이스 개체 보안&#40;Master Data Services&#41;](../master-data-services/database-object-security-master-data-services.md)을 참조하세요.  
  
### 계층 멤버 권한을 즉시 적용하려면  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 을(를) 열고 [!INCLUDE[ssDE](../includes/ssde-md.md)] 데이터베이스의 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 연결합니다.  
  
2.  새 쿼리를 만듭니다.  
  
3.  다음 텍스트를 입력하여 *database*를 데이터베이스 이름으로 바꾸고 *Model_Name*을 모델 이름으로 바꿉니다.  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  쿼리를 실행합니다.  
  
## 관련 항목:  
 [계층 멤버 권한 할당&#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [계층 멤버 권한&#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  