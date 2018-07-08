---
title: ReferenceMeasureGroupDimension 데이터 형식 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ReferenceMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReferenceMeasureGroupDimension
helpviewer_keywords:
- ReferenceMeasureGroupDimension data type
ms.assetid: 81f7b83e-71a3-4eab-b291-0500d05903dc
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e8e2134f14ad34f14cbf1b7f6a2858fe14485bbe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159314"
---
# <a name="referencemeasuregroupdimension-data-type-assl"></a>ReferenceMeasureGroupDimension 데이터 형식(ASSL)
  중간 차원을 통해 팩트 테이블과 간접적으로 관련된 차원을 나타내는 파생 데이터 형식을 정의합니다. 예를 들어 Sales 측정값 그룹은 Geography 차원을 참조할 수 있으며 이 차원은 Customer 차원을 통해 관련됩니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<ReferenceMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
      <IntermediateCubeDimensionID>...</IntermediateCubeDimensionID>  
   <IntermediateGranularityAttributeID>...</IntermediateGranularityAttributeID>  
   <Materialization>...</Materialization>  
</ReferenceMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>데이터 형식 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|기본 데이터 형식|[MeasureGroupDimension](dimension-data-type-assl.md)|  
|파생 데이터 형식|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>데이터 형식 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|InclusionThresholdSetting|  
|자식 요소|[IntermediateCubeDimensionID](../properties/id-element-assl.md)하십시오 [IntermediateGranularityAttributeID](../properties/attributeid-element-assl.md), [구체화](../properties/materialization-element-assl.md)|  
|파생 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Analysis Services Scripting Language XML 데이터 형식 &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  