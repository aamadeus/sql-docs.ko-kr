---
title: "보고서 작성기에서 보고서 미리 보기 | Microsoft Docs"
ms.custom: ""
ms.date: "01/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# 보고서 작성기에서 보고서 미리 보기
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 페이지를 매긴 보고서를 만들 때 보고서에 원하는 항목이 표시되는지 확인하기 위해 자주 보고서를 미리 보는 것이 유용합니다. 보고서를 미리 보려면 **실행**을 클릭합니다. 보고서가 미리 보기 모드에서 렌더링됩니다.  
  
 보고서 작성기는 보고서 서버에 연결될 때 편집 세션을 사용하여 미리 보기 환경을 개선합니다. 편집 세션에서는 데이터 캐시를 만들고 반복된 보고서 미리 보기에 사용할 수 있는 캐시에 데이터 집합을 만듭니다. 편집 세션은 직접 상호 작용하는 기능이 아니지만 캐시된 데이터 집합이 새로 고쳐지는 경우를 이해하면 보고서를 미리 볼 때 성능을 높이고 보고서가 더 빠르거나 더 느리게 렌더링되는 이유를 이해하는 데 도움이 됩니다.  
  
 편집 세션에서는 보고서 서버에 저장된 이미지 또는 하위 보고서와 같은 참조 항목이나 포함된 데이터 원본을 사용하는 보고서를 편집할 수 있다는 이점도 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 미리 보기 성능 향상  
 보고서를 만들고 업데이트하는 방법은 보고서가 미리 보기에서 렌더링되는 속도에 영향을 미칩니다. 서버 참조를 사용하는 보고서를 처음 미리 볼 때 편집 세션이 자동으로 생성되고 보고서가 실행될 때 사용된 데이터가 보고서 서버에 저장된 데이터 캐시에 추가됩니다. 데이터에 영향을 미치지 않는 보고서를 변경하는 경우 데이터의 캐시된 복사본이 보고서에서 사용됩니다. 이에 따라 보고서를 미리 볼 때마다 데이터 변경 내용이 표시되지는 않습니다. 새 데이터를 원하는 경우 리본에서 **새로 고침** 단추를 클릭합니다.  
  
 다음 동작을 수행하면 캐시가 새로 고쳐지고 다음에 보고서를 미리 볼 때 보고서 렌더링 속도가 느려집니다.  
  
-   데이터 집합 추가, 변경 또는 삭제. 캐시된 데이터 집합에는 보고서에서 사용하는 모든 데이터 집합이 포함되며 데이터 집합을 수정하면 캐시된 데이터 집합이 무효화됩니다. 이러한 수정에는 데이터 집합에서 이름, 쿼리 또는 필드를 변경하는 작업이 포함됩니다.  
  
    > [!NOTE]  
    >  데이터 집합에 사용하지 않을 필드가 많이 있는 경우 데이터 집합을 업데이트하여 이러한 필드를 생략하는 것을 고려해야 합니다. 이렇게 하면 새 편집 세션이 만들어지고 보고서를 처음 미리 볼 때 속도가 느려지지만 캐시된 데이터 집합의 크기가 작아지므로 보고서 서버의 성능에 전반적으로 도움이 됩니다.  
  
-   데이터 원본 추가, 변경 또는 삭제. 여기에는 데이터 원본의 이름 또는 속성, 데이터 원본의 데이터 확장 또는 데이터 원본에 대한 연결의 속성을 변경하는 작업이 포함됩니다.  
  
-   보고서에서 사용하는 공유 데이터 원본을 다른 데이터 원본으로 변경  
  
-   보고서의 언어 변경  
  
-   보고서에서 사용하는 어셈블리 또는 사용자 지정 코드 변경  
  
-   보고서의 쿼리 매개 변수나 매개 변수 값 추가, 변경 또는 삭제  
  
 보고서 레이아웃과 데이터 서식의 변경은 캐시된 데이터 집합에 영향을 미치지 않습니다. 캐시된 데이터 집합을 새로 고치지 않고 다음 동작을 수행할 수 있습니다.  
  
