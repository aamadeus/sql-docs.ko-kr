---
title: Cluster (DMX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cluster
dev_langs:
- DMX
helpviewer_keywords:
- Cluster function
ms.assetid: 14b2942a-6dec-4dfa-98a6-697a3c89036a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 65e0d6942d48657f99d5cff3365a80d4853c66d4
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="cluster-dmx"></a>Cluster(DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  입력 사례가 포함되었을 가능성이 가장 높은 클러스터를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>적용 대상  
 이 함수는 기본 데이터 마이닝 모델이 클러스터링을 지원할 때만 사용할 수 있습니다.  
  
## <a name="return-type"></a>반환 형식  
 **클러스터** 함수 매개 변수가 필요 하지 않습니다.  
  
 **클러스터** 함수는 클러스터 이름의 스칼라 값을 반환 합니다. 그러나 다른 함수의 인수로 서이 함수를 사용 하는 경우 간주 해야로 \<클러스터 열 참조 > 합니다.  
  
## <a name="remarks"></a>주의  
 **클러스터** 으로 사용할 수는 `<`클러스터 열 참조`>` 에 대 한는 **PredictHistogram** 함수입니다.  
  
## <a name="examples"></a>예  
 다음 예제에서는 단일 쿼리를 사용 하 여는 [PredictHistogram &#40; DMX &#41;](../dmx/predicthistogram-dmx.md) TM Clustering 마이닝 모델 및는 개별 사례를 각 클러스터에 있는지 확률의 각 클러스터에서 개별 사례의 거리를 반환 하는 함수를 클러스터 합니다.  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>관련 항목:  
 [ClusterProbability &#40; DMX &#41;](../dmx/clusterprobability-dmx.md)   
 [Data Mining Extensions &#40; DMX &#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [함수 &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [일반 예측 함수 &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
