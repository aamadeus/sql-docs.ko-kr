---
title: getPacketSize 메서드(SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7790bc9eabb5127e36faddc02bb477c91ba72ac6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838981"
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>getPacketSize 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]와의 통신에 사용되는 현재 네트워크 패킷 크기(바이트)를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>반환 값  
 현재 네트워크 패킷 크기가 들어 있는 **int** 값입니다.  
  
## <a name="remarks"></a>Remarks  
 packetSize 속성이 설정되어 있지 않으면 getPacketSize 메서드는 기본값인 8000을 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
