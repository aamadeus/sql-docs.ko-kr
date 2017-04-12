---
title: "모바일 보고서에 매개 변수 추가 | Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "11/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 113cb057-deec-40eb-abc8-f35d3900eaa6
caps.latest.revision: 12
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 12
---
# 모바일 보고서에 매개 변수 추가 | Reporting Services
작성자와 보고서를 읽는 사람이 보고서를 필터링할 수 있도록 매개 변수가 있는 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 모바일 보고서를 작성할 수 있습니다. 매개 변수가 있는 보고서는 [원본 보고서에서 드릴스루](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)의 대상이 될 수도 있습니다. 

매개 변수가 있는 모바일 보고서를 만들려면 적어도 하나의 매개 변수가 있는 공유 데이터 집합으로 시작합니다. [공유 데이터 집합에 매개 변수 만들기](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)를 참조하세요.  

모바일 보고서에 매개 변수를 추가한 후 URL을 만들어 [쿼리 문자열 매개 변수가 있는 보고서를 열 수 있습니다.](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters.md)

1. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion.md)] 웹 포털의 위쪽 표시줄에서 **새로 만들기** > **모바일 보고서**를 선택합니다.  
  
   ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png)  
     
2. [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-long.md)]왼쪽 위에서 **데이터** 탭을 선택합니다.   
  
3. 오른쪽 위에서 **데이터 추가**를 선택합니다.  
  
4. **보고서 서버**를 선택한 다음 서버를 선택합니다.  
  
5. 서버의 공유 데이터 집합으로 이동한 다음 매개 변수가 있는 데이터 집합을 선택합니다.  
  
   표에 데이터 집합의 데이터가 표시됩니다. 괄호**{ }** 안에 녹색 원은 매개 변수가 있는 데이터 집합을 표시합니다.  
     
   ![SSMRP_PforParam](../../reporting-services/mobile-reports/media/ssmrp-pforparam.png)  
  
6. 탭에서 코그를 선택한 다음 **매개 변수 {}**를 선택합니다.  
  
   ![SSMRP_ParamWheel](../../reporting-services/mobile-reports/media/ssmrp-paramwheel.png)  
  
7. 매개 변수에 값을 전달할 보고서 요소를 선택합니다.  
  
   ![SSMRP_SetParam](../../reporting-services/mobile-reports/media/ssmrp-setparam.png)  
     
8. **미리 보기**를 선택하면 보고서가 표시되는 모양을 확인할 수 있습니다. 이 보고서에서 선택 목록은 범주 매개 변수를 사용합니다.

   ![sql-server-mobile-report-publisher-Selection-List-View-No-Selection](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-view-no-selection.png) 
   
9. 선택 목록에서 값을 선택하면 보고서는 해당 값으로 필터링됩니다(이 경우 보조 프로그램).

   ![sql-server-mobile-report-publisher-Selection-List-Category-Selected](../../reporting-services/mobile-reports/media/sql-server-mobile-report-publisher-selection-list-category-selected.png)   
  
### 참고 항목  
-  [특정 쿼리 문자열 매개 변수가 있는 모바일 보고서 열기](../../reporting-services/mobile-reports/open-a-mobile-report-with-specific-query-string-parameters.md)
-  [모바일 보고서에서 다른 모바일 보고서나 URL로 드릴스루 추가](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)
-  [공유 데이터 집합 또는 포함된 데이터 집합 만들기](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)
- [SQL Server 모바일 보고서 게시자를 사용하여 모바일 보고서 만들기 및 게시](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
  
  