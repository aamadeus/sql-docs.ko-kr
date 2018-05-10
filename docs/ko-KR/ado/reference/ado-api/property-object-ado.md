---
title: Property 개체 (ADO) | Microsoft Docs
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
- Property
helpviewer_keywords:
- Property object [ADO]
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 774ed0d33d3066f600c6af98ea89b91a2770ed3c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="property-object-ado"></a>Property 개체 (ADO)
공급자에 의해 정의 된 ADO 개체의 동적 특성을 나타냅니다.  
  
## <a name="remarks"></a>주의  
 ADO 개체에는 두 가지 유형의 속성: 기본 제공 및 동적입니다.  
  
 기본 제공 속성은 즉시 사용할 수 및 ADO에서 구현 된 이러한 속성 new를 사용 하 여 개체는 `MyObject.Property` 구문입니다. 로 표시 되지 않습니다 **속성** 개체는 개체의 [속성](../../../ado/reference/ado-api/properties-collection-ado.md) 컬렉션 되므로 해당 값을 변경할 수 있지만 해당 특성을 수정할 수 없습니다.  
  
 동적 속성은 기본 데이터 공급자에 의해 정의 되며에 표시 된 **속성** 해당 ADO 개체에 대 한 컬렉션입니다. 예를 들어 한 속성 공급자와 관련 수를 표시 하는 경우는 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 개체가 트랜잭션이나 업데이트를 지원 합니다. 이러한 추가 속성으로 나타납니다. **속성** 개체에 있는 **레코드 집합** 개체의 **속성** 컬렉션입니다. 동적 속성 컬렉션을 통해서만 참조할 수 있습니다를 사용 하는 `MyObject.Properties(0)` 또는 `MyObject.Properties("Name")` 구문입니다.  
  
 두 가지 속성을 삭제할 수 없습니다.  
  
 동적 **속성** 개체에는 자체의 네 가지 기본 제공 속성:  
  
-   [이름](../../../ado/reference/ado-api/name-property-ado.md) 속성은 속성을 식별 하는 문자열입니다.  
  
-   [형식](../../../ado/reference/ado-api/type-property-ado.md) 속성은 속성 데이터 형식을 지정 하는 정수입니다.  
  
-   [값](../../../ado/reference/ado-api/value-property-ado.md) 속성은 속성 설정을 포함 하는 variant입니다. **값** 은 대 한 기본 속성을 **속성** 개체입니다.  
  
-   [특성](../../../ado/reference/ado-api/attributes-property-ado.md) 속성은 공급자와 관련 된 속성의 특성을 나타내는 long 값입니다.  
  
 이 섹션에는 다음 항목 포함 되어 있습니다.  
  
-   [Property 개체 속성, 메서드 및 이벤트](../../../ado/reference/ado-api/property-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>관련 항목:  
 [Command 개체 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [연결 개체 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Field 개체](../../../ado/reference/ado-api/field-object.md)   
 [Properties 컬렉션 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)