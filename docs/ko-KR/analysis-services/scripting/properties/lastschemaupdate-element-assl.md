---
title: LastSchemaUpdate 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- LastSchemaUpdate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- LastSchemaUpdate
helpviewer_keywords:
- LastSchemaUpdate element
ms.assetid: 0634c105-91cc-4882-87be-97ca29a251a6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6d982c24edb3a88239f8636437db4ffa033ea986
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="lastschemaupdate-element-assl"></a>LastSchemaUpdate 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  부모 요소의 읽기 전용 메타데이터 업데이트 타임스탬프를 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Assembly> <!-- or one of the elements that are listed in the Element Relationships table -->  
   ...  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|과 같이 지원되는|  
|기본값|없음|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[어셈블리](../../../analysis-services/scripting/objects/assembly-element-assl.md), [큐브](../../../analysis-services/scripting/objects/cube-element-assl.md), [데이터베이스](../../../analysis-services/scripting/objects/database-element-assl.md), [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md), [차원](../../../analysis-services/scripting/objects/dimension-element-assl.md), [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [파티션](../../../analysis-services/scripting/objects/partition-element-assl.md), [권한](../../../analysis-services/scripting/data-type/permission-data-type-assl.md), [관점](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 **LastSchemaUpdate** 읽기 전용 요소는 포함 **DateTime** 개체에 대 한 메타 데이터의 특정 인스턴스에서 변경 된 시간과 날짜를 나타내는 값 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 부모에 해당 하는 요소 **LastSchemaUpdate** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.Assembly>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.DataSourceView>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MdxScript>, <xref:Microsoft.AnalysisServices.MeasureGroup>, <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningStructure>, <xref:Microsoft.AnalysisServices.Partition>, <xref:Microsoft.AnalysisServices.Permission>, 및 <xref:Microsoft.AnalysisServices.Perspective>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  