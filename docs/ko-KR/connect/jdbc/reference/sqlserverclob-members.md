---
title: SQLServerClob 멤버 | Microsoft Docs
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
apitype: Assembly
ms.assetid: 7db785ca-edd5-4833-8053-17fdbf87279a
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d0c1db09adaa23a9f1ac1309cce91e4cf087437
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverclob-members"></a>SQLServerClob 멤버
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  다음 표에서에서 노출 하는 멤버는 [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md) 클래스입니다.  
  
## <a name="constructors"></a>생성자  
  
|이름|Description|  
|----------|-----------------|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md)|SQLServerClob 클래스의 새 인스턴스를 초기화합니다.|  
  
## <a name="fields"></a>필드  
 없음  
  
## <a name="inherited-fields"></a>상속된 필드  
 없음  
  
## <a name="methods"></a>메서드  
  
|이름|Description|  
|----------|-----------------|  
|[무료](../../../connect/jdbc/reference/free-method-sqlserverclob.md)|이 메서드는 CLOB 개체 및 이 개체가 보유한 리소스를 해제합니다.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverclob.md)|Clob을 ASCII 스트림으로 구체화합니다.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)|Clob 데이터를 java.io.Reader 개체 또는 문자 스트림으로 반환합니다.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlserverclob.md)|지정된 시작 위치 및 복사할 문자 수에 따라 Clob에서 지정된 부분 문자열의 복사본을 반환합니다.|  
|[length](../../../connect/jdbc/reference/length-method-sqlserverclob.md)|Clob의 문자 수를 반환합니다.|  
|[position](../../../connect/jdbc/reference/position-method-sqlserverclob.md)|지정된 시작 위치에 따라 지정된 Clob 개체 또는 해당 Clob에 있는 부분 문자열의 문자 위치를 반환합니다.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverclob.md)|Clob의 지정된 위치에서부터 ASCII 문자를 쓰는 데 사용할 스트림을 반환합니다.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverclob.md)|Clob의 지정된 위치에서부터 유니코드 문자 스트림을 쓰는 데 사용할 스트림을 반환합니다.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)|지정된 문자열을 Clob의 지정된 위치에서부터 씁니다.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlserverclob.md)|Clob을 지정된 길이로 자릅니다.|  
  
## <a name="inherited-methods"></a>상속된 메서드  
  
|상속하는 원본 클래스|메서드|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerClob 클래스](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  