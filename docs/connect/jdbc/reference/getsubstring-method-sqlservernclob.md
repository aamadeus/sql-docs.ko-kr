---
title: getSubString 메서드(SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1d91c930-1bac-4da9-b9a5-ac2cfd31541b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f283115f4629e778d9b6fc4a94ccaf85064da6c4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47648961"
---
# <a name="getsubstring-method-sqlservernclob"></a>getSubString 메서드(SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  지정된 시작 위치 및 복사할 문자 수에 따라 **NCLOB**에서 지정된 부분 문자열의 복사본을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.lang.String getSubString(long pos,  
                                  int length)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *pos*  
  
 추출할 부분 문자열의 첫 번째 문자입니다. 첫 번째 문자는 위치 1에 있습니다.  
  
 *length*  
  
 복사할 연속된 문자의 수입니다.  
  
## <a name="return-value"></a>반환 값  
 **NCLOB**에서 지정된 부분 문자열인 **문자열**입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 getSubString 메서드 java.sql.NClob 인터페이스의 getSubString 메서드에 의해 지정됩니다.  
  
 null 또는 길이가 0인 NCLOB에서 0개의 문자를 가져오려고 하면 빈 문자열이 반환됩니다. 길이가 0인 NCLOB에서 위치 1이 아닌 다른 위치에 있는 임의 길이의 문자를 가져오려고 하면 위치 예외가 발생합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerNClob 메서드](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 멤버](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 클래스](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
