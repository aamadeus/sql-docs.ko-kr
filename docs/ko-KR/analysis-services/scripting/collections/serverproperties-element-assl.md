---
title: ServerProperties 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
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
- ServerProperties Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ServerProperties
helpviewer_keywords:
- ServerProperties element
ms.assetid: 8ccbef3f-1388-4fa3-b0a4-c89b89f09056
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d5c331700507e6959e11b55586280ff9843eacf7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="serverproperties-element-assl"></a>ServerProperties 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  컬렉션을 포함 [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md) 와 관련 된 요소는 [서버](../../../analysis-services/scripting/objects/server-element-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Server>  
      ...  
   <ServerProperties>  
      <ServerProperty>...</ServerProperty>  
   </ServerProperties>  
   ...  
</Server>  
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
|부모 요소|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|자식 요소|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
  
## <a name="remarks"></a>주의  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.ServerPropertyCollection>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [컬렉션 & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  