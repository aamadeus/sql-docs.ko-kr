---
title: getShort 메서드(java.lang.String)(SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getShort (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 183af414-b0a3-4ca7-b160-d199bcf469b0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d4a3695752004b9e688dbf266fa613e24673558
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47725311"
---
# <a name="getshort-method-javalangstring-sqlserverresultset"></a>getShort 메서드(java.lang.String)(SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 개체의 현재 행에서 지정된 열 이름의 값을 Java 프로그래밍 언어의 **short**로 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public short getShort(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *columnName*  
  
 열 이름이 포함된 **문자열**입니다.  
  
## <a name="return-value"></a>반환 값  
 A **짧은** 값입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 getShort 메서드는 java.sql.ResultSet 인터페이스의 getShort 메서드에 의해 지정됩니다.  
  
 이 메서드는 smallint, tinyint 및 bit와 같이 정수 값을 안전하게 반환할 수 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식에서만 지원됩니다. 다른 데이터 형식에 이 메서드를 사용하면 예외가 발생합니다.  
  
## <a name="see-also"></a>참고 항목  
 [getShort 메서드&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getshort-method-sqlserverresultset.md)   
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
