---
title: Delete 메서드 (ADO 필드 컬렉션) | Microsoft Docs
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
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a1d6bdde017ac021d455d02c655dfc6f3a6151c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="delete-method-ado-fields-collection"></a>Delete 메서드 (ADO 필드 컬렉션)
개체를 삭제는 [필드](../../../ado/reference/ado-api/fields-collection-ado.md) 컬렉션입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>매개 변수  
 *필드*  
 A **Variant** 를 지정 하는 [필드](../../../ado/reference/ado-api/field-object.md) 삭제할 개체입니다. 이 매개 변수 이름을 일 수는 **필드** 개체나의 서 수 위치는 **필드** 개체 자체입니다.  
  
## <a name="remarks"></a>주의  
 호출 된 **Fields.Delete** 열린 메서드 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 하면 런타임 오류가 발생 합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [Fields 컬렉션(ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>관련 항목:  
 [Delete 메서드 (ADO Parameters 컬렉션)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete 메서드 (ADO 레코드 집합)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord 메서드(ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)