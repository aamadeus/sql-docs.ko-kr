---
title: "getFloat 메서드 (int) (SQLServerResultSet) | Microsoft Docs"
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
- SQLServerResultSet.getFloat (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 30863ef5-7a7c-440e-8fbb-426a99266ee1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1651330ec0c4d18c1d0352c7dc27df2696fb4794
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getfloat-method-int-sqlserverresultset"></a>getFloat 메서드 (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 현재 행에서 지정 된 열 인덱스의 값을 검색 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 개체로 **float** Java 프로그래밍 언어의에서 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public float getFloat(int columnIndex)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *columnIndex*  
  
 **int** 열 인덱스를 나타내는입니다.  
  
## <a name="return-value"></a>반환 값  
 A **float** 값입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getFloat 메서드는 java.sql.ResultSet 인터페이스의 getFloat 메서드에 의해 지정 됩니다.  
  
 이 메서드는 Java 모든 숫자 기반 형식을 반환 **float** 충실도 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [getFloat 메서드 &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)   
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  