---
title: E Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- Type Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6480eec04a32ee76ee4cd83f8df096b2d18e879
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="type-element-xmla"></a>Type 요소(XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  수행 될 처리 유형을 결정는 [프로세스](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|없음|  
|카디널리티|1-1: 한 번만 나타나는 필수 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[처리](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 인스턴스의 개체에 사용할 수 있는 옵션을 처리 하는 방법에 대 한 자세한 내용은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], 참조 [다차원 모델 처리 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)합니다.  
  
 값은 **형식** 요소는 다음 표에 나열 된 문자열 중 하나로 제한 합니다.  
  
|Value|Description|  
|-----------|-----------------|  
|*ProcessFull*|영향을 받는 개체에서 모든 데이터를 삭제한 다음 영향을 받는 개체를 처리합니다.|  
|*ProcessAdd*|영향을 받는 개체에 새 데이터를 추가합니다.|  
|*ProcessUpdate*|영향을 받는 개체에서 데이터를 새로 고칩니다.|  
|*ProcessIndexes*|영향을 받는 개체에서 인덱스 및 집계를 만들거나 다시 작성합니다.|  
|*ProcessScriptCache*|큐브가 처리되면 서버에서 MDX 스크립트 캐시가 다시 작성됩니다. 그렇지 않으면 오류가 발생합니다.<br /><br /> **참고** 큐브에만 적용 됩니다.|  
|*ProcessData*|영향을 받는 개체에서만 데이터를 처리합니다.|  
|*ProcessDefault*|영향을 받는 개체의 상태를 검색한 다음 영향을 받는 개체에서 적절한 처리 옵션을 수행하여 해당 개체를 완전히 최적화하고 완전히 처리된 상태로 되돌립니다.|  
|*ProcessClear*|영향을 받는 개체와 모든 관련 개체에서 데이터를 삭제합니다.|  
|*ProcessStructure*|영향을 받는 개체의 구조만 처리합니다.|  
|*ProcessClearStructureOnly*|영향을 받는 개체에서만 데이터를 지웁니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  