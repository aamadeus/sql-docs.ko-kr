---
title: getStatement 메서드(SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getStatement
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dea981b-b4fd-4f8d-954f-e686124627e2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 880572925fb1eeb9a9b6f7becbe42d6ed5601d28
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635201"
---
# <a name="getstatement-method-sqlserverresultset"></a>getStatement 메서드(SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 개체를 생성한 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 개체를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.Statement getStatement()  
```  
  
## <a name="return-value"></a>반환 값  
 SQLServerStatement 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 getStatement 메서드는 java.sql.ResultSet 인터페이스의 getStatement 메서드에 의해 지정됩니다.  
  
 결과 집합이 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 메서드 등의 다른 방식으로 생성된 경우 이 메서드는 null을 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
