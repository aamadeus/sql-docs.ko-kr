---
title: setAsciiStream 메서드 (SQLServerNClob) | Microsoft Docs
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
ms.assetid: 617ece92-0fb1-4f95-b32d-29b5b56eb3fb
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5139e22b9370584f9d4b4011f42541d29c9d317
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="setasciistream-method-sqlservernclob"></a>setAsciiStream 메서드(SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  검색 ASCII를 쓰는 데 사용할 스트림을 문자 수는 **NCLOB** 값이 **java.sql.NClob** 개체가 나타내는, 지정된 된 위치에서 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *pos*  
  
 에 쓰기 시작할 위치는 **NCLOB** 개체; 첫 번째 위치는 1입니다.  
  
## <a name="return-value"></a>반환 값  
 ASCII 인코딩 문자 스트림을 나타내는 OutputStream 개체를 작성할 수 있습니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 setAsciiStream 메서드 setAsciiStream 메서드 java.sql.NClob 인터페이스에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerNClob 메서드](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 멤버](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 클래스](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  