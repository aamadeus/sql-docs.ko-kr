---
title: "getUpdateCount 메서드 (SQLServerStatement) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 50d702db72b2d02cc52401d76cd289a3b21de81a
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getupdatecount-method-sqlserverstatement"></a>getUpdateCount 메서드 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  현재 결과를 검색하여 업데이트 횟수로 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>반환 값  
 **int** 업데이트 횟수가 들어 있는입니다. 반환된 결과가 결과 집합 개체이거나 결과가 더 이상 없으면 -1이 반환됩니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getUpdateCount 메서드는 java.sql.Statement 인터페이스의 getUpdateCount 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerStatement 멤버](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 클래스](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  