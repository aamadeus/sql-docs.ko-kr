---
title: return 요소 (XMLA) | Microsoft Docs
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
- return Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1a4468ce3d4b14ff9cd9db7c9373083aad75d3eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36078636"
---
# <a name="return-element-xmla"></a>return 요소(XMLA)
  반환 된 정보를 포함 한 [DiscoverResponse](../xml-elements-objects-discoverresponse.md) 요소에 대 한 응답에는 [Discover](../xml-elements-methods-discover.md) 메서드 호출 또는 [ExecuteResponse](../xml-elements-objects-executeresponse.md) 요소는 에대한응답에서[Execute](../xml-elements-methods-execute.md) 메서드를 호출 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|InclusionThresholdSetting|  
|기본값|InclusionThresholdSetting|  
|카디널리티|1-1: 한 번만 나타나는 필수 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[DiscoverResponse](../xml-elements-objects-discoverresponse.md), [ExecuteResponse](../xml-elements-objects-executeresponse.md)|  
|상위:[DiscoverResponse](../xml-elements-objects-discoverresponse.md)|자식: <br />                        [root](root-element-xmla.md)|  
|상위 항목: <br />                        [ExecuteResponse](../xml-elements-objects-executeresponse.md)|자식: [루트](root-element-xmla.md) 또는 [결과](results-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 `return` 요소는 `Discover` 및 `Execute` 메서드가 반환하는 데이터를 포함합니다. 일반적으로 `return` 요소는 성공적인 `root` 또는 `Discover` 메서드 호출에 의해 반환되는 데이터, 또는 실패한 메서드 호출에 의해 반환되는 XMLA(XML for Analysis) 예외를 포함하는 하나의 `Execute` 요소를 포함합니다. `Execute` 메서드가 여러 작업을 수행하는 `Batch` 명령을 포함한 경우 `return` 요소는 `results` 요소를 포함하며, 이 요소는 `root` 명령에 의해 실행되는 성공 또는 실패한 각 명령에 대해 하나의 `Batch` 요소를 포함합니다.   
  
## <a name="see-also"></a>관련 항목  
 [속성 &#40;XMLA&#41;](xml-elements-properties.md)  
  
  