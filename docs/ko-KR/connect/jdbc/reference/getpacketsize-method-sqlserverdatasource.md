---
title: getPacketSize 메서드 (SQLServerDataSource) | Microsoft Docs
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
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a320d10b6dab2335226087f97d54edc213d4b50
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>getPacketSize 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  와 통신 하는 데 사용 되는 현재 네트워크 패킷 크기를 반환 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], 바이트 단위로 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>반환 값  
 **int** 현재 네트워크 패킷 크기를 포함 하는 값입니다.  
  
## <a name="remarks"></a>주의  
 PacketSize 속성을 설정 하지 않으면 getPacketSize 메서드는 기본값인 8000 반환 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  