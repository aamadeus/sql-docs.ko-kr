---
title: E Element (Action) (ASSL) | Microsoft Docs
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
- Type Element (Action)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d71abdd26cea5fa03c8e70f882f893878a70969a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091359"
---
# <a name="type-element-action-assl"></a>Type 요소(Action)(ASSL)
  유형을 포함 된 [동작](../objects/action-element-assl.md) 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|String(열거형)|  
|기본값|InclusionThresholdSetting|  
|카디널리티|1-1: 한 번만 나타나는 필수 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[동작](../objects/action-element-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 이 요소의 값은 다음 표에 나열된 문자열 중 하나로 제한됩니다.  
  
|값|Description|  
|-----------|-----------------|  
|*Url*|가변 페이지를 인터넷 브라우저로 표시합니다.|  
|*Html*|인터넷 브라우저에서 HTML 스크립트를 실행합니다.|  
|*문*|OLE DB 명령을 실행합니다.|  
|*드릴스루*|드릴스루에 대한 행 집합을 검색합니다.<br /><br /> 이 값은 동일 *행 집합* 및 드릴스루 동작을 식별 합니다. 만 사용할 수 인 작업에 사용할 [TargetType](targettype-element-assl.md) 값으로 설정 되어 *셀*합니다.|  
|*데이터 집합*|데이터 집합을 검색합니다.|  
|*행 집합*|행 집합을 검색합니다.|  
|*명령줄*|명령 프롬프트에서 명령을 실행합니다.|  
|*소유*|이 표의 앞에 나열된 것과는 다른 인터페이스를 사용하여 작업을 수행합니다.|  
|*보고서*|가변 페이지를 인터넷 브라우저로 표시합니다.<br /><br /> 이 값은 동일 *Url* 보고서 동작을 식별 하 고 있습니다.|  
  
 부모에 해당 하는 요소 `Type` Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.Action>합니다.  
  
## <a name="see-also"></a>관련 항목  
 [DrillThroughAction 데이터 형식 &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [ReportAction 데이터 형식 &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [속성 &#40;ASSL&#41;](properties-assl.md)  
  
  