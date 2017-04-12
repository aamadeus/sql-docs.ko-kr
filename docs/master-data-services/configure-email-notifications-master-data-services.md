---
title: "전자 메일 알림 구성(Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "전자 메일 [Master Data Services], 구성"
  - "알림 [Master Data Services], 알림 구성"
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# 전자 메일 알림 구성(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에서 전자 메일 메시지를 자동으로 보내도록 하려면 알림 전자 메일을 구성합니다.  
  
### 알림을 구성하려면  
  
1.  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]의 **데이터베이스** 페이지에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택합니다.  
  
2.  **시스템 설정** 섹션에서 **프로필 만들기**를 클릭합니다.  
  
3.  모든 필수 필드에 내용을 입력합니다. 자세한 내용은 [데이터베이스 메일 프로필 및 계정 만들기 대화 상자&#40;Master Data Services 구성 관리자&#41;](../master-data-services/create database mail profile and account dialog box.md)를 참조하세요.  
  
4.  **확인**을 클릭합니다.  
  
    > [!NOTE]  
    >  알림을 구성한 후에는 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 를 사용하여 변경할 수 없으며 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 직접 변경해야 합니다. 자세한 내용은 [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md)을(를) 참조하세요.  
  
## 다음 단계  
  
-   [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에는 알림에 영향을 주는 설정이 있습니다. 이러한 설정은 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 조정하거나 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 시스템 설정 테이블에서 직접 조정할 수 있습니다. 자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md)을 참조하세요.  
  
## 관련 항목:  
 [알림&#40;Master Data Services&#41;](../master-data-services/notifications-master-data-services.md)   
 [전자 메일 알림 문제 해결(Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)   
 [알림을 보내도록 비즈니스 규칙 구성&#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  