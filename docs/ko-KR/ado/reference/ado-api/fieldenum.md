---
title: FieldEnum | Microsoft Docs
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
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6caaf8db2b8f2e19060f6e9766bb3650ac9b5400
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="fieldenum"></a>FieldEnum
참조 하는 특수 필드를 지정 된 [레코드](../../../ado/reference/ado-api/record-object-ado.md) 개체의 [필드](../../../ado/reference/ado-api/fields-collection-ado.md) 컬렉션입니다.  
  
## <a name="remarks"></a>주의  
 이러한 상수는 "바로 가기" 제공와 관련 된 특별 한 필드에 액세스 하는 **레코드**합니다. 검색의 [필드](../../../ado/reference/ado-api/field-object.md) 에서 개체는 **필드** 컬렉션을 사용 하 여 해당 콘텐츠를 다음 확인는 **필드** 개체의 [값](../../../ado/reference/ado-api/value-property-ado.md) 속성.  
  
|상수|Value|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|기본값을 포함 하는 필드 참조 [스트림](../../../ado/reference/ado-api/stream-object-ado.md) 연관 된 개체는 **레코드**합니다.|  
|**adRecordURL**|-2|현재에 대 한 절대 URL 문자열을 포함 하는 필드 참조 **레코드**합니다.|