---
title: getDateTimeOffset(int) (SQLServerResultSet) | Microsoft Docs
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
ms.assetid: 60abf83d-6f97-4e47-b9d3-5072bd09d869
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 434048c645ec01717e462e11262e9609a13e58d6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getdatetimeoffsetint-sqlserverresultset"></a>getDateTimeOffset(int)(SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 메서드는에서 추가 된 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC 드라이버 3.0.  
  
 지정 된 열의 값을 검색 하는 [DateTimeOffset 클래스](../../../connect/jdbc/reference/datetimeoffset-class.md) java 프로그래밍 언어 매개 변수 인덱스가 지정 된 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int columnIndex)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *columnIndex*  
  
 열 서수입니다.  
  
## <a name="return-value"></a>반환 값  
 A [DateTimeOffset 클래스](../../../connect/jdbc/reference/datetimeoffset-class.md) 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 업데이트할 수 있습니다는 [DateTimeOffset 클래스](../../../connect/jdbc/reference/datetimeoffset-class.md) 값과 [sqlserverresultset.updatedatetimeoffset을 사용](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerResultSet 멤버](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 클래스](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  