---
title: Expression 요소 (ASSL) | Microsoft Docs
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
- Expression Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Expression
helpviewer_keywords:
- Expression element
ms.assetid: a9491b21-5279-4531-b6a5-9e8022060dd8
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0809c6a5a1c1f896e88d930a79927029265cee0d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="expression-element-assl"></a>Expression 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  부모 요소의 내용을 정의하는 MDX(Multidimensional Expressions) 식을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|문자열|  
|기본값|없음|  
|카디널리티|1-1: 한 번만 나타나는 필수 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md), [StandardAction](../../../analysis-services/scripting/data-type/standardaction-data-type-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 에 대 한는 **CellPermission** 요소는 **식** 요소에서 나타내는 권한에 해당 하는 셀을 식별 하는 MDX 논리 식을 포함는 [액세스](../../../analysis-services/scripting/properties/access-element-assl.md) 요소는 **CellPermission** 요소입니다. 하는 경우의 값은 **식** 에 대 한 요소는 **CellPermission** 요소가 비어는 **CellPermission** 요소는 무시 됩니다.  
  
 에 대 한는 **StandardAction** 요소는 **식** 요소는 동작 내용을 나타내는 MDX 식을 포함 합니다. 하는 경우의 값은 **식** 에 대 한 요소는 **StandardAction** 요소가 비어는 **StandardAction** 요소는 무시 됩니다.  
  
 AMO(Analysis Management Object) 개체 모델에서 부모에 해당하는 요소는 <xref:Microsoft.AnalysisServices.CellPermission> 및 <xref:Microsoft.AnalysisServices.StandardAction>입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  