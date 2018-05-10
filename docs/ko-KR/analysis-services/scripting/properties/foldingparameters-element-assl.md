---
title: FoldingParameters 요소 (ASSL) | Microsoft Docs
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
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- FoldIndex
- FoldCount
- MaxCases
- FoldingParameters
- FoldTargetAttribute
helpviewer_keywords:
- FoldingParameters element
ms.assetid: 5f5c5a3e-4aed-48fb-bca5-e67f421bef2f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8d536d67738872ba070217d934a1b47be7857398
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="foldingparameters-element-assl"></a>FoldingParameters 요소(ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 서버에서 마이닝 모델의 교차 유효성 검사를 수행할 때 사용하는 매개 변수를 지정합니다.  
  
> [!NOTE]  
>  이러한 매개 변수는 내부에서 사용하기 위한 것입니다. 여기에 제공된 정보는 참조용일 뿐입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<MiningModel>  
   ...  
   <ddl100_100:FoldingParameters>...  
      <ddl100_100:FoldIndex>...</ddl100_100:FoldIndex>  
      <ddl100_100:FoldCount>...</ddl100_100:FoldCount>  
      <ddl100_100:MaxCases>...</ddl100_100:MAxCases>  
      <ddl100_100:FoldTargetAttribute>...</ddl100_100:FoldTargetAttribute  
...</ddl100_100:FoldingParameters>  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|*FoldIndex*|교차 유효성 검사에 사용되는 파티션의 시작 위치를 나타내는 정수입니다.|  
|*FoldCount*|교차 유효성 검사 후 모델에 있는 파티션 수를 나타내는 정수입니다.|  
|*MaxCases*|교차 유효성 검사에 사용되는 모델 사례 수를 나타내는 정수입니다.<br /><br /> 값 0은 모든 사례가 사용됨을 나타냅니다.|  
|*FoldTargetAttribute*|예측 가능한 특성이 포함된 모델 열의 ID를 나타내는 문자열입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|자식 요소|*FoldIndex*<br /><br /> *FoldCount*<br /><br /> *MaxCases*<br /><br /> *FoldTargetAttribute*|  
  
## <a name="remarks"></a>주의  
 이러한 속성은 내부에서 사용하기 위한 것이며 DDL 문에서 사용할 수 없습니다.  
  
 교차 유효성 검사를 사용 하는 방법에 대 한 내용은 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], 참조 [교차 유효성 검사 보고서의 측정값](../../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)합니다.  
  
 사용 하 여 교차 유효성 검사를 수행 하는 방법에 대 한 내용은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 저장된 프로시저 참조 [Stored Procedures &#40;Analysis Services-데이터 마이닝&#41;](../../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [속성 & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  