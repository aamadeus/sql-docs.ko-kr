---
title: getAsciiStream (java.lang.String) | Microsoft Docs
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
- SQLServerCallableStatement.getAsciiStream(String paramName)
apilocation:
- SQLServerCallableStatement.getAsciiStream(String paramName)
apitype: Assembly
ms.assetid: 630b659f-eb36-4277-b04e-9a2e6134f795
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab473df5fc28d88a573c8bdf0276d582a9aef0f2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getasciistream-javalangstring"></a>getAsciiStream(java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  스트림으로 지정된 된 매개 변수의 값을 검색 **ASCII** 문자 매개 변수 이름이 지정 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public final java.io.InputStream getAsciiStream(java.lang.String paramName)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *paramName*  
  
 A **문자열** 매개 변수 이름을 나타내는입니다.  
  
## <a name="return-value"></a>반환 값  
 InputStream 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>관련 항목:  
 [getAsciiStream 메서드 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 멤버](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 클래스](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  