-   테이블, 행렬, 차트 등의 데이터 영역 추가 또는 제거  
  
-   보고서에서 열 추가 또는 삭제. 데이터 집합의 모든 필드를 보고서에서 사용할 수 있습니다. 보고서에서 필드를 추가하거나 제거해도 데이터 집합에 영향을 미치지 않습니다.  
  
-   테이블 및 행렬의 필드 순서 변경  
  
-   행 및 열 그룹 추가, 변경 또는 삭제  
  
-   필드의 데이터 값 서식 추가, 변경 또는 삭제  
  
-   이미지, 선 또는 입력란 추가, 변경 또는 삭제  
  
-   페이지 나누기 변경  
  
 편집 세션은 보고서를 처음 미리 볼 때 생성됩니다. 기본적으로 편집 세션은 7200초(2시간) 동안 지속됩니다. 편집 세션은 보고서를 실행할 때마다 2시간으로 다시 설정됩니다. 편집 세션이 만료되면 데이터 캐시가 삭제됩니다. 편집 세션이 만료되면 보고서를 다음에 미리 볼 때 편집 세션이 자동으로 다시 생성됩니다. 편집 세션의 만료 시간은 구성할 수 있습니다. 2시간이 너무 길거나 너무 짧은 경우 보고서 서버 관리자에게 문의하십시오.  
  
 기본적으로 데이터 캐시는 데이터 집합을 5개까지 포함할 수 있습니다. 매개 변수 값의 다양한 조합을 사용하는 경우 보고서에 데이터가 더 필요할 수 있습니다. 이 경우 캐시가 새로 고쳐져야 하고 다음에 보고서를 미리 볼 때 보고서가 더 느리게 렌더링됩니다. 캐시의 항목 수는 보고서 서버의 관리자가 구성할 수 있습니다.  
  
## 보고서 업데이트의 동시성  
 보고서를 업데이트한 다음 보고서 서버에 저장하는 경우 중간에 보고서를 미리 보는 경우가 많습니다. 보고서를 업데이트할 때 다른 사용자가 보고서를 업데이트한 다음 동시에 저장할 수도 있습니다. 마지막으로 저장된 보고서가 이후에 보고 업데이트할 때 사용할 수 있는 보고서 버전입니다. 즉, 미리 본 보고서 버전이 다시 연 버전이 아닐 수도 있습니다. 보고서 작성기 메뉴에서 **다른 이름으로 저장** 옵션을 사용하여 새 이름으로 보고서를 저장하는 옵션이 있습니다.  
  
## 외부 보고서 항목  
 보고서에는 공유 데이터 원본, 외부 이미지, 보고서에서 별도로 저장된 하위 보고서 등의 항목이 포함될 수 있습니다. 항목이 별도로 저장되기 때문에 항목을 보고서 서버의 다른 위치로 이동하거나 삭제할 수 있습니다. 이 경우 보고서를 미리 보지 못할 수 있습니다. 항목의 업데이트된 위치를 나타내기 위해 보고서를 업데이트하거나, 항목이 삭제된 경우 항목을 기존 항목으로 바꾸거나 보고서에서 항목에 대한 참조를 제거할 수 있습니다.  
  
 보고서에서 사용하는 하위 보고서가 편집 세션이 생성된 후 변경되는 경우 보고서가 미리 보기에서 렌더링되지 않습니다. 보고서를 성공적으로 미리 보려면 보고서를 저장하거나 **새로 고침** 을 클릭하여 새로운 데이터를 가져와야 합니다.  
  
## 관련 항목:  
 [보고서 데이터 집합&#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [보고서 항목 서식 지정&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [차트&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [보고서 저장&#40;보고서 작성기&#41;](../../reporting-services/report-builder/saving-reports-report-builder.md)  
  
  