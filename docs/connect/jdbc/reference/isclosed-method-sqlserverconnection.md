---
title: isClosed 메서드(SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 508b3d1fe22ff58e91865204d6b74822ba6f5763
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647633"
---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed 메서드(SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 개체가 닫혔는지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>반환 값  
 **true 이면** 연결이 닫혀 있으면 **false** 없는 경우.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 isClosed 메서드는 java.sql.Connection 인터페이스의 isClosed 메서드에 의해 지정 됩니다.  
  
 호출된 된 SQLServerConnection 개체의 상태를 확인합니다. 개체에서 [close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) 메서드가 호출되었거나 치명적인 오류가 발생했으면 연결이 닫혀 있습니다. 이 메서드는 close 메서드가 호출된 후에 호출되는 경우에만 **true**를 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerConnection 멤버](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 클래스](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
