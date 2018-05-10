---
title: RestrictionList 요소 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- RestrictionList Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c3308d4e65fd502c5ff4195477ed114eaedb0acf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="restrictionlist-element-xmla"></a>RestrictionList 요소(XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) 메서드에서 사용되는 제한 열 및 값의 컬렉션을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
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
|부모 요소|[제한 사항](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|자식 요소|제한 열 및 값(주의 참조)|  
  
## <a name="remarks"></a>주의  
 **RestrictionList** 요소에는 **Discover** 메서드에서 반환한 데이터를 필터링할 수 있는 제한 열의 컬렉션이 포함되어 있습니다. **RestrictionList** 요소의 각 제한 열은 별도의 XML 요소로 정의됩니다. 제한 열의 값은 XML 요소에 포함된 데이터이고, 제한 열의 이름은 XML 요소의 이름과 일치합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  