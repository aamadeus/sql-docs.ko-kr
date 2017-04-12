---
title: "사용자에게 DQS 역할 부여 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# 사용자에게 DQS 역할 부여
  이 항목에서는 Windows 보안 주체를 기반으로 SQL 로그인을 만들고 사용자에게 DQS_MAIN 데이터베이스에 대한 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]\(DQS) 역할을 부여하는 방법에 대해 설명합니다.  
  
## 필수 구성 요소  
  
-   DQSInstaller.exe 파일을 실행하여 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 설치를 완료해야 합니다. 자세한 내용은 [DQSInstaller.exe를 실행하여 Data Quality 서버 설치 완료](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)를 참조하세요.  
  
-   SQL 로그인을 만들고 DQS 역할을 부여하려면 Windows 사용자 계정은 적절한 고정 서버 역할(예: securityadmin, serveradmin 또는 sysadmin)의 멤버여야 합니다.  
  
### SQL 로그인을 만들고 DQS 역할을 부여하려면  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작합니다.  
  
2.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 SQL Server 인스턴스를 확장한 다음 **보안**을 확장합니다.  
  
3.  **보안** 폴더를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 다음 **로그인**을 클릭합니다.  
  
4.  **로그인 – 새로 만들기** 대화 상자에서 **로그인 이름** 상자에 Windows 사용자 이름을 지정하고 인증 유형으로 **Windows 인증**을 지정한 다음 **검색** 을 클릭하여 사용자를 확인합니다.  
  
5.  사용자 유효성을 확인한 후에 왼쪽 창에서 **사용자 매핑** 페이지를 클릭합니다.  
  
6.  오른쪽 창에서 **DQS_MAIN** 데이터베이스에 대해 **매핑** 열 아래의 확인란을 선택한 후 사용자에게 필요한 액세스 수준에 따라 **데이터베이스 역할 멤버 자격: DQS_MAIN** 창에서 **dqs_administrator**, **dqs_kb_editor** 또는 **dqs_kb_operator** 확인란을 선택합니다. 세 가지 DQS 역할에 대한 자세한 내용은 [DQS Security](../../data-quality-services/dqs-security.md)을 참조하십시오.  
  
7.  **로그인 – 새로 만들기** 대화 상자에서 **확인** 을 클릭하여 변경 내용을 적용합니다.  
  
    > [!NOTE]  
    >  사용자에게 **dqs_administrator** 역할을 부여할 경우 변경 내용을 적용한 후 사용자 권한을 다시 확인하면 다른 두 개의 DQS 역할 확인란(**dq_kb_editor** 및 **dqs_kb_operator**)도 함께 선택됩니다.  
  
## 다음 단계  
 바로 전에 SQL 로그인을 만들고 DQS 역할을 부여한 Windows 사용자 계정을 사용하여 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]에 로그인을 시도합니다.  
  
## 참고 항목  
 [Data Quality Services 설치](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [로그인 만들기](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  