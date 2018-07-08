---
title: DefaultMember 요소 (ASSL) | Microsoft Docs
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
- DefaultMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultMember
helpviewer_keywords:
- DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 71b8b2ecd1d5cd46ea50cceebe2a0105d9b7311f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091602"
---
# <a name="defaultmember-element-assl"></a>DefaultMember 요소(ASSL)
  부모 요소의 기본 멤버를 식별하는 MDX(Multidimensional Expressions) 식을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<AttributePermission> <!-- or DimensionAttribute, ManyToManyMeasureGroupDimension, PerspectiveAttribute -->  
      ...  
   <DefaultMember>...</DefaultMember>  
      ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[AttributePermission](../objects/attributepermission-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md), [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `DefaultMember` 요소는 부모 요소의 기본 멤버를 정의합니다. 경우 `DefaultMember` 지정 되지 않았거나 빈 문자열로 설정 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 기본 멤버로 사용할 멤버를 선택 합니다.  
  
 `ManyToManyMeasureGroupDimension` 요소의 경우 `DefaultMember` 요소는 `CubeDimensionID`의 `ManyToManyMeasureGroupDimension` 요소에서 식별되는 차원 멤버를 지정하는 MDX 식을 포함합니다. MDX 식을 비슷합니다는 [StrToMember](/sql/mdx/strtomember-mdx) MDX 또는 사용자 정의 함수를 포함할 수 없습니다 한다는 점에서 MDX 제한 된 키워드와 함께 작동 합니다.  
  
 기본 멤버에 대한 자세한 내용은 [기본 멤버 정의](../../multidimensional-models/attribute-properties-define-a-default-member.md)를 참조하세요.  
  
 AMO(Analysis Management Objects) 개체 모델에서 `DefaultMember`의 부모에 해당하는 요소는 <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute> 및 <xref:Microsoft.AnalysisServices.PerspectiveAttribute>입니다.  
  
## <a name="see-also"></a>관련 항목  
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  