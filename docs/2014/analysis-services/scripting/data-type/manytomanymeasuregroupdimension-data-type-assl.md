---
title: ManyToManyMeasureGroupDimension 데이터 형식 (ASSL) | Microsoft Docs
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
- ManyToManyMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ManyToManyMeasureGroupDimension
helpviewer_keywords:
- ManyToManyMeasureGroupDimension data type
ms.assetid: f2b914cb-c817-43ff-9cb4-ac8d326136b5
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 14233f2e39771174b4d1b15acdeafb76bc76f32d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093404"
---
# <a name="manytomanymeasuregroupdimension-data-type-assl"></a>ManyToManyMeasureGroupDimension 데이터 형식(ASSL)
  다 대 다 차원과 측정값 그룹 간의 관계를 나타내는 파생 데이터 형식을 정의합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<ManyToManyMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
   <MeasureGroupID>...</MeasureGroupID>  
   <DefaultMember>...</DefaultMember>  
</ManyToManyMeasureGroupDimension>  
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
|자식 요소|[DefaultMember](../objects/member-element-assl.md), [MeasureGroupID](../properties/id-element-assl.md)|  
|파생 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Analysis Services 스크립팅 언어 XML 데이터 형식 &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  