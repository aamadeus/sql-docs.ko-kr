---
title: "CubeAttribute 데이터 형식 (ASSL) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubeAttribute Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeAttribute
helpviewer_keywords:
- CubeAttribute data type
ms.assetid: 114ffb44-460b-4971-b31b-dd844e960b81
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c04b5602de94ac46b736ebfc878760174ced5a8d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="cubeattribute-data-type-assl"></a>CubeAttribute 데이터 형식(ASSL)
  와 연결 된 특성을 나타내는 기본 데이터 형식을 정의 [큐브](../../../analysis-services/scripting/objects/cube-element-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<CubeAttribute>  
   <AttributeID>...</AttributeID>  
   <AggregationUsage>...</AggregationUsage>  
   <AttributeHierarchyOptimizedState>...</AttributeHierarchyOptimizedState>  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   <Annotations>...</Annotations>  
</CubeAttribute>  
```  
  
## <a name="data-type-characteristics"></a>데이터 형식 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|기본 데이터 형식|없음|  
|파생 데이터 형식|없음|  
  
## <a name="data-type-relationships"></a>데이터 형식 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|없음|  
|자식 요소|[AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md), [주석](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeHierarchyEnabled](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md), [AttributeHierarchyOptimizedState](../../../analysis-services/scripting/properties/attributehierarchyoptimizedstate-element-assl.md), [ AttributeHierarchyVisible](../../../analysis-services/scripting/properties/attributehierarchyvisible-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)|  
|파생 요소|[특성](../../../analysis-services/scripting/objects/attribute-element-assl.md) ([특성](../../../analysis-services/scripting/collections/attributes-element-assl.md) 컬렉션 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md))|  
  
## <a name="remarks"></a>주의  
 *AttributeHierarchyOptimizedState* DeploymentMode 구성 속성 값이 1 또는 2에서 서비스를 실행 하는 경우에 요소가 지원 되지 않습니다 (SharePoint 또는 테이블 형식 모드를 실행 하는 데 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 및 테이블 형식 모델 데이터베이스에 해당)입니다.  
  
 *AtttributeHierarchyEnabled*속성이 FALSE로 설정되고 인스턴스가 DeploymentMode 1 또는 2(SharePoint 또는 테이블 형식 서버 모드)에서 실행되는 경우 특성을 계층 구조 수준으로 추가할 수 없습니다.  
  
 특성은 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md) 에 명시적으로 포함 되지 않은 요소는 [특성](../../../analysis-services/scripting/collections/attributes-element-assl.md) 기본 값이 할당을 사용 하 여 컬렉션의 일부가 될 컬렉션입니다. 컬렉션에 추가 된 특성은 특성에서 반환 될 수는 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) 메서드.  
  
 [AggregationUsage](../../../analysis-services/scripting/properties/aggregationusage-element-assl.md) 요소 컨트롤 어떻게 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 자동으로 특성에 대 한 집계를 디자인 합니다. **AggregationUsage** 요소는 큐브에 대해 수동으로 생성되는 집계를 제한하지 않습니다.  
  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.CubeAttribute>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [스크립팅 언어 XML 데이터 형식 &#40; analysis Services ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  