---
title: supportsStatementPooling 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsStatementPooling
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 83777807-5838-4f81-94ab-3ba4fc5aaa47
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c066dba16919a2cf16c9470ee726c97220c285f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782761"
---
# <a name="supportsstatementpooling-method-sqlserverdatabasemetadata"></a>supportsStatementPooling 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 데이터베이스에서 문 풀링을 지원하는지 여부를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean supportsStatementPooling()  
```  
  
## <a name="return-value"></a>반환 값  
 **true** 지원 되는 경우. 그렇지 않으면 **false**입니다.  
  
## <a name="exceptions"></a>예외  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 이 supportsStatementPooling 메서드는 java.sql.DatabaseMetaData 인터페이스의 supportsStatementPooling 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
