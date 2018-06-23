---
title: ClassifiedColumnID 요소 (ASSL) | Microsoft Docs
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
- ClassifiedColumnID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClassifiedColumnID
helpviewer_keywords:
- ClassifiedColumnID element
ms.assetid: c294b9c5-3ac2-4554-8ba8-d9f15d7e85c0
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: aa8223969facc66d126bcba7c7d74a8056e60f00
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093858"
---
# <a name="classifiedcolumnid-element-assl"></a>ClassifiedColumnID 요소(ASSL)
  분류 되는 관련 열의 식별자 (ID)가 포함 된 [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<ClassifiedColumns>  
   <ClassifiedColumnID>...</<ClassifiedColumnID>  
</ClassifiedColumns>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-n: 두 번 이상 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[ClassifiedColumns](../collections/columns-element-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 AMO(Analysis Management Object) 개체 모델에서 `ClassifiedColumns` 컬렉션의 부모에 해당하는 요소는 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>입니다.  
  
## <a name="see-also"></a>관련 항목  
 [요소 콘텐츠 &#40;ASSL&#41;](content-element-assl.md)   
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  