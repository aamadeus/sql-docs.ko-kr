---
title: moveToInsertRow 메서드(SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cea6bc026cecccdb362b8aef422f3f38ab8ef22
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677171"
---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>moveToInsertRow 메서드(SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  커서를 삽입 행으로 이동합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 moveToInsertRow 메서드는 java.sql.ResultSet 인터페이스의 moveToInsertRow 메서드에 의해 지정 됩니다.  
  
 현재 커서 위치는 커서가 삽입 행에 있는 동안 저장됩니다. 삽입 행은 업데이트할 수 있는 결과 집합과 연결된 특수한 행으로, 기본적으로는 결과 집합에 행을 추가하기 전에 updater 메서드를 호출하여 새 행을 생성할 수 있는 버퍼입니다.  
  
 커서가 삽입 행에 있을 때는 updater, getter 및 [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) 메서드만 호출할 수 있습니다. 이 메서드를 호출할 때마다, 또한 insertRow를 호출하기 전에 결과 집합의 모든 열에 값을 지정해야 합니다. 또한 열 값에 대해 getter 메서드를 호출하려면 먼저 updater 메서드를 호출해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
