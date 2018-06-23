---
title: AggregationFunction 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AggregationFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6c8b28c740e82d661c2664eac576f0e079fd3d46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082356"
---
# <a name="aggregationfunction-element-assl"></a>AggregationFunction 요소(ASSL)
  계정 유형에 사용할 집계 함수를 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Account>  
   ...  
   <AggregationFunction>...</AggregationFunction>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|*Sum*|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[계정](../objects/account-element-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 이 요소의 값은 다음 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*Sum*|측정값이 `Sum` 함수를 사용하여 집계됩니다.|  
|*개수*|측정값이 `Count` 함수를 사용하여 집계됩니다.|  
|*Min*|측정값이 `Min` 함수를 사용하여 집계됩니다.|  
|*Max*|측정값이 `Max` 함수를 사용하여 집계됩니다.|  
|*DistinctCount*|측정값이 `DistinctCount` 함수를 사용하여 집계됩니다.|  
|*없음*|측정값이 집계되지 않습니다.|  
|*AverageOfChildren*|측정값은 자식의 평균을 반환하여 집계됩니다.|  
|*FirstChild*|측정값이 해당 첫 번째 자식 멤버를 반환하여 집계됩니다.|  
|*LastChild*|측정값이 해당 마지막 자식 멤버를 반환하여 집계됩니다.|  
|*FirstNonEmpty*|측정값이 비어 있지 않은 해당 첫 번째 멤버를 반환하여 집계됩니다.|  
|*LastNonEmpty*|측정값이 비어 있지 않은 해당 마지막 멤버를 반환하여 집계됩니다.|  
  
 AMO(Analysis Management Objects) 개체 모델에서 `AggregationFunction`에 대해 허용된 값에 해당하는 열거형은 <xref:Microsoft.AnalysisServices.AggregationFunction>입니다.  
  
## <a name="see-also"></a>관련 항목  
 [요소 계정 &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  