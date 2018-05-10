---
title: executeUpdate 메서드 (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb1b5e42d05508ea83b37985356c4eb0da6c68d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="executeupdate-method-javalangstring"></a>executeUpdate 메서드(java.lang.String)

INSERT, UPDATE, MERGE 또는 DELETE 문과 같은 지정된 SQL 문이나 SQL DDL 문 같이 아무 것도 반환하지 않는 SQL 문을 실행합니다.

## <a name="syntax"></a>구문

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>매개 변수
*sql*

A **문자열** SQL 문이 들어 있는입니다.

## <a name="return-value"></a>반환 값
**int** DDL 문을 사용 하는 경우 0, 영향을 받는 행의 수를 나타내는입니다.

## <a name="exceptions"></a>예외
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>주의
이 executeUpdate 메서드는 java.sql.PreparedStatement 인터페이스의 executeUpdate 메서드에 의해 지정 됩니다.

이 메서드를 호출 개체가 만들어질 때 SQLServerPreparedStatement 개체에 대 한 SQL 문이 지정 된 후 예외가 발생 합니다.

## <a name="see-also"></a>관련 항목:

[executeUpdate 메서드 &#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[SQLServerPreparedStatement 멤버](./sqlserverpreparedstatement-members.md)

[SQLServerPreparedStatement 클래스](./sqlserverpreparedstatement-class.md)