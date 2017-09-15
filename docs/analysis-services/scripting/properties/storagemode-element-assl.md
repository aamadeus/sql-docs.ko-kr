---
title: "StorageMode 요소 (ASSL) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- StorageMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- StorageMode
helpviewer_keywords:
- StorageMode element
ms.assetid: 197e8153-1ab6-43ba-a7e9-ae9be19ac511
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd6ed7838025255015c3a4103689b772dd035771
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="storagemode-element-assl"></a>StorageMode 요소(ASSL)
  부모 요소의 저장소 모드를 결정합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|*MOLAP*|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[Cube 요소 &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/cube-element-assl.md), [요소 &#40; 차원 ASSL &#41; ](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MeasureGroup 요소 &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [요소 &#40; 분할 ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 이 요소의 값은 다음 표에 나열된 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*MOLAP*|부모가 MOLAP(다차원 OLAP) 저장소를 사용합니다.|  
|*ROLAP*|부모가 ROLAP(관계형 OLAP) 저장소를 사용합니다.|  
|*HOLAP*|부모가 HOLAP(하이브리드 OLAP) 저장소를 사용합니다.<br /><br /> 참고:이 값에 대해 올바르지 않습니다 [차원](../../../analysis-services/scripting/objects/dimension-element-assl.md) 부모 요소입니다.|  
|*InMemory*|부모가 IMBI 저장소를 사용합니다.|  
  
 에 대 한 허용된 된 값에 해당 하는 열거형 **StorageMode** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.StorageMode>합니다.  
  
 부모에 해당 하는 요소 **StorageMode** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, 및 <xref:Microsoft.AnalysisServices.Partition>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  