---
title: 이상 값 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48073f6ce9c1d5836d85cf468b2b9a45256f8163
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082150"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>이상값(SQL Server 데이터 마이닝 추가 기능)
  ![데이터 마이닝 리본의 이상 값 마법사](media/dmc-outliers.gif "데이터 마이닝 리본의 이상 값 마법사")  
  
 *이상 값* 다음 이유 중 하나에 대 한 문제가 될 수 있는 데이터 값을 의미 합니다.  
  
-   값이 예상 범위를 벗어납니다.  
  
-   데이터가 잘못 입력되었습니다.  
  
-   값이 누락되었습니다.  
  
-   데이터가 공백 또는 다른 Null 문자열로 구성되어 있습니다.  
  
-   값은 정확하지만 분포된 범위를 너무 벗어나서 모델에 심각한 영향을 줄 수 있습니다.  
  
 Excel용 데이터 마이닝 클라이언트를 사용하여 이러한 데이터를 찾아낸 다음 값을 업데이트하거나 표시하지 않을 수 있습니다. 예를 들어 이상값을 산술 평균값으로 바꾸거나 잠재적으로 잘못된 값이 포함된 행을 삭제할 수 있습니다.  
  
## <a name="handling-outliers"></a>이상값 처리  
 **이상 값 제거** 마법사 이상 값을 적절히 처리 하도록 여러 가지 도구를 제공 합니다.  
  
-   먼저 이상값과 다른 데이터 간의 관계 및 값 분포를 보다 잘 파악하기 위해 데이터를 탐색할 수 있습니다.  
  
     예를 들어, 사용할 수는 **데이터 탐색** 작업을 검토 하 고 값을 수정 합니다. **이상 값 제거** 마법사에는 그래프의 한 줄 또는 모든 값의 분포를 쉽게 이해할 수 있도록 가로 막대형 차트도 표시 됩니다.  
  
-   다음으로 사용할 수 있습니다는 **이상 값** 마법사를 제거 하거나 이상 값을 변경 합니다. 사용자가 사용하는 방법은 불연속 값인지 아니면 연속 값인지에 따라 달라집니다.  
  
     이 마법사는 불연속 값을 막대형 차트로 표시하는데 각 막대는 데이터의 특정 값을 나타내며 막대의 높이는 각 값에 대한 사례 수를 나타냅니다. 차트의 임계값 컨트롤을 이동하여 극단적이거나 잠재적으로 잘못된 값 그룹을 나타내는 막대를 삭제할 수 있습니다.  
  
-   이 마법사는 연속 값을 막대형 차트 또는 꺾은선형 차트로 표시합니다. 꺾은선형 차트에서 값은 X축에 표시되며 값의 개수는 Y축에 표시됩니다.  
  
     제거 하거나 변경 하 여 차트의 상한값과 하한값에서 값을 유지 여부를 제어할 수 있습니다는 **최소** 및 **최대** 값 또는 막대를 이동 합니다. 최소값 및 최대값 설정을 변경하면 그래프에서 표시되지 않을 데이터가 음영으로 표시됩니다.  
  
 처리할 이상값을 선택한 후에는 이러한 이상값을 처리하는 방법을 설정할 수 있습니다. 이상값을 포함하고 있는 행을 삭제하거나 평균, null 또는 다른 선택 사항 값과 같은 대체 값을 지정할 수 있습니다.  
  
 끝으로 마법사는 새 데이터를 표시하는 몇 가지 동기화 옵션을 제공합니다. 원래 데이터를 새 값으로 바꾸거나 새 값을 포함하는 테이블에 새 열을 추가하거나 업데이트된 데이터를 포함하는 새 워크시트를 만들 수 있습니다.  
  
### <a name="using-the-outlier-wizard"></a>이상값 마법사 사용  
  
1.  에 **데이터 마이닝** 리본에서 클릭 **데이터 정리**, 선택 하 고 **이상 값**합니다.  
  
2.  에 **원본 데이터 선택** 대화 상자에서 Excel 데이터 테이블 또는 셀 범위를 선택 하 고 클릭 **다음**합니다.  
  
    > [!WARNING]  
    >  사용할 수 없습니다는 **이상 값** Excel에 먼저 복사 하지 않으면 외부 데이터에서 마법사.  
  
3.  에 **열 선택** 선택 대화 상자는 **단일** 열입니다.  
  
     **다음**을 클릭합니다.  
  
4.  에 **임계값 지정** 대화 상자에서 데이터 분포를 검토 합니다.  
  
    -   열에 불연속 값이 포함되어 있는 경우 마법사는 각 불연속 값에 대한 개수가 포함된 히스토그램을 표시합니다.  
  
         이상 값이 드문 값 이라고 가정할 필터링 할 수 있습니다 이러한으로 변경 하 여는 **최소** 값입니다.  
  
    -   열에 숫자 데이터가 포함 된 경우 클릭할 수 있습니다는 **불연속으로 보기** 단추 또는 **숫자로 보기** 단추는 가로 막대형 차트 또는 꺾은선형 차트에서 값 보기 사이 전환 합니다.  
  
5.  에 **임계값 지정** 대화 상자에서 최소값과 최대값을 입력 하거나 슬라이더 막대를 끌어 유지 하려는 데이터의 범위를 선택 합니다. **다음**을 클릭합니다.  
  
6.  에 **이상 값 처리** 대화 상자, 값을 삭제할지 아니면 바꿀지를 사용할지를 지정 하 고, 클릭 **다음**합니다.  
  
7.  에 **대상 선택** 대화 상자에서 새 데이터를 저장할 위치를 지정 합니다.  
  
### <a name="related-options"></a>관련 옵션  
 마법사는 다음과 같은 옵션을 제공합니다.  
  
|**옵션**|**설명**|  
|-----------------|-----------------|  
|**열 선택**|한 번에 하나의 열만 사용할 수 있습니다.|  
|**임계값 처리 지정**|사용 하 여 임계값 설정 **최소** 임계값 보다 적은 수의 행에 있는 값을 제외 하도록 합니다.<br /><br /> 처음에 값 **최소** 가장 적은 행이 포함 된 값과 동일한 값 보다 작은 최소를 만들 수 없는 합니다.|  
|**이상 값 처리**|이상값을 삭제하려는 경우 현재 워크시트에서 데이터를 변경하거나 새 워크시트에서 데이터의 복사본을 만들 수 있습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [데이터 탐색 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  