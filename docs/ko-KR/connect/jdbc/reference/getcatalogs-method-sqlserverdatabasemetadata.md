---
title: getCatalogs 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs
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
- SQLServerDatabaseMetaData.getCatalogs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdac1017f9327cd69f83f66aa71ec58bb42710e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getcatalogs-method-sqlserverdatabasemetadata"></a>getCatalogs 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  연결된 서버에서 사용할 수 있는 카탈로그 이름을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## <a name="return-value"></a>반환 값  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getCatalogs 메서드는 java.sql.DatabaseMetaData 인터페이스의 getCatalogs 메서드에 의해 지정 됩니다.  
  
> [!NOTE]  
>  호출 하려면 master 데이터베이스에 연결 해야 SQL Azure에서 **SQLServerDatabaseMetaData.getCatalogs**합니다. SQL Azure 사용자 데이터베이스에서 카탈로그의 전체 집합을 반환 하는 것을 지원 하지 않습니다. **SQLServerDatabaseMetaData.getCatalogs** 는 sys.databases 보기를 사용 하 여 카탈로그를 가져옵니다. 권한 설명을 참조 하십시오 [sys.databases (SQL Azure 데이터베이스)](http://go.microsoft.com/fwlink/?LinkId=217396) 이해 하려면 **SQLServerDatabaseMetaData.getCatalogs** SQL Azure의 동작입니다.  
  
 GetCatalogs 메서드에 의해 반환 된 결과 집합에는 다음 정보가 포함 됩니다.  
  
|이름|유형|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**문자열**|시스템 데이터베이스를 비롯 한 카탈로그의 이름 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]합니다.|  
  
## <a name="example"></a>예제  
 다음 예제에서는에 포함 된 모든 데이터베이스의 이름을 반환 하려면 getCatalogs 메서드를 사용 하는 방법을 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], 시스템 데이터베이스를 포함 합니다.  
  
```  
public static void executeGetCatalogs(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCatalogs();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  