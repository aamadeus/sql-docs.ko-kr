---
title: EmptyResult 데이터 형식 (XMLA) | Microsoft Docs
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
- EmptyResult Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EmptyResult
- olapxmla_EmptyResult
- urn:schemas-microsoft-com:xml-analysis#EmptyResult
helpviewer_keywords:
- EmptyResult data type
ms.assetid: 63818123-acbb-4220-9d60-1aa20a7326a1
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bba727b2d7d612fa59c99665bd16d936da137fb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185481"
---
# <a name="emptyresult-data-type-xmla"></a>EmptyResult 데이터 형식(XMLA)
  나타내는 파생된 데이터 형식을 정의 [루트](../xml-elements-properties/root-element-xmla.md) 요소에서 데이터를 반환 하지 않는 한 [Discover](../xml-elements-methods-discover.md) 또는 [Execute](../xml-elements-methods-execute.md) 메서드를 호출 합니다.  
  
 **네임스페이스** urn:schemas-microsoft-com:xml-analysis:empty  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>데이터 형식 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|기본 데이터 형식|[결과 집합](resultset-data-type-xmla.md)|  
|파생 데이터 형식|InclusionThresholdSetting|  
  
## <a name="data-type-relationships"></a>데이터 형식 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|InclusionThresholdSetting|  
|자식 요소|InclusionThresholdSetting|  
|파생 요소|[root](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 일부 XMLA(XML for Analysis) 명령은 결과를 반환하지 않거나 오류로 인해 결과를 반환하지 못할 수 있습니다. 결과를 반환하지 않는 XMLA 명령은 `EmptyResult` 요소의 네임스페이스인 `root` 데이터 형식을 반환합니다.  
  
## <a name="example"></a>예제  
 다음 예는 빈 결과에 대해 반환되는 `root` 요소를 보여 줍니다.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>관련 항목  
 [XML 데이터 형식 &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  