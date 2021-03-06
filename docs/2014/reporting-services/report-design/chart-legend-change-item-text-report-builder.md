---
title: 범례 항목의 텍스트 변경(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ba16d9d50faaaef740f3aa4c4eaff5122fdff438
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081043"
---
# <a name="change-the-text-of-a-legend-item-report-builder-and-ssrs"></a>범례 항목의 텍스트 변경(보고서 작성기 및 SSRS)
  차트의 값 영역에 필드를 배치하면 해당 필드의 이름이 들어 있는 범례 항목이 자동으로 생성됩니다. 모든 범례 항목은 차트의 개별 계열에 연결됩니다. 단, 셰이프 차트의 경우에는 범례가 개별 계열 대신 개별 데이터 요소에 연결됩니다.  
  
 셰이프 차트에서는 범례 항목의 텍스트를 변경하여 개별 데이터 요소에 대해 추가적인 정보를 표시할 수 있습니다. 예를 들어 데이터 요소의 값을 범례에서 백분율로 표시 하려는 경우 사용할 수는 키워드와 같은 `#PERCENT`합니다. .NET Framework 형식 코드와 키워드를 함께 추가하여 숫자 및 날짜 형식을 적용할 수 있습니다. 키워드에 대한 자세한 내용은 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.  
  
 ![뾰족한 차트](../media/sharpchart.png "뾰족한 차트")  
  
 셰이프 차트가 아닌 차트에서도 범례 항목의 텍스트를 변경할 수 있습니다. 예를 들어 계열 이름이 "Series1"인 경우 "Sales for 2008"과 같이 이해하기 쉬운 텍스트로 변경할 수 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a>셰이프 차트의 범례에 나타나는 텍스트를 수정하려면  
  
1.  **값** 영역에 포함된 필드 또는 계열을 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다.  
  
2.  **범례** 를 클릭하고 **사용자 지정 범례 텍스트** 상자에서 키워드를 입력합니다.  
  
 다음 표에서는 **사용자 지정 범례 텍스트** 속성에 사용하는 차트별 키워드의 예를 보여 줍니다. 키워드에 대한 자세한 내용은 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.  
  
|키워드|Description|범례에 텍스트로 나타나는 항목의 예|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|합계 값의 백분율을 소수점 한 자리 수로 표시합니다.|85.0%|  
|`#VALY`|데이터 필드의 실제 숫자 값을 표시합니다.|17000|  
|`#VALY{C2}`|데이터 필드의 실제 숫자 값을 소수점 두 자리의 통화로 표시합니다.|$17000.00|  
|`#AXISLABEL (#PERCENT{P0})`|범주 필드의 텍스트 표현과 각 범주가 차트에 표시되는 백분율을 차례로 표시합니다.|Michael Blythe (85%)|  
  
> [!NOTE]  
>  #AXISLABEL 키워드는 **계열 그룹** 영역에 지정된 필드가 없을 때 런타임에만 평가될 수 있습니다.  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a>셰이프 차트가 아닌 차트의 범례에 나타나는 텍스트를 수정하려면  
  
1.  **값** 영역에 포함된 필드 또는 계열을 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다.  
  
2.  **범례** 를 클릭하고 **사용자 지정 범례 텍스트** 상자에서 범례 레이블을 입력합니다. 입력한 텍스트로 계열이 업데이트됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [차트의 범례 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [차트에서 계열 색 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [차트에서 범례 항목 숨기기&#40;보고서 작성기 및 SSRS&#41;](chart-legend-hide-items-report-builder.md)  
  
  
