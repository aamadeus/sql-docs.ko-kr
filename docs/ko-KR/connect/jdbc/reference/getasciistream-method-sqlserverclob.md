---
title: getAsciiStream 메서드 (SQLServerClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
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
- SQLServerClob.getAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 134abe5e-5add-4d27-b333-b4b0f4d94c31
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3bba1354a860bf0c7ba044646cb4e21d3bb4166b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getasciistream-method-sqlserverclob"></a>getAsciiStream 메서드(SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  CLOB을 ASCII 스트림으로 구체화합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.io.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>반환 값  
 CLOB 데이터가 들어 있는 입력 스트림입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getAsciiStream 메서드는 java.sql.Clob 인터페이스의 getAsciiStream 메서드에 의해 지정 됩니다.  
  
 항상 바이트 배열을 반환하며, CLOB의 데이터가 유니코드인지 아니면 다른 멀티바이트 코드 페이지인지를 알 수 있는 방법이 없으므로 이 데이터가 ASCII 형식이라고 가정합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerClob 메서드](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 멤버](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 클래스](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  