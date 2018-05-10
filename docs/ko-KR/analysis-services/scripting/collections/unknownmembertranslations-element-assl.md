---
title: UnknownMemberTranslations 요소 (ASSL) | Microsoft Docs
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
- UnknownMemberTranslations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- UnknownMemberTranslations
helpviewer_keywords:
- UnknownMemberTranslations element
ms.assetid: 72920843-2d43-4ff4-b38e-19c9a7451cb2
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 49bb3e60fef358cadce65fe8cdd61ba44fe3de32
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="unknownmembertranslations-element-assl"></a>UnknownMemberTranslations 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  캡션에 대 한 번역의 컬렉션을 포함 된 [UnknownMember](../../../analysis-services/scripting/properties/unknownmember-element-assl.md) 차원의 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Dimension>  
   ...  
   <UnknownMemberTranslations>  
      <UnknownMemberTranslation xsi:type="Translation ">...</UnknownMemberTranslation>  
      </UnknownMemberTranslations>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|없음|  
|기본값|없음|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[차원](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|자식 요소|[UnknownMemberTranslation](../../../analysis-services/scripting/objects/unknownmembertranslation-element-assl.md) 형식의 [변환](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)|  
  
## <a name="remarks"></a>주의  
 부모에 해당 하는 요소 **UnknownMemberTranslations** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.Dimension>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [Translation 데이터 형식 &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/translation-data-type-assl.md)   
 [컬렉션 & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  