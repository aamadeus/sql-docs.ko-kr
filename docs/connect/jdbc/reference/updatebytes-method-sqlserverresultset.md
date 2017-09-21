---
title: "updateBytes 메서드 (SQLServerResultSet) | Microsoft Docs"
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
- SQLServerResultSet.updateBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e20e126945f11a2cba5d4b1171dc762f2a2efbac
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="updatebytes-method-sqlserverresultset"></a>updateBytes 메서드(SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  지정된 된 열을의 배열로 업데이트 **바이트** 값입니다.  
  
## <a name="overload-list"></a>오버로드 목록  
  
|이름|Description|  
|----------|-----------------|  
|[updateBytes (int, 바이트 &#91; &#93;)](../../../connect/jdbc/reference/updatebytes-method-int-byte.md)|지정된 된 열을의 배열로 업데이트 **바이트** 열 인덱스가 지정 된 값입니다.|  
|[updateBytes (java.lang.String, 바이트 &#91; &#93;)](../../../connect/jdbc/reference/updatebytes-method-java-lang-string-byte.md)|지정된 된 열을의 배열로 업데이트 **바이트** 열 이름이 지정 된 값입니다.|  
  
## <a name="remarks"></a>주의  
 이전 버전의에서 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], SQLServerResultSet.updateBytes를 사용 하 여 바이트 배열 간에 값을 변환할 수 있습니다 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 데이터 형식 **날짜**, **시간**, ** datetime2**, 또는 **datetimeoffset**합니다. 이제 이 메서드와 이러한 데이터 형식을 함께 사용하면 변환이 지원되지 않음을 나타내는 예외가 발생합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  