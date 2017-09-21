---
title: "getLockTimeout 메서드 (SQLServerDataSource) | Microsoft Docs"
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
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: edbd984352f2b75711e9fc9a445a84066fb9f0ac
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>getLockTimeout 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  반환 된 **int** 는 데이터베이스에서 잠금 시간 초과가 보고 되기 전까지 대기 하는 시간 (밀리초)의 수를 나타내는 값입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>반환 값  
 **int** 데이터베이스에서 대기 하는 시간 (밀리초)의 수를 포함 하는 값입니다.  
  
## <a name="remarks"></a>주의  
 잠금 제한 시간은 데이터베이스에서 잠금 시간 초과가 보고될 때까지의 대기 시간(밀리초)입니다. 기본값인 -1은 무기한 대기를 의미합니다. 이 값을 지정하면 연결의 모든 문에 대해 이 값이 기본값으로 사용됩니다.  
  
> [!NOTE]  
>  값 0은 대기하지 않음을 의미합니다. lockTimeout 속성이 설정되어 있지 않으면 getLockTimeout 메서드는 기본값인 -1을 반환합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  