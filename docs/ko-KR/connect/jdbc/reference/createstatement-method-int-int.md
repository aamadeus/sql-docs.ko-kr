---
title: createStatement 메서드 (int, int) | Microsoft Docs
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
- SQLServerConnection.createStatement (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90dbf639-c3d8-4519-9300-5447c79aec17
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7aaf58f311d4b3ebcd59cfd86aa07bc80ca1a2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="createstatement-method-int-int"></a>createStatement 메서드(int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  만듭니다는 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 생성 하는 개체 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 지정 된 형식 및 동시성을 사용 하 여 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.Statement createStatement(int resultSetType,  
                                          int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *resultSetType*  
  
 **int** 결과 집합 유형을 나타내는 값입니다.  
  
 *resultSetConcurrency*  
  
 **int** 결과 집합 동시성 유형을 나타내는 값입니다.  
  
## <a name="return-value"></a>반환 값  
 문 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 createStatement 메서드는 java.sql.Connection 인터페이스의 createStatement 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [createStatement 메서드 &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection 멤버](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 클래스](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  