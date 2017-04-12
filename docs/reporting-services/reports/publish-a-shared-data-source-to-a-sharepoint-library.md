---
title: "SharePoint 라이브러리에 공유 데이터 원본 게시 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "데이터 원본 [Reporting Services], SharePoint 라이브러리에 게시"
  - "SharePoint 통합 [Reporting Services], 라이브러리에 게시"
  - "보고서 게시 [Reporting Services], SharePoint 라이브러리에"
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
caps.latest.revision: 14
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 14
---
# SharePoint 라이브러리에 공유 데이터 원본 게시
  SharePoint 통합 모드에서 실행 중인 보고서 서버에 공유 데이터 원본을 게시하려면 보고서 디자이너에서 보고서 프로젝트 속성을 설정해야 합니다. 프로젝트 속성에서 서버, 보고서 및 공유 데이터 원본에 대한 모든 참조는 정규화된 URL이어야 합니다.  
  
 SharePoint 사이트에 대한 **멤버** 또는 **소유자** 권한이 있어야 합니다. 자세한 내용은 [SharePoint 모드의 보고서 서버에 게시된 보고서 항목에 대한 URL 예&#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)를 참조하세요.  
  
### SharePoint 사이트에 공유 데이터 원본을 게시하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 기존 또는 새로운 보고서 서버 프로젝트를 엽니다.  
  
2.  **프로젝트** 메뉴에서 **속성**을 클릭합니다. *\<프로젝트>***속성 페이지** 대화 상자가 열립니다.  
  
3.  SharePoint 사이트에 게시하는 데 사용할 **구성** 을 선택합니다(예:  
  
4.  프로젝트의 공유 데이터 원본을 게시하고 이전에 게시된 공유 데이터 원본을 덮어쓰려면 **OverwriteDataSources** 를 **True**로 설정합니다.  
  
5.  (옵션) **TargetDataSourceFolder**에 SharePoint 라이브러리 또는 라이브러리 폴더에 대한 URL을 입력합니다. 예를 들어 *http://TestServer/TestSite/Documents/DataSources*입니다.  
  
     값을 지정하지 않으면 **TargetReportFolder** 값이 사용됩니다.  
  
6.  **TargetReportFolder**에 라이브러리 또는 라이브러리 폴더에 대한 URL을 입력합니다. 예를 들어 http:*//TestServer/TestSite/Documents/Reports*입니다.  
  
7.  **TargetServerURL**에 SharePoint 최상위 사이트 또는 하위 사이트에 대한 URL을 입력합니다. 사이트를 지정하지 않으면 기본 최상위 사이트가 사용됩니다. 예를 들어 http://*servername*, http://*servername*/*site* 또는 http://*servername*/*site*/*subsite*입니다.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. 솔루션 탐색기에서 게시하려는 공유 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음 **배포**를 클릭합니다. 데이터 원본이 **TargetDataSourceFolder**에 지정된 위치에 게시됩니다. 출력 창에 배포 오류가 표시됩니다.  
  
    > [!NOTE]  
    >  SharePoint 사이트에 공유 데이터 원본을 게시하면 파일 확장명이 .rsds로 변경됩니다. SharePoint 사이트에서 공유 데이터 원본을 직접 편집 및 관리할 수 있습니다. 자세한 내용은 [공유 데이터 원본 만들기 및 관리&#40;SharePoint 통합 모드의 Reporting Services&#41;](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)를 참조하세요.  
  
## 관련 항목:  
 [SharePoint 라이브러리에 보고서 게시](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [SharePoint 모드의 보고서 서버에 게시된 보고서 항목에 대한 URL 예&#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [프로젝트 속성 페이지 대화 상자](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [배포 속성 설정&#40;Reporting Services&#41;](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [보고서 서버에 보고서 게시](../../reporting-services/reports/publishing-reports-to-a-report-server.md)   
 [보고서에 Office 데이터 연결&#40;.odc&#41; 사용&#40;SharePoint 통합 모드의 Reporting Services&#41;](../../reporting-services/report-data/use an office data connection (.odc) with reports.md)  
  
  