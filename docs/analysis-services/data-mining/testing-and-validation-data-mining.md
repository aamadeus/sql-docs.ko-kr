---
title: "테스트 및 유효성 검사(데이터 마이닝) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "데이터 마이닝 모델 테스트"
  - "마이닝 모델 비교"
  - "연속 특성 차트"
  - "데이터 마이닝 [Analysis Services], 모델"
  - "차트 [Analysis Services]"
  - "예측 모델링 [Analysis Services]"
  - "마이닝 모델 [Analysis Services], 유효성 검사"
  - "데이터 마이닝 모델 유효성 검사"
  - "마이닝 정확도 보기"
  - "신뢰성 점수 [데이터 마이닝]"
  - "마이닝 정확도 표시"
  - "예측 [Analysis Services], 마이닝 모델 비교"
  - "점수 [데이터 마이닝]"
  - "리프트 차트 [Analysis Services]"
  - "분류 행렬 [Analysis Services]"
  - "CRISP-DM"
  - "정확도 테스트 [데이터 마이닝]"
ms.assetid: 197144f5-21ed-4009-b448-fe412fb3916c
caps.latest.revision: 61
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 61
---
# 테스트 및 유효성 검사(데이터 마이닝)
  유효성 검사는 실제 데이터에 대한 마이닝 모델의 성능을 평가하는 프로세스입니다. 마이닝 모델을 프로덕션 환경으로 배포하기 전에 품질과 특징을 이해하여 마이닝 모델의 유효성을 검사하는 것이 중요합니다.  
  
 이 섹션에서는 모델 품질과 관련된 몇 가지 기본 개념을 소개하고 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 제공된 모델 유효성 검사를 위한 전략을 설명합니다. 대규모 데이터 마이닝 프로세스에서 모델 유효성 검사를 수행하는 방법에 대한 개요는 [데이터 마이닝 솔루션](../../analysis-services/data-mining/data-mining-solutions.md)을 참조하세요.  
  
## 데이터 마이닝 모델의 테스트 및 유효성 검사 방법  
 데이터 마이닝 모델의 품질과 특징을 평가하는 데에는 여러 가지 방법이 있습니다.  
  
-   통계 유효성의 다양한 측정값을 사용하여 데이터나 모델에 문제가 있는지 여부를 확인할 수 있습니다.  
  
-   데이터를 학습 집합과 테스트 집합으로 구분하여 예측의 정확도를 테스트할 수 있습니다.  
  
-   비즈니스 전문가에게 데이터 마이닝 모델의 결과를 검토하도록 요청하여 검색된 패턴이 대상 비즈니스 시나리오에서 의미가 있는지 여부를 결정할 수 있습니다.  
  
 이러한 모든 방법은 데이터 마이닝 방법에서 유용하며 특정 문제를 해결하기 위한 모델을 생성, 테스트 및 구체화하면서 반복적으로 사용됩니다. 모델이 적당하거나 데이터가 충분하다고 판단하는 기준으로 삼을 수 있는 하나의 포괄적인 규칙은 없습니다.  
  
## 데이터 마이닝 모델의 유효성 검사를 위한 기준 정의  
 데이터 마이닝의 측정값은 일반적으로 정확도, 안정성 및 유용성의 범주로 나누어집니다.  
  
 *정확도* 는 모델에서 제공된 데이터의 특성과 결과 간 상관 관계를 나타내는 측정값입니다. 다양한 정확도 측정값이 있지만 모든 정확도 측정값은 사용되는 데이터에 따라 달라집니다. 실제로는 값이 없거나 근사값일 수 있으며 여러 프로세스에 의해 데이터가 변경되었을 수 있습니다. 특히 탐색 및 개발 단계에서 데이터의 특징이 비교적 균일한 경우 데이터에서 오류가 일정 정도 발생하도록 허용할 수 있습니다. 예를 들어 과거 판매량을 기반으로 특정 매장의 판매량을 예측하는 모델은 해당 매장에서 계속 잘못된 회계 방법을 사용한 경우에도 상관 관계가 높고 매우 정확할 수 있습니다. 따라서 정확도 측정은 안정성 평가에 따라 균형을 맞춰야 합니다.  
  
 *안정성* 은 다른 데이터 집합에 대한 데이터 마이닝 모델의 성능을 평가합니다. 제공된 테스트 데이터와 상관없이 동일한 유형의 예측을 생성하거나 동일한 일반적인 종류의 패턴을 찾는 경우 데이터 마이닝 모델은 안정적입니다. 예를 들어 잘못된 회계 방법을 사용한 매장에 대해 생성하는 모델은 다른 매장에도 적용할 수 있을 정도로 일반화될 수 없으므로 안정적이지 않습니다.  
  
 *유용성* 에는 모델이 유용한 정보를 제공하는지 여부를 알려 주는 다양한 메트릭이 포함됩니다. 예를 들어 매장 위치와 판매량 간 상관 관계를 찾는 데이터 마이닝 모델은 정확하면서 안정적일 수 있지만 동일한 위치에 있는 다른 매장을 추가하여 결과를 일반화할 수 없으므로 유용하지 않을 수 있습니다. 또한 이 모델로는 특정 위치에서 판매량이 왜 더 많은가라는 기본적인 비즈니스 질문에 대한 답을 얻을 수 없습니다. 성공적으로 보이는 모델이 데이터의 교차 상관 관계를 기반으로 하고 있기 때문에 실제로는 의미가 없을 수도 있습니다.  
  
