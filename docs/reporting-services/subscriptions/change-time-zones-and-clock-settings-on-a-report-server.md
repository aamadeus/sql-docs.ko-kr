---
title: "보고서 서버에서 표준 시간대 및 시계 설정 변경 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "표준 시간대 [Reporting Services]"
  - "시계 [Reporting Services]"
  - "일정 [Reporting Services], 시계 설정"
  - "일정 [Reporting Services], 시간대"
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
caps.latest.revision: 22
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 22
---
# 보고서 서버에서 표준 시간대 및 시계 설정 변경
  보고서 서버는 항상 설치된 컴퓨터의 현지 시간을 사용합니다. 다른 표준 시간대를 사용하도록 구성할 수 없습니다. 클라이언트 응용 프로그램이 다른 표준 시간대의 보고서 서버를 가리키는 경우 해당 보고서 서버의 표준 시간대를 사용하여 예약된 작업을 실행합니다. 보고서 관리자 및 SharePoint 관리 페이지에서 표준 시간대가 각 일정 페이지에 표시되므로 예약된 작업이 언제 수행되는지 정확히 알 수 있습니다. 예를 들어 사용자 지정 일정을 만들기 위한 페이지에 "시간은 (UTC-08: 00) 태평양 표준시(미국 및 캐나다)로 표시됩니다."라고 나타납니다.  
  
## 표준 시간대(기본 모드) 변경  
 보고서 서버를 호스팅하는 컴퓨터의 표준 시간대를 변경하는 경우 보고서 서버 서비스를 다시 시작해야 표준 시간대의 변경 내용이 적용됩니다.  
  
 기존 보고서 기록 스냅숏의 타임스탬프 값은 새 표준 시간대 설정으로 동기화됩니다. 오전 9시에 보고서 기록 스냅숏을 생성하고 표준 시간대를 1시간 늦춰 다시 설정한 경우 생성된 스냅숏의 타임스탬프는 오전 9시에서 오전 10시로 변경됩니다.  
  
 일정은 새 표준 시간대로 매핑되는 것을 제외하고는 기존 설정을 유지합니다. 예를 들어 일정이 태평양 표준시로 오전 2시에 실행되는 경우 표준 시간대를 동부 오스트레일리아 표준시로 변경하면 일정이 동부 오스트레일리아 표준시로 오전 2시에 실행됩니다.  
  
 폴더나 링크된 보고서 항목이 생성되는 시간과 같은 속성 타임스탬프 값은 새 표준 시간대 설정으로 동기화되지 않습니다. 6월 25일 오전 9시에 항목을 만들고 표준 시간대나 시계를 다시 설정해도 해당 타임스탬프는 6월 25일 오전 9시로 유지됩니다.  
  
## 표준 시간대(SharePoint 모드) 변경  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드를 위한 표준 시간대 구성은 SharePoint 국가별 설정의 일부로 관리됩니다. 자세한 내용은 [국가별 설정(SharePoint Server 2010)(http://technet.microsoft.com/library/cc824907.aspx)](http://technet.microsoft.com/library/cc824907.aspx)을 참조하세요.  
  
## 시계 설정 변경  
 컴퓨터 시계를 변경해도 기존 타임스탬프 값에는 영향이 없습니다. 예를 들어 시계를 1시간 앞으로 이동해도 보고서 기록 스냅숏의 타임스탬프는 변경되지 않습니다. 10초 정도 경과 후 일정 예약 및 배달 프로세스에 새 설정이 사용됩니다. 구성 파일의 폴링 간격 설정을 수정한 경우 실제 지연 시간이 다를 수 있습니다.  
  
## 관련 항목:  
 [보고서 서버 서비스 시작 및 중지](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)   
 [일정](../../reporting-services/subscriptions/schedules.md)  
  
  