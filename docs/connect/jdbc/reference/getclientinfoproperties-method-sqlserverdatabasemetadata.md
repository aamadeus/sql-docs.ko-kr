---
title: "getClientInfoProperties 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 022f09c50d0a47851e375fcbb617ee40266dbb38
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>getClientInfoProperties 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  드라이버에서 지원하는 클라이언트 정보 속성의 목록을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>반환 값  
 결과 집합 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getClientInfoProperties 메서드는 java.sql.DatabaseMetaData 인터페이스의 getClientInfoProperties 메서드에 의해 지정 됩니다.  
  
> [!NOTE]  
>  이 메서드는 빈 결과 집합을 반환합니다. 드라이버 지원 설정에는 **applicationName** 설정는 **applicationName** 연결 시에만 합니다. SQL Server에서는 연결이 설정된 후 클라이언트 응용 프로그램 정보에 대한 업데이트를 지원하지 않습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  