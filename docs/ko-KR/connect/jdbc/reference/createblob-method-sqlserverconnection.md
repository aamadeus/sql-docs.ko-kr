---
title: createBlob 메서드 (SQLServerConnection) | Microsoft Docs
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
ms.assetid: 630a93b0-6e3c-4255-a007-1097ce0ee243
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6d149dfe7c29b129b023c70bf983f11d185582f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="createblob-method-sqlserverconnection"></a>createBlob 메서드(SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  데이터가 없는 Blob 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.Blob createBlob()  
```  
  
## <a name="return-value"></a>반환 값  
 Blob 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 createBlob 메서드는 java.sql.Connection 인터페이스의 createBlob 메서드에 의해 지정 됩니다.  
  
 이 메서드 대신 사용할 [SQLServerBlob 생성자 &#40;SQLServerConnection, 바이트&#41;](../../../connect/jdbc/reference/sqlserverblob-constructor-sqlserverconnection-byte.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerConnection 멤버](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 클래스](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  