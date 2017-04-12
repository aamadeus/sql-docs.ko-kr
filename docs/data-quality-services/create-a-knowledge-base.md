---
title: "기술 자료 만들기 | Microsoft Docs"
ms.custom: ""
ms.date: "06/04/2013"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.kb.selectkb.f1"
  - "sql13.dqs.kb.newkb.f1"
ms.assetid: 2733a284-975f-4650-abcc-cc2aad074cab
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# 기술 자료 만들기
  이 항목에서는 DQS([!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)])에서 기술 자료를 만들고 도메인 관리, 기술 자료 검색 또는 일치 정책 추가를 수행할 준비를 갖추는 방법에 대해 설명합니다.  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Prerequisites"></a> 필수 구성 요소  
 기술 자료를 만들려면 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 및 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]가 설치되어 있어야 합니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 사용 권한  
 기술 자료를 만들려면 DQS_MAIN 데이터베이스의 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.  
  
##  <a name="Createaknowledgebase"></a> 기술 자료 만들기  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [데이터 품질 클라이언트 응용 프로그램 실행](../data-quality-services/run-the-data-quality-client-application.md)합니다.  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **새 기술 자료**를 클릭합니다.  
  
3.  새 기술 자료의 이름과 설명을 입력합니다.  
  
4.  **기술 자료 만들기**에서 기술 자료의 기반으로 사용할 항목을 선택합니다.  
  
    -   기존 기술 자료나 데이터 파일을 기반으로 새 기술 자료를 만들지 않으려면 **없음** 을 선택합니다.  
  
    -   이미 **에서 만든 기술 자료나 기본 기술 자료를 기반으로 새 기술 자료를 만들려면** 기존 기술 자료 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]를 선택합니다. 기술 자료를 선택는 **기술 자료 선택** 드롭 다운 목록 또는 클릭 **찾아보기** 표시 하는 **기술 자료 선택** 대화 상자에서 기존 기술 자료를 자료 새 기술 자료, 선택한 다음 **확인**. 표에서 기술 자료를 선택하면 기술 자료의 도메인과 일치 규칙이 대화 상자 오른쪽 창에 표시됩니다. 선택할 수도 있습니다는 **DQS 데이터** 공용의 기본 도메인 및 미국 회사, 주소 및 파티 데이터와 관련 된 기술 자료를 포함 하는 기본 기술 자료를 기술 합니다.  
  
    -   **의 DQS 파일을 새 기술 자료의 기반으로 사용하려면** DQS 파일에서 가져오기 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]를 선택합니다. **찾아보기**를 클릭하고 확장명이 .dqs인 DQS 데이터 파일을 선택한 후 **확인**을 클릭합니다.  
  
5.  **작업 선택**에서 새 기술 자료에 대해 수행할 작업을 선택합니다.  
  
    -   기술 자료를 만들고 기술 자료의 도메인을 수정하는 데 사용하는 화면으로 이동하려면 **도메인 관리** 를 선택합니다.  
  
    -   기술 자료를 만들고, 데이터 샘플을 분석하고 기술 자료의 도메인에 결과를 채우는 데 사용하는 마법사를 시작하려면 **기술 자료 검색** 을 선택합니다.  
  
    -   **일치 정책** 을 선택하여 일치 정책을 만들고 기술 자료에 추가합니다.  
  
6.  **만들기**를 클릭합니다.  
  
##  <a name="FollowUp"></a> 후속 작업: 기술 자료를 만든 후  
 기술 자료를 만든 후에는 기술 자료 검색을 수행하는 데 사용할 수 있는 마법사, 일치 정책을 만드는 데 사용하는 마법사 또는 도메인 관리를 수행할 수 있는 페이지가 나타납니다. 기술 자료 검색, 도메인 관리 또는 일치 정책에 대 한 자세한 내용은 참조 [기술 자료 검색 수행](../data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../data-quality-services/managing-a-domain.md), 또는 [일치 정책을 만드는](../data-quality-services/create-a-matching-policy.md)합니다.  
  
  