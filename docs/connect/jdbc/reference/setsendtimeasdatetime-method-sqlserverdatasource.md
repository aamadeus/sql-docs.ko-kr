---
title: setSendTimeAsDatetime 메서드 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad4f7e8cee834619985be1ab140bc39698215060
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798241"
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>setSendTimeAsDatetime 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 메서드는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC 드라이버 3.0에서 추가되었습니다.  
  
 설정을 수정 합니다 **sendTimeAsDatetime** 연결 속성입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *sendTimeAsDateTime*  
  
 부울 값입니다. true이면 java.sql.Time 값이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime** 형식으로 서버에 보내집니다. false이면 java.sql.Time 값이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **time** 형식으로 서버에 보내집니다.  
  
## <a name="remarks"></a>Remarks  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)은 **sendTimeAsDatetime** 연결 속성의 설정을 반환합니다.  
  
 에 대 한 자세한 합니다 **sendTimeAsDatetime** 연결 속성을 참조 하세요 [연결 속성 설정](../../../connect/jdbc/setting-the-connection-properties.md)합니다.  
  
 자세한 내용은 [어떻게 구성 java.sql.Time 값을 서버로 전송 됩니다](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
