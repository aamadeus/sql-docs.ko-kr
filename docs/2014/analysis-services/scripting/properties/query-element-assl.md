---
title: 쿼리 요소 (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Query Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Query element
ms.assetid: 832c3337-de6d-43b2-8f1c-75bdba76539b
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fac4774f6e8a2694ee79691a84f3333ab1a4226b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091609"
---
# <a name="query-element-assl"></a>Query 요소(ASSL)
  알림을 위해 실행할 쿼리의 텍스트를 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<QueryNotification>  
   <Query>...</Query>  
</QueryNotification>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String|  
|기본값|InclusionThresholdSetting|  
|카디널리티|1-1: 한 번만 나타나는 필수 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[QueryNotification](../objects/querynotification-element-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 부모에 해당 하는 요소 `Query` Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.QueryNotification>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [ProactiveCachingQueryBinding 데이터 형식 &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  