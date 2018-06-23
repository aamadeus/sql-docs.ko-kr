---
title: Usage 요소 (MiningModelColumn) (ASSL) | Microsoft Docs
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
- Usage Element (MiningModelColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Usage
helpviewer_keywords:
- Usage element
ms.assetid: 435a857e-37a9-434e-9de1-354f1ff2993f
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4a4e4c2b11a9a9281f64062390257bf5ddf3145b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36182336"
---
# <a name="usage-element-miningmodelcolumn-assl"></a>Usage 요소(MiningModelColumn)(ASSL)
  설명 어떻게 부모에 연결 된 열 [MiningStructure](../objects/miningstructure-element-assl.md) 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<MiningModelColumn>  
   ...  
   <Usage>...</Usage>  
   ...  
</MiningModelColumn>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 이 요소의 값은 다음 표에 나열된 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*키*|열이 키 열입니다.|  
|*입력*|열이 입력 열입니다.|  
|*Predict*|열이 예측 열입니다.|  
|*PredictOnly*|열이 예측 열 전용입니다.|  
|*없음*|열이 모델에서 사용되지 않습니다. **경고:** Usage 값은 "None", Analysis Services 보내지 않습니다 값 서버에 기본적으로, 따라서 사용 특성은 요청/응답에 포함 되지 않습니다.|  
  
 AMO(Analysis Management Objects) 개체 모델에서 `Usage`에 대해 허용된 값에 해당하는 열거형은 <xref:Microsoft.AnalysisServices.MiningModelColumnUsages>입니다.  
  
## <a name="see-also"></a>관련 항목  
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  