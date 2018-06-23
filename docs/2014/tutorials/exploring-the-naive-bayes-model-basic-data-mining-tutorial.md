---
title: Naive Bayes 모델 (기본 데이터 마이닝 자습서) 탐색 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce01a9d352513e4b69bb4a9e735f30cc657a9c97
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311861"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Naive Bayes 모델 탐색(기본 데이터 마이닝 자습서)
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes 알고리즘은 자전거 구매와 입력된 특성 간의 상호 작용을 표시 하는 여러 가지 방법을 제공 합니다.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes 뷰어는 Naive Bayes 마이닝 모델 탐색 시 사용 하기 위해 다음과 같은 탭을 제공 합니다.  
  
 
  
##  <a name="DependencyNetwork"></a> 종속성 네트워크  
 **종속성 네트워크** 동일한 방식으로 작동 하는 탭의 **종속성 네트워크** 탭을 [!INCLUDE[msCoName](../includes/msconame-md.md)] 트리 뷰어. 뷰어의 각 노드는 특성을, 노드 사이의 선은 관계를 나타냅니다. 뷰어에서 예측 가능한 특성인 Bike Buyer의 상태에 영향을 주는 특성을 모두 확인할 수 있습니다.  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>종속성 네트워크 탭에서 모델을 탐색하려면  
  
1.  사용 하 여는 **마이닝 모델** 목록 맨 위에 있는 **마이닝 모델 뷰어** 탭으로 전환 하는 `TM_NaiveBayes` 모델입니다.  
  
2.  사용 하 여는 **뷰어** 전환 하려면 목록 **Microsoft Naive Bayes 뷰어**합니다.  
  
3.  클릭는 `Bike Buyer` 노드를 해당 종속성을 식별 합니다.  
  
     분홍색 음영은 모든 특성이 자전거 구매에 영향을 준다는 것을 나타냅니다.  
  
4.  슬라이더를 조정하여 가장 큰 영향을 주는 특성을 식별합니다.  
  
     슬라이더를 내리면 [Bike Buyer] 열에 가장 큰 영향을 주는 특성만 남습니다. 슬라이더를 조정하여 소유 차량 대수, 통근 거리 및 총 자녀 수가 가장 영향을 주는 특성 중 일부임을 알 수 있습니다.  
 
  
##  <a name="AttributeProfiles"></a> 특성 프로필  
 **특성 프로필** 탭 어떻게 서로 다른 입력된 특성에 영향 예측 가능한 특성의 결과 상태를 설명 합니다.  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>특성 프로필 탭에서 모델을 탐색하려면  
  
1.  에 **예측 가능** 상자를 확인 하는 `Bike Buyer` 을 선택 합니다.  
  
2.  경우는 **마이닝 범례** 의 표시를 차단 된 **특성 프로필**, 위치로 이동 합니다.  
  
3.  에 **히스토그램** 막대 상자 **5**합니다.  
  
     이 모델에서 5는 어느 한 변수의 상태에 지정할 수 있는 최대값입니다.  
  
     입력 특성의 각 상태 값 및 해당 특성이 예측 가능한 특성의 각 상태에서 가지는 분포와 함께 이 예측 가능 특성의 상태에 영향을 주는 특성이 나열됩니다.  
  
4.  에 **특성** 열을 찾을 **Number Cars Owned**합니다.  히스토그램에서 자전거 구매자(레이블이 1인 열)와 비구매자(레이블이 0인 열) 간의 차이를 확인하십시오. 차가 한 대 있거나 한 대도 없는 사람이 자전거를 구매할 확률이 더 높습니다.  
  
5.  두 번 클릭은 **Number Cars Owned** 자전거 구매자의 셀 (레이블이 1 인 열) 열입니다.  
  
     **마이닝 범례** 더 자세한 보기를 표시 합니다.  
  
  
##  <a name="AttributeCharacteristics"></a> 특성 특징  
 와 **특성 특징** 탭, 특성 및 값이 선택한 값 사례에 다른 특성에 대 한 값을 표시 하는 얼마나 자주 참조을 선택할 수 있습니다.  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>특성 특징 탭에서 모델을 탐색하려면  
  
1.  에 **특성** 나열 되어 있는지 확인 합니다. `Bike Buyer` 을 선택 합니다.  
  
2.  설정의 **값** 를 **1**합니다.  
  
     뷰어에서 자녀가 없고, 통근 거리가 짧고, 북미 지역에 사는 고객이 자전거를 구매할 가능성이 더 많음을 알 수 있습니다.  
  
  
##  <a name="AttributeDiscrimination"></a> 특성 판별  
 와 **특성 판별** 탭 자전거 구매의 두 불연속 값 및 기타 특성 값 사이의 관계를 조사할 수 있습니다. 때문에 `TM_NaiveBayes` 모델의 두 상태만 1과 0 뷰어를 변경할 필요가 없습니다.  
  
 뷰어에서 차량을 소유하지 않은 사람들이 자전거를 구매하고 두 대의 차량을 소유한 사람들이 자전거를 구매하지 않는 경향이 있음을 확인할 수 있습니다.  
  
## <a name="related-tasks"></a>관련 작업  
 다른 마이닝 모델을 탐색 하려면 다음 항목을 참조 하십시오.  
  
-   [의사 결정 트리 모델 탐색 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [클러스터링 모델 탐색 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>다음 단원  
 [5 단원: 모델 테스트 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>단원의 이전 태스크  
 [클러스터링 모델 탐색 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>관련 항목  
 [Microsoft Naive Bayes 뷰어를 사용 하 여 모델 찾아보기](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [특성 판별 탭 &#40;마이닝 모델 뷰어&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [특성 프로필 탭 &#40;마이닝 모델 뷰어&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [특성 특징 탭 &#40;마이닝 모델 뷰어&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [종속성 네트워크 탭 &#40;마이닝 모델 뷰어&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  