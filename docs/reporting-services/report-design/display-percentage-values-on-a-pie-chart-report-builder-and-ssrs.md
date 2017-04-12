---
title: "원형 차트에서 백분율 값 표시(보고서 작성기 및 SSRS) | Microsoft Docs"
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
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 6
---
# 원형 차트에서 백분율 값 표시(보고서 작성기 및 SSRS)
  기본적으로 범주는 범례에 표시되어 각 값을 식별합니다. 범주 레이블을 사용하여 원형 차트에 레이블을 적용했다면 범례에 백분율을 표시하기를 원할 것입니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### 원형 차트에 레이블로 백분율 값을 표시하려면  
  
1.  보고서에 원형 차트를 추가합니다. 자세한 내용은 [보고서에 차트 추가&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)를 참조하세요.  
  
2.  디자인 화면에서 원형을 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다. 원형 차트의 각 조각 내에 데이터 레이블이 표시됩니다.  
  
3.  디자인 화면에서 레이블을 마우스 오른쪽 단추로 클릭하고 **계열 레이블 속성**을 선택합니다. **계열 레이블 속성** 대화 상자가 표시됩니다.  
  
4.  **레이블 데이터** 옵션에 **#PERCENT**를 입력합니다.  
  
5.  (옵션) 레이블을 표시할 때 사용할 소수 자릿수를 지정하려면 "#PERCENT{P*n*}"를 입력합니다. 여기서 *n*은 표시할 소수 자릿수입니다. 예를 들어 소수 자릿수를 표시하지 않으려면 "#PERCENT{P0}"를 입력합니다.  
  
### 원형 차트의 범례에 백분율 값을 표시하려면  
  
1.  디자인 화면에서 원형 차트를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다. **계열 속성** 대화 상자가 표시됩니다.  
  
2.  **범례**에서 **사용자 지정 범례 텍스트** 속성에 **#PERCENT**를 입력합니다.  
  
## 참고 항목  
 [원형 차트 &#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [차트의 범례 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/formatting-the-legend-on-a-chart-report-builder-and-ssrs.md)   
 [원형 차트 외부에 데이터 요소 레이블 표시 &#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [원형 차트에서 작은 조각 수집 &#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  