## 마이닝 모델의 테스트 및 유효성 검사 도구  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 데이터 마이닝 솔루션의 유효성을 여러 방법으로 검사하여 데이터 마이닝 테스트 방법의 모든 단계를 지원합니다.  
  
-   데이터를 학습 및 테스트 집합으로 분할합니다.  
  
-   모델을 필터링하여 동일한 원본 데이터의 서로 다른 조합을 학습하고 테스트할 수 있습니다.  
  
-   *리프트* 및 *이득*을 측정합니다. *리프트 차트* 는 데이터 마이닝 모델을 임의 추측과 비교할 때 데이터 마이닝 모델 사용에서 얻는 향상률을 시각화하는 방법입니다.  
  
-   데이터 집합의 *교차 유효성 검사*를 수행합니다.  
  
-   *분류 행렬*을 생성합니다. 이러한 차트에서는 모델이 대상 값을 정확하게 예측하는 정도를 쉽게 빠르고 측정할 수 있도록 올바른 추측과 잘못된 추측을 테이블로 정렬합니다.  
  
-   회귀 수식에 맞는지 평가할 수 있는 *산점도* 를 만듭니다.  
  
-   마이닝 모델 사용과 재무 이익 또는 비용을 연결하는 *수익 차트* 를 만들어 권장 구성의 값을 평가할 수 있습니다.  
  
 이러한 메트릭의 목적은 데이터 마이닝 모델이 비즈니스 질문에 대한 해답을 제공하는지 여부에 대한 질문에 응답하는 것이 아닙니다. 그보다는 예측 분석을 위해 데이터의 안정성을 평가하고 개발 프로세스에서 특정 반복을 사용할지 여부를 결정하도록 돕는 데 사용할 수 있는 객관적인 측정값을 제공하는 것입니다.  
  
 이 섹션의 항목에서는 각 방법의 개요를 제공하고 SQL Server 데이터 마이닝을 사용하여 빌드하는 모델의 정확도를 측정하는 프로세스를 안내합니다.  
  
### 관련 항목  
  
|항목|링크|  
|------------|-----------|  
|마법사 또는 DMX 명령을 사용하여 테스트 데이터 집합을 설정하는 방법 배우기|[데이터 집합 학습 및 테스트](../../analysis-services/data-mining/training-and-testing-data-sets.md)|  
|마이닝 구조에서 데이터의 배포 및 대표성을 테스트하는 방법 배우기|[교차 유효성 검사&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)|  
|[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]에서 제공하는 정확도 차트 종류에 대해 배우기.|[리프트 차트&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)<br /><br /> [수익 차트&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/profit-chart-analysis-services-data-mining.md)<br /><br /> [산점도&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/scatter-plot-analysis-services-data-mining.md)|  
|여러 참과 거짓의 긍정 및 부정을 평가할 수 있는 분류 행렬(혼동 행렬이라고도 함)을 만드는 방법 배우기.|[분류표&#40;Analysis Services - 데이터 마이닝&#41;](../../analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)|  
  
## 관련 항목:  
 [데이터 마이닝 도구](../../analysis-services/data-mining/data-mining-tools.md)   
 [데이터 마이닝 솔루션](../../analysis-services/data-mining/data-mining-solutions.md)   
 [테스트 및 유효성 검사 태스크 및 방법&#40;데이터 마이닝&#41;](../../analysis-services/data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  