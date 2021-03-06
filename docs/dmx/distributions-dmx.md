---
title: 분포 (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e4ffd21a2b507e03af6534296715528d83aac0f6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992035"
---
# <a name="distributions-dmx"></a>배포(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], 마이닝 구조에 마이닝 모델을 만들 때 알고리즘에서 이러한 열에 있는 데이터를 처리 하는 방법에 영향을 줄에서 열의 콘텐츠를 정의할 수 있습니다. 이렇게 하면 공통적인 값 배포가 열에 포함되어 있을 경우 모델을 처리하기 전에 몇몇 알고리즘에서 연속 열 배포를 정의하는 데 도움이 됩니다. 배포를 정의하지 않으면 알고리즘이 데이터를 해석하는 데 사용할 정보가 더 줄어듭니다. 따라서 마이닝 모델에서 얻는 예측의 정확도가 배포를 정의했을 경우보다 낮아질 수 있습니다.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] 데이터 마이닝 알고리즘에서는 다음 배포 유형을 지원합니다.  
  
 **보통**  
 연속 열에 대한 값은 정규 가우스 분포로 된 히스토그램을 형성합니다.  
  
 **Log Normal**  
 연속 열에 대한 값은 값 로그가 정상적으로 분포된 히스토그램을 형성합니다.  
  
 **UNIFORM**  
 연속 열에 대한 값은 모든 값이 균일한 평탄 곡선을 형성합니다.  
  
 에 대 한 자세한 내용은 [!INCLUDE[msCoName](../includes/msconame-md.md)] 데이터 마이닝 알고리즘을 참조 하세요 [데이터 마이닝 알고리즘 &#40;Analysis Services-Data Mining&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)합니다. 타사 알고리즘 공급자가 추가 배포 유형을 지원할 수 있습니다. 지 원하는 배포 알고리즘 유형을 확인 하려면을 사용 합니다 **SUPPORTED_DISTRIBUTION_FLAGS** 스키마 행 집합입니다.  
  
 배포 유형에 대 한 자세한 내용은 참조 하세요. [열 배포 &#40;데이터 마이닝&#41;](../analysis-services/data-mining/column-distributions-data-mining.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [콘텐츠 형식 &#40;데이터 마이닝&#41;](../analysis-services/data-mining/content-types-data-mining.md)   
 [Data Mining Extensions &#40;DMX&#41; 참조](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; 구문 요소](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Data Mining Extensions &#40;DMX&#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; 연산자 참조](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40;DMX&#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40;DMX&#41; 구문 표기 규칙](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [일반 예측 함수 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [구조 및 사용법 DMX 예측 쿼리](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX Select 문 이해](../dmx/understanding-the-dmx-select-statement.md)  
  
  
