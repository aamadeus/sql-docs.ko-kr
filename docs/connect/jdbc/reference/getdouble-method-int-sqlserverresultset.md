---
title: getDouble 메서드(int)(SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDouble (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 128df26a-9063-4bdf-a4fb-a077cbe7cfe1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77589b13639f678b0c647241054075ec26151e5b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635221"
---
# <a name="getdouble-method-int-sqlserverresultset"></a>getDouble 메서드(int)(SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 개체의 현재 행에서 지정된 열 인덱스의 값을 Java 프로그래밍 언어의 **double**로 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public double getDouble(int columnIndex)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *columnIndex*  
  
 열 인덱스를 나타내는 **int**입니다.  
  
## <a name="return-value"></a>반환 값  
 A **이중** 값입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 getDouble 메서드는 java.sql.ResultSet 인터페이스의 getDouble 메서드에 의해 지정됩니다.  
  
 이 메서드는 Java **double** 정확성이 유지되는 모든 숫자 기반 데이터 형식을 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [getDouble 메서드&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdouble-method-sqlserverresultset.md)   
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
