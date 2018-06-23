---
title: ProactiveCachingBinding 데이터 형식 (ASSL) | Microsoft Docs
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
- ProactiveCachingBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingBinding data type
ms.assetid: 02e6ff2f-2f18-4607-9198-bb46f113f9ac
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 881e593fda57d63a4041e469c48807d434324856
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093618"
---
# <a name="proactivecachingbinding-data-type-assl"></a>ProactiveCachingBinding 데이터 형식(ASSL)
  정보를 나타내는 추상 파생된 데이터 형식을 정의 [ProactiveCaching](../objects/proactivecaching-element-assl.md) 캐시를 다시 작성 해야 하는 데이터 원본 변경 내용이 나 다시 작성 프로세스의 상태에 대 한 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<ProactiveCachingBinding>  
   <!-- ProactiveCachingBinding is an abstract base class with no child elements -->  
</ProactiveCachingBinding>  
```  
  
## <a name="data-type-characteristics"></a>데이터 형식 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|기본 데이터 형식|[바인딩](binding-data-type-assl.md)|  
|파생 데이터 형식|[ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md), [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md), [ProactiveCachingQueryBinding](querybinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>데이터 형식 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|InclusionThresholdSetting|  
|자식 요소|InclusionThresholdSetting|  
|파생 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 에 대 한 자세한 내용은 `Binding` 유형의 Analysis Services Scripting Language (ASSL) 개체 테이블을 포함 하 여는 `Binding` 유형과의 상속 계층 구조 `Binding` 형식 참조 [바인딩 데이터 형식 &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 ASSL의 데이터 바인딩에 대 한 개요를 참조 하세요. [데이터 원본 및 바인딩 &#40;SSAS 다차원&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)합니다.  
  
 Analysis Management Objects (AMO) 개체 모델의 해당 요소는 <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>합니다.  
  
## <a name="inheritance-hierarchy-of-proactivecachingbinding-types"></a>ProactiveCachingBinding 유형의 상속 계층  
 다음 계층에서는 `ProactiveCachingBinding` 유형의 상속을 보여 줍니다.  
  
 [바인딩](binding-data-type-assl.md) 요소  
  
 `ProactiveCachingBinding` 요소  
  
 [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md) 요소  
  
 [ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md) 요소  
  
 [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md) 요소  
  
 [ProactiveCachingQueryBinding](querybinding-data-type-assl.md) 요소  
  
 [ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md) 요소  
  
## <a name="see-also"></a>관련 항목  
 [Analysis Services 스크립팅 언어 XML 데이터 형식 &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  