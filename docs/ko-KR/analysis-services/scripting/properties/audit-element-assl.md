---
title: Audit 요소 (ASSL) | Microsoft Docs
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
- Audit Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Audit
helpviewer_keywords:
- Audit element
ms.assetid: 26488119-6490-426d-a4e4-274b5bdffbc2
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cb446a7f795f6b2be1b299832b4188cdcdf9f835
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="audit-element-assl"></a>Audit 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  서버의 성능이 저하되는 경우에도 [Trace](../../../analysis-services/scripting/objects/trace-element-assl.md) 요소가 이벤트를 삭제할 수 없도록 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Trace>  
   ...  
   <Audit>...</Audit>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|Boolean|  
|기본값|**False**|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[추적](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 부모에 해당 하는 요소 **감사** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.Trace>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [Traces 요소 & #40; ASSL & #41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [속성 & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  