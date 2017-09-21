---
title: "setString 메서드 (long, java.lang.String, int, int) | Microsoft Docs"
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
- SQLServerClob.setString (long, java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fb59b09-e825-46a6-ba5d-85d4a8dc143a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 362cd4df54ee5ad826d2313341cd9ba4c7253546
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring-int-int"></a>setString 메서드(long, java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  지정된 오프셋 및 길이에 따라 CLOB의 지정된 위치부터 지정된 문자열을 씁니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public int setString(long pos,  
                     java.lang.String str,  
                     int offset,  
                     int len)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *pos*  
  
 CLOB에 쓰기 시작할 위치입니다.  
  
 *str*  
  
 CLOB에 쓸 문자열입니다.  
  
 *오프셋*  
  
 문자열 내에서 문자를 읽기 시작할 위치의 오프셋입니다.  
  
 *len 함수*  
  
 쓸 문자 수입니다.  
  
## <a name="return-value"></a>반환 값  
 쓴 문자 수입니다.  
  
## <a name="exceptions"></a>예외  
 java.sql.SQLException  
  
## <a name="remarks"></a>주의  
 이 setString 메서드는 java.sql.Clob 인터페이스의 setString 메서드에 의해 지정 됩니다.  
  
 문자 데이터는 지정된 위치부터 덮어쓰여지며 CLOB의 초기 길이를 덮어쓸 수 있습니다. 위치+1 값을 지정하면 문자열이 추가되고, 위치+2 이상(또는 0 이하)의 값을 지정하면 위치 오류가 발생합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [setString 메서드 &#40; SQLServerClob &#41;](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)   
 [SQLServerClob 메서드](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 멤버](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob 클래스](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  