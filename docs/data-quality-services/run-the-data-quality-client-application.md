---
title: "데이터 품질 클라이언트 응용 프로그램 실행 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.browseforservers.f1"
  - "sql13.dqs.connecttoserver.f1"
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# 데이터 품질 클라이언트 응용 프로그램 실행
  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]을(를) 실행하고 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]에 로그온합니다.  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전 주의 사항  
  
###  <a name="Prerequisites"></a> 필수 구성 요소  
 DQSInstaller.exe 파일을 실행하여 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 설치를 완료해야 합니다. 자세한 내용은 참조 [DQSInstaller.exe 완료 Data Quality 서버 설치를 실행](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)합니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 사용 권한  
 DQS_MAIN 데이터베이스에 대해 세 가지 DQS 역할(dqs_adminstrator, dqs_kb_editor 또는 dqs_kb_operator) 중 하나가 있어야 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]에 로그온할 수 있습니다.  
  
##  <a name="Run"></a> Data Quality 클라이언트 실행  
 설치된 컴퓨터에서 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 를 실행하려면 다음과 같이 진행합니다.  
  
1.  **시작**을 클릭하고 **모든 프로그램**을 가리킨 다음 **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, **Data Quality Services**, **Data Quality 클라이언트**를 차례로 클릭합니다.  
  
2.  **서버에 연결** 대화 상자에서  
  
    1.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 응용 프로그램을 연결할 서버를 지정합니다. 선택 **(로컬)** 연결할 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 로컬 컴퓨터에 있습니다. 아래쪽 화살표를 클릭 하 고 선택할 수도 있습니다 **\< 추가 서버 찾아보기 네트워크>** 다른 서버에 연결 (또는 이름으로 로컬 서버에 연결). **서버 찾아보기** 대화 상자가 표시됩니다. **로컬 서버** 탭이나 **네트워크 서버** 탭에서 서버를 선택할 수 있습니다.  
  
    2.  [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 와 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]사이의 데이터 전송을 암호화하려면 **옵션**을 클릭하고 **연결 암호화** 확인란을 선택합니다.  
  
3.  **연결**을 클릭합니다.  
  
 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면이 나타납니다. 자세한 내용은 참조 [데이터 품질 클라이언트 홈 화면](../data-quality-services/data-quality-client-home-screen.md)합니다.  
  
  