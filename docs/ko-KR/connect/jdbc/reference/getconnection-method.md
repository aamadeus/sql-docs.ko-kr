---
title: getConnection 메서드 () | Microsoft Docs
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
- SQLServerDataSource.getConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f520e96-5313-468f-b987-535ddaea027e
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2dabbf8ab94b8f9213ff2043ff83a1874dbd15b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getconnection-method-"></a>getConnection 메서드()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 데이터와 연결을 설정 하려고 원본 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) 개체가 나타내는입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>반환 값  
 A [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 개체입니다.  
  
## <a name="exceptions"></a>예외  
 java.sql.SQLException  
  
## <a name="remarks"></a>주의  
 이 getConnection 메서드는 javax.sql.DataSource 인터페이스의 getConnection 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [getConnection 메서드 &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  