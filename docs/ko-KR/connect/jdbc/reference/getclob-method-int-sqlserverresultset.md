---
title: getClob 메서드 (int) (SQLServerResultSet) | Microsoft Docs
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
- SQLServerResultSet.getClob (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91020fad-a9e2-4ea4-9c72-c63cf6b1051c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6842cedbdacbd5b9dcdde83cf55fd1e40ec258f2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getclob-method-int-sqlserverresultset"></a>getClob 메서드 (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 현재 행에서 지정 된 열 인덱스의 값을 검색 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) Java 프로그래밍 언어의에서 Clob 개체로 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.Clob getClob(int columnIndex)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *columnIndex*  
  
 **int** 열 인덱스를 나타내는입니다.  
  
## <a name="return-value"></a>반환 값  
 Clob 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getClob 메서드는 java.sql.ResultSet 인터페이스의 getClob 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [getClob 메서드 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)   
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  