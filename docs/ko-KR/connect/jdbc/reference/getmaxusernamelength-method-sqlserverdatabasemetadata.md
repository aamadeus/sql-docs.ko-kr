---
title: getMaxUserNameLength 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs
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
- SQLServerDatabaseMetaData.getMaxUserNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 09ec7d40-4c4a-4d89-ba11-78e5327b5759
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da7d25781e1ebd084a3c1a8e33942ba2cf53868e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getmaxusernamelength-method-sqlserverdatabasemetadata"></a>getMaxUserNameLength 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 데이터베이스가 사용자 이름에 허용하는 최대 문자 수를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public int getMaxUserNameLength()  
```  
  
## <a name="return-value"></a>반환 값  
 **int** 허용 되는 문자의 최대 수를 나타내는입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getMaxUserNameLength 메서드는 java.sql.DatabaseMetaData 인터페이스의 getMaxUserNameLength 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  