---
title: isWrapperFor 메서드 (SQLServerPreparedStatement) | Microsoft Docs
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
ms.assetid: b0e591b1-73e2-4f90-967f-5555eadfc3f1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3920e10bb7fc100879b1ab52e19e2ef9705cf5b6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="iswrapperfor-method-sqlserverpreparedstatement"></a>isWrapperFor 메서드(SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 문 개체가 지정된 인터페이스에 대한 래퍼인지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *iface*  
  
 A **클래스** 인터페이스를 정의 합니다.  
  
## <a name="return-value"></a>반환 값  
 **true 이면** 이 개체가 인터페이스를 구현 하거나 인터페이스를 구현 하는 개체를 래핑합니다. 그렇지 않으면 **false**입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md) 메서드 및 [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) 메서드는 JDBC 4.0 사양에서 도입 된 java.sql.Wrapper 인터페이스에 의해 정의 됩니다.  
  
 이 메서드가 true를 반환 하는 경우 호출 [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) 동일한 인수 성공 합니다.  
  
 자세한 내용은 참조 [래퍼 및 인터페이스](../../../connect/jdbc/wrappers-and-interfaces.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [unwrap 메서드 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 멤버](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement 클래스](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  