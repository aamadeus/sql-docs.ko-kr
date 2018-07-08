---
title: NamingTemplateTranslation 요소 (ASSL) | Microsoft Docs
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
- NamingTemplateTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dc6c6689f4028c0983267a38435c76e7258768a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180594"
---
# <a name="namingtemplatetranslation-element-assl"></a>NamingTemplateTranslation 요소(ASSL)
  지역화 된 번역을 제공 된 [NamingTemplate](../properties/namingtemplate-element-assl.md) 요소는 부모에 대 한 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) 데이터 형식입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|[번역](translation-element-assl.md)|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[NamingTemplateTranslations](../collections/translations-element-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 값은 `NamingTemplateTranslation` 요소 부모 특성에만 사용 됩니다 (의 값 즉,는 [사용량](../properties/usage-element-dimensionattribute-assl.md) 의 요소는 `DimensionAttribute` 로 설정 됩니다 *부모*) 버전을 저장 하 번역 된 `NamingTemplate` 지정된 된 언어에 대 한 값입니다.  
  
 부모에 해당 하는 요소 `NamingTemplateTranslations` Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.DimensionAttribute>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [NamingTemplate 요소 &#40;ASSL&#41;](../properties/namingtemplate-element-assl.md)   
 [개체 &#40;ASSL&#41;](objects-assl.md)  
  
  