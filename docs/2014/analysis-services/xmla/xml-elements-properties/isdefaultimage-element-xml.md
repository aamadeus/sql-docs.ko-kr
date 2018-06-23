---
title: IsDefaultImage 요소 (XML) | Microsoft Docs
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
ms.assetid: e29cd137-af82-4753-a681-0d3e705513f3
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: c4d15ea9048c83b1579b688f6848e48deb1dffe4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36088688"
---
# <a name="isdefaultimage-element-xml"></a>IsDefaultImage 요소(XML)
  다른 테이블에 대한 이 관계를 탐색하고 IsDefaultImage 특성이 있는 멤버를 인출하여 이 엔터티의 기본 이미지를 가져올 수 있음을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultImage>...</IsDefaultImage>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|Description|  
|--------------------|-----------------|  
|데이터 형식 및 길이|Boolean|  
|기본값|false|  
|카디널리티|0-1: 한 번만 나타나는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|자식 요소|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Remarks  
 `RelationshipEndVisualizationProperties` 요소의 경우 `IsDefaultImage` 요소는 이 관계의 다른 끝을 탐색하여 이 엔터티의 기본 이미지를 가져올 수 있음을 나타냅니다. 기본값인 `false`는 가져올 기본 이미지가 없음을 나타냅니다.  
  
  