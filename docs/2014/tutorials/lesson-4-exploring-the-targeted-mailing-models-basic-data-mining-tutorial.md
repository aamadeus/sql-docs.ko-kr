---
title: '4 단원: 타겟된 메일링 모델 (기본 데이터 마이닝 자습서) 탐색 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
caps.latest.revision: 51
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 57ebae0dfb1e8f472647818cad2c8f724e8b3c0e
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313178"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a>4단원: 타겟 메일링 모델 탐색(기본 데이터 마이닝 자습서)
  프로젝트의 모델이 처리되면 이러한 모델을 탐색하여 관심 있는 추세를 찾아볼 수 있습니다. 숫자만 보는 경우 패턴이 복잡하고 어려울 수 있기 때문에 SQL Server 데이터 마이닝은 데이터를 조사하고 알고리즘이 데이터 내에서 발견한 규칙과 관계를 이해하는 데 도움을 주는 몇 가지 시각적 도구를 제공합니다. 또한 다양한 정확도 테스트를 사용하여 데이터 집합의 유효성을 검사하거나 모델을 배포하기 전에 성능이 가장 뛰어난 모델을 찾을 수 있습니다.  
  
 사용 하는 경우 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 경우 만들어진 각 모델에 나열 된 모델을 탐색 하 고 **마이닝 모델 뷰어** 데이터 마이닝 디자이너의 탭 합니다. 뷰어를 사용하여 모델을 탐색할 수 있습니다. 이러한 뷰는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서도 사용할 수 있습니다.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 모델을 작성하는 데 사용하는 각 알고리즘에 따라 다른 유형의 결과가 반환됩니다. 따라서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 기계 학습 모델의 각 형식에 대 한 사용자 지정 뷰어를 제공 합니다.  
  
 세부 정보를 가져오려는 경우 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 또한 호출 하는 HTML 뷰어를 제공는 **일반 콘텐츠 트리 뷰어**, 반 표 형식에서 발견 된 패턴 및 모델 데이터에 대 한 자세한 정보를 표시 하는 합니다. 자세한 내용은 [Microsoft 일반 콘텐츠 트리 뷰어를 사용하여 모델 찾아보기](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)를 참조하세요.  
  
 이 단원에서는 세 모델에서 결과를 확인합니다. 각 모델 형식은 다른 알고리즘을 기반으로 하며 데이터에 대한 다른 관점을 제공합니다.  
  
-   의사 결정 트리 모델은 자전거 구매에 영향을 주는 요소에 대해 알려줍니다.  
  
-   클러스터링 모델은 자전거 구매 동작 및 기타 선택한 특성을 포함하는 특성별로 고객을 그룹화합니다.  
  
-   Naive Bayes 모델을 통해 다른 특성 간 관계를 탐색할 수 있습니다.  
  
 각 마이닝 모델 뷰어에 대해 자세히 알아보려면 다음 항목을 참조하십시오.  
  
-   [의사 결정 트리 모델 탐색 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [클러스터링 모델 탐색 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [Naive Bayes 모델 탐색 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 수식, 데이터 값 등을 추출하기 위해 세 모델을 모두 **일반 콘텐츠 트리 뷰어**를 사용하여 볼 수 있습니다.  
  
## <a name="first-task-in-lesson"></a>단원의 첫 번째 태스크  
 [의사 결정 트리 모델 탐색 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>이전 단원  
 [3단원: 모델 추가 및 처리](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a>다음 단원  
 [5 단원: 모델 테스트 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>관련 항목  
 [마이닝 모델 뷰어 태스크 및 방법](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [데이터 마이닝 모델 뷰어](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  