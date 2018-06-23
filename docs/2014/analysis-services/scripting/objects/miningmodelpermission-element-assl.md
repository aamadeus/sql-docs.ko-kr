---
title: MiningModelPermission 요소 (ASSL) | Microsoft Docs
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
- MiningModelPermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 42a02eedcc2c054269872e4c0f9523ab63632eda
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36183332"
---
# <a name="miningmodelpermission-element-assl"></a>MiningModelPermission 요소(ASSL)
  사용 권한 멤버를 정의 [역할](role-element-assl.md) 요소 가지는 개별 [MiningModel](miningmodel-element-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<MiningModelPermissions>  
   <MiningModelPermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <AllowBrowsing>...</AllowBrowsing>  
   </MiningModelPermission>  
</MiningModelPermissions>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|[사용 권한](../data-type/permission-data-type-assl.md)|  
|기본값|InclusionThresholdSetting|  
|카디널리티|0-n: 두 번 이상 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[MiningModelPermissions](../collections/miningmodelpermissions-element-assl.md)|  
|자식 요소|[AllowBrowsing](../properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]를 추가 하 여 마이닝 구조에서 드릴스루를 사용할 수는 `AllowDrillthrough` 수 있는 권한을 [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) 컬렉션입니다. 경우 `AllowDrillthrough` 마이닝 구조와 마이닝 모델을 가지는 역할의 모든 멤버가 모두에서 활성화 [AllowDrillThrough 요소 &#40;ASSL&#41; ](../properties/allowdrillthrough-element-assl.md) 모델에 대 한 데이터 마이닝 모델을 쿼리하고 반환할 수 있습니다 다음 구문을 사용 하 여 모델에 포함 되지 않은 구조 열:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 따라서 중요한 데이터나 개인 정보를 보호하려면 필요한 경우에만 마이닝 모델에 대한 `AllowDrillthrough` 권한을 부여해야 합니다. 자세한 내용은 참조 [AllowDrillThrough 요소 &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md)합니다.  
  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.MiningModelPermission>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [개체 &#40;ASSL&#41;](objects-assl.md)  
  
  