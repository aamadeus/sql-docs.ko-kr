---
title: 마이닝 모델에 드릴스루 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0086339e2f4286257b6236f8caf297ce8cded202
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186201"
---
# <a name="enable-drillthrough-for-a-mining-model"></a>마이닝 모델에 드릴스루 사용
  마이닝 모델에 드릴스루를 사용하는 경우 모델을 찾을 때 모델을 만드는 데 사용된 사례에 대한 세부 정보를 검색할 수 있습니다. 이 정보를 보려면 필요한 사용 권한이 있어야 하고 구조가 이미 처리되어 있어야 합니다.  
  
 **권한** 사용자가 모델 데이터 또는 구조 데이터로 드릴스루하려면 마이닝 모델 또는 마이닝 구조에 대한 [AllowDrillThrough](../scripting/properties/allowdrillthrough-element-assl.md) 권한이 있는 역할의 멤버여야 합니다. 드릴스루 권한은 구조와 모델에 개별적으로 설정됩니다.  
  
-   모델에 대한 드릴스루 권한이 있으면 구조에 대한 사용 권한이 없는 경우에도 모델에서 드릴스루할 수 있습니다.  
  
-   구조에 대한 드릴스루 권한이 있으면 추가적으로 [StructureColumn&#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 함수를 사용하여 모델에서 드릴스루 쿼리에 구조 열을 포함할 수도 있습니다. SELECT… \<구조 > 합니다. 경우 구문입니다.  
  
 **학습 사례의 캐싱** 드릴스루는 마이닝 구조의 학습 사례에 대한 정보를 검색하는 방식으로 작동합니다. 이 정보는 구조가 처리될 때 캐시됩니다. 따라서를 지우도록 선택한 경우 모든 캐시 된 데이터를 변경 하 여는 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 속성을 `ClearAfterProcessing`, 드릴스루가 작동 하지 것입니다.  
  
> [!NOTE]  
>  학습 사례가 캐시되지 않은 경우에는 사례 데이터를 보기 전에 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 속성을 **KeepTrainingCases** 로 변경한 다음 모델을 다시 처리해야 합니다.  
  
 자세한 내용은 [드릴스루 쿼리&#40;데이터 마이닝&#41;](drillthrough-queries-data-mining.md)를 참조하세요.  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>마이닝 모델에서 드릴스루를 사용하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에 있는 데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 드릴스루를 사용할 마이닝 모델의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
2.  **속성** 창에서 **AllowDrillthrough**를 클릭하고 **True**를 선택합니다.  
  
3.  **마이닝 모델** 탭에서 모델을 마우스 오른쪽 단추로 클릭하고 **모델 처리**를 선택합니다.  
  
### <a name="to-enable-caching-for-a-mining-structure"></a>마이닝 구조에 캐싱을 사용하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 데이터 마이닝 디자이너에 있는 **마이닝 구조** 탭에서 마이닝 구조 이름을 마우스 오른쪽 단추로 클릭합니다.  
  
2.  **속성** 창을 엽니다.  
  
3.  **속성** 창에서 **CacheMode** 속성을 찾고 목록에서 **KeepTrainingCases** 를 선택합니다.  
  
4.  **데이터베이스** 메뉴에서 **처리**를 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [드릴스루 쿼리 &#40;데이터 마이닝&#41;](drillthrough-queries-data-mining.md)  
  
  