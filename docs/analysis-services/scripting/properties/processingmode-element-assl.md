---
title: "ProcessingMode 요소 (ASSL) | Microsoft Docs"
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
- ProcessingMode Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ProcessingMode
helpviewer_keywords:
- ProcessingMode element
ms.assetid: dff6eeba-f09c-4d8c-ad81-caef76254af0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81a9733cecb0aaea39c52183eae40ec66626f3f9
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="processingmode-element-assl"></a>ProcessingMode 요소(ASSL)
  인스턴스에서 인덱싱 및 집계를 처리 중에 수행할지 아니면 처리 후에 수행할지를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProcessingMode>...</ProcessingMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|*일반*|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[큐브](../../../analysis-services/scripting/objects/cube-element-assl.md), [차원](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [파티션](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 **ProcessingMode** 의 **Cube** 값은 큐브의 기본값을 제공하며 각 파티션에 대해 **ProcessingMode** 를 설정하여 이 기본값을 덮어쓸 수 있습니다.  
  
 이 요소의 값은 다음 표에 나열된 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*일반*|인스턴스가 처리 중에 인덱싱 및 집계를 수행합니다.|  
|*LazyOptimizations*|인스턴스가 처리 후에 인덱싱 및 집계를 수행합니다.|  
  
 에 대 한 허용된 된 값에 해당 하는 열거형 **ProcessingMode** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.ProcessingMode>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  