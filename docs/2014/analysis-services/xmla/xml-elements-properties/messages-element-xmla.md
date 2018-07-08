---
title: 메시지를 요소 (XMLA) | Microsoft Docs
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
- Messages Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Messages
- microsoft.xml.analysis.messages
- urn:schemas-microsoft-com:xml-analysis#Messages
helpviewer_keywords:
- Messages element
ms.assetid: 719d15ff-f18b-4c56-80ba-a9114c0b7d8a
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 64895171a352fd981eb811c39be84b4268d5ed19
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36088920"
---
# <a name="messages-element-xmla"></a>Messages 요소(XMLA)
  컬렉션을 포함 [메시지](message-element-xmla.md) 요소에서의 인스턴스로 반환 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 여는 [Discover](../xml-elements-methods-discover.md) 또는 [Execute](../xml-elements-methods-execute.md) 메서드 호출 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|InclusionThresholdSetting|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[결과 집합](../xml-data-types/resultset-data-type-xmla.md)|  
|자식 요소|[메시지](message-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 이 요소는 `Discover` 메서드 호출 또는 `Execute` 메서드 호출 내 단일 XMLA 명령이 성공적으로 완료되었지만 오류 또는 경고가 발생한 경우 사용됩니다. 이러한 경우에는 `Messages` 요소가 추가 되는 [루트](root-element-xmla.md) 하나 이상 포함 된 다른 모든 요소 뒤 요소 `Message` 요소입니다. 각 `Message` 요소가 나타내는 단일 메시지를 오류 또는 경고를 반환한는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스.  
  
## <a name="see-also"></a>관련 항목  
 [속성 &#40;XMLA&#41;](xml-elements-properties.md)  
  
  