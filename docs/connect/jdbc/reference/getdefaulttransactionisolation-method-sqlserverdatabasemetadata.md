---
title: "getDefaultTransactionIsolation 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs"
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
- SQLServerDatabaseMetaData.getDefaultTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85b867ed-de5a-4879-b3f8-bce897879077
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4f080450f81b5298df60c168e549a41c3d148cc7
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getdefaulttransactionisolation-method-sqlserverdatabasemetadata"></a>getDefaultTransactionIsolation 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 데이터베이스에 대한 기본 트랜잭션 격리 수준을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public int getDefaultTransactionIsolation()  
```  
  
## <a name="return-value"></a>반환 값  
 **int** 기본 트랜잭션 격리 수준을 나타내는입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getDefaultTransactionIsolation 메서드는 java.sql.DatabaseMetaData 인터페이스의 getDefaultTransactionIsolation 메서드에 의해 지정 됩니다.  
  
 사용 하는 경우는 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 데이터베이스에서이 메서드는 TRANSACTION_READ_COMMITTED의 값을 반환 또는 **int** 값 2입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  