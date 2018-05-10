---
title: ADO MD 개체 수준 | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02a1a7e433c13c52db6c1e9112437470769c76be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="level-object-ado-md"></a>수준 개체 (ADO MD)
계층에서 순위가 같은 멤버 집합이 포함 되어 있습니다.  
  
## <a name="remarks"></a>주의  
 컬렉션과의 속성을 사용 하 여 한 **수준** 개체를 다음을 수행할 수 있습니다.  
  
-   식별 된 **수준** 와 [이름](../../../ado/reference/ado-md-api/name-property-ado-md.md) 및 [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) 속성입니다.  
  
-   표시할 때 사용할 문자열을 반환 하는 **수준** 와 [캡션](../../../ado/reference/ado-md-api/caption-property-ado-md.md) 속성입니다.  
  
-   설명 하는 의미 있는 문자열을 반환 된 **수준** 와 [설명](../../../ado/reference/ado-md-api/description-property-ado-md.md) 속성입니다.  
  
-   반환 된 [멤버](../../../ado/reference/ado-md-api/member-object-ado-md.md) 구성 하는 개체는 **수준** 와 [멤버](../../../ado/reference/ado-md-api/members-collection-ado-md.md) 컬렉션입니다.  
  
-   루트에서 수준 수를 반환 합니다.는 **수준** 와 [깊이](../../../ado/reference/ado-md-api/depth-property-ado-md.md) 속성입니다.  
  
-   표준 ADO를 사용 하 여 [속성](../../../ado/reference/ado-api/properties-collection-ado.md) 컬렉션에 대 한 추가 정보를 가져올 수는 **수준** 개체입니다.  
  
 **속성** 컬렉션 공급자를 제공 하는 속성을 포함 합니다. 다음 표에서 사용할 수 있는 속성을 나열 합니다. 실제 속성 목록은 공급자의 구현에 따라 달라질 수 있습니다. 사용 가능한 속성의 전체 목록은 대 한 공급자에 대 한 설명서를 참조 하십시오.  
  
|이름|Description|  
|----------|-----------------|  
|CatalogName|이 큐브 속해 있는 카탈로그의 이름입니다.|  
|CubeName|큐브의 이름입니다.|  
|Description|수준의 의미 있는 설명입니다.|  
|DimensionUniqueName|모호 하지 않은 이름을 [차원](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)합니다.|  
|HierarchyUniqueName|계층의 명확한 이름입니다.|  
|LevelCaption|레이블 또는 수준에 연결 된 캡션입니다.|  
|LevelCardinality|수준의 멤버 수입니다.|  
|LevelGUID|GUID는 수준입니다.|  
|LevelName|수준의 이름입니다.|  
|LevelNumber|계층의 루트 수준 사이의 거리입니다.|  
|LevelType|형식 수준입니다.|  
|LevelUniqueName|수준의 모호 하지 않은 이름입니다.|  
|SchemaName|이 큐브 속해 있는 스키마의 이름입니다.|  
  
 이 섹션에는 다음 항목 포함 되어 있습니다.  
  
-   [속성, 메서드 및 이벤트](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>관련 항목:  
 [CubeDef 예 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Hierarchy 개체 (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [ADO MD 수준 컬렉션](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [(ADO MD) members 컬렉션](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties 컬렉션(ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)