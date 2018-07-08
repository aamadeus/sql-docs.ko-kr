---
title: DiscretizationBucketCount 요소 (ASSL) | Microsoft Docs
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
- DiscretizationBucketCount Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationBucketCount
helpviewer_keywords:
- DiscretizationBucketCount element
ms.assetid: 551a73ae-59e1-4079-a2d9-988df96b5e07
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e3609dcc1a5a926e4b9ecc46736a90d6620ec068
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186172"
---
# <a name="discretizationbucketcount-element-assl"></a>DiscretizationBucketCount 요소(ASSL)
  불연속화할 버킷의 수를 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|정수|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `DiscretizationBucketCount` 요소의 값은 `DimensionAttribute` 또는 `ScalarMiningStructureColumn`에 대한 값이 불연속화되거나 특정 그룹 집합으로 구성될 때 생성되는 그룹 또는 "버킷"의 수를 결정합니다. 요소를 지정 하지 않으면 또는 요소의 값에 대해 0을 지정 하면 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 경우 적절 한 개수의 불연속화 방법에 따라 그룹을 만듭니다. 불연속화 방법에 대 한 자세한 내용은 참조 [분할 방법 &#40;데이터 마이닝&#41;](../../data-mining/discretization-methods-data-mining.md)합니다.  
  
 부모에 해당 하는 요소 `DiscretizationBucketCount` Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.DimensionAttribute> 및 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [DiscretizationMethod 요소 &#40;ASSL&#41;](discretizationmethod-element-assl.md)   
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  