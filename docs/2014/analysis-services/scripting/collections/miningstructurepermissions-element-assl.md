---
title: MiningStructurePermissions 요소 (ASSL) | Microsoft Docs
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
- MiningStructurePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructurePermissions
helpviewer_keywords:
- MiningStructurePermissions element
ms.assetid: 4db9a9b2-8525-441f-a202-fd253282f540
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a4771102a81dfae1e4a0e62ea1527a5ad6d19199
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36090548"
---
# <a name="miningstructurepermissions-element-assl"></a>MiningStructurePermissions 요소(ASSL)
  에 대 한 권한 컬렉션을 포함 한 [MiningStructure](../objects/miningstructure-element-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<MiningStructure>  
   ...  
   <MiningStructurePermissions>  
      <MiningStructurePermission xsi:type="Permission">...</MiningStructurePermission>  
   </MiningStructurePermissions>  
   ...  
</MiningStructure>  
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
|부모 요소|[MiningStructure](../objects/miningstructure-element-assl.md)|  
|자식 요소|[MiningStructurePermission](../objects/miningstructurepermission-element-assl.md) 형식의 [사용 권한](../data-type/permission-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.MiningStructurePermissionCollection>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Permission 데이터 형식 &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [컬렉션 &#40;ASSL&#41;](collections-assl.md)  
  
  