---
title: UnknownMemberName 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- UnknownMemberName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- UnknownMemberName
helpviewer_keywords:
- UnknownMemberName element
ms.assetid: 54271336-ea9b-4270-ac3a-9658a5cff77b
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 66bfcca0b35be927a086aa5eb534576a0782d8d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="unknownmembername-element-assl"></a>UnknownMemberName 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  차원의 알 수 없는 멤버에 대한 캡션을 차원의 기본 언어로 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Dimension>  
      ...  
   <UnknownMemberName>...</UnknownMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|문자열|  
|기본값|*알 수 없음*|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[차원](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 **UnknownMemberName** 요소의 값은 알 수 없는 멤버에 사용되는 캡션을 제공합니다. 알 수 없는 멤버의 멤버 ID는 *Dimension*.UnknownMember입니다. 여기서 *Dimension* 은 차원의 고유한 이름이며 변경할 수 없습니다.  
  
 부모에 해당 하는 요소 **UnknownMemberName** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.Dimension>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  