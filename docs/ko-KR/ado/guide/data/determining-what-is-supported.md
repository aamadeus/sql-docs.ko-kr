---
title: 지원 되는 옵션 확인 | Microsoft Docs
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
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 842b700a9359fe513fcdfc0b01009da1c10a084a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="determining-what-is-supported"></a>지원 되는 기능 확인
**지원** 메서드를 사용 하는 지정 된 지 여부를 결정 **레코드 집합** 개체는 특정 종류의 기능을 지원 합니다. 다음 구문이 있습니다.  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>주의  
 **지원** 메서드 공급자의 모든 CursorOptions 인수에 의해 식별 된 기능을 지원 하는지 여부를 나타내는 부울 값을 반환 합니다. 사용할 수 있습니다는 **지원** 어떤 유형의 기능을 확인 하는 **레코드 집합** 개체를 지원 합니다. 경우는 **레코드 집합** 개체에 있는 해당 상수는 기능을 지원 *CursorOptions*, **지원** 메서드 반환 **True**. 그렇지 않으면 반환 **False**합니다.  
  
 사용 하는 **지원** 메서드의 기능을 확인할 수 있습니다는 **레코드 집합** 새 레코드를 추가, 책갈피 사용, 사용 하 여 개체는 **찾을** 메서드를 사용 하 여 스크롤을 사용 하 여는  **인덱스** 속성을 일괄 처리 업데이트를 수행 합니다. 상수 및 해당 의미의 전체 목록은 참조 하십시오. [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)합니다.  
  
 하지만 **지원** 반환 될 수 있으며 **True** 지정된 된 기능에 대 한 보장 하지는 않습니다 공급자 사용할 수 있는 기능 모든 상황에서. **지원** 메서드는 특정 조건이 충족 된다는 가정 하는 공급자 지정 된 기능을 지원할 수 있는지 여부를 반환 합니다. 예를 들어는 **지원** 메서드를 나타낼 수 있습니다는 **레코드 집합** 커서 여러 테이블 조인에 기반 하는 경우에 개체가 업데이트를 지 원하는-의 일부 열을 업데이트할 수 없는 경우.