---
title: WritebackTableCreation 요소 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- WritebackTableCreation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#WritebackTableCreation
- microsoft.xml.analysis.writebacktablecreation
- http://schemas.microsoft.com/analysisservices/2003/engine#WritebackTableCreation
helpviewer_keywords:
- WritebackTableCreation element
ms.assetid: e9579d63-e28c-4d4e-9f4a-21c5da24c276
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9f0edcc8c195cb97aa388fd8d24f384fbc1231c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="writebacktablecreation-element-xmla"></a>WritebackTableCreation 요소(XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  하는 동안 쓰기 저장 테이블을 생성할지 여부를 결정은 [프로세스](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) 작업 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|없음|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[처리](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 Analysis Services 인스턴스에서 개체를 사용할 수 있는 처리 옵션에 대 한 자세한 내용은 참조 [다차원 모델 처리 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)합니다.  
  
 **WritebackTableCreation** 요소의 값은 다음 표에 나열된 문자열 중 하나로 제한됩니다.  
  
|Value|Description|  
|-----------|-----------------|  
|*만들기*|쓰기 저장 테이블이 없는 경우 새 쓰기 저장 테이블을 만듭니다. 쓰기 저장 테이블이 이미 있으면 오류가 발생합니다.|  
|*CreateAlways*|새 쓰기 저장 테이블을 만들고 기존 쓰기 저장 테이블이 있으면 덮어씁니다.|  
|*Useexisting이*|기존 쓰기 저장 테이블이 있으면 사용합니다. 기존 쓰기 저장 테이블이 없으면 오류가 발생합니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  