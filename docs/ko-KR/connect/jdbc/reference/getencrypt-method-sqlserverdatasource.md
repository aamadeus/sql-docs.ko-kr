---
title: getEncrypt 메서드 (SQLServerDataSource) | Microsoft Docs
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
- getEncrypt Method (SQLServerDataSource)
apilocation:
- getEncrypt Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 1cdb12dd-6e6f-4bbd-8f5f-9e630f3ee2c9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fcc6ba50954f45d88bb16d1a5ba065d59cf0f57
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="getencrypt-method-sqlserverdatasource"></a>getEncrypt 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  반환 된 **부울** encrypt 속성이 사용 되는지 여부를 나타내는 값입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean getEncypt()  
```  
  
## <a name="return-value"></a>반환 값  
 **true 이면** 경우 암호화를 사용할 수 있습니다. 그렇지 않으면 **false**입니다.  
  
## <a name="remarks"></a>주의  
 Encrypt 속성이로 설정 되어 있으면 **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 되도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 서버 인증서가 설치 되어 있으면 클라이언트와 서버 간에 전송 되는 모든 데이터에 대해 SSL 암호화를 사용 합니다.  
  
 Encrypt 속성이 지정 되지 않았거나로 설정 하는 경우 **false**, 드라이버는 적용 하지 않습니다는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL 암호화를 지원 하도록 합니다. 경우는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 인스턴스가 SSL 암호화 사용 하도록 구성 되지 않은, 암호화 없이 연결이 설정 됩니다. 경우는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 인스턴스가 SSL 암호화를 사용 하도록 구성 되어는 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 가 자동으로 SSL 암호화를 사용 경우 클라이언트 올바르게 구성 된 실행 가상 컴퓨터 JVM (Java), 그렇지 않으면 연결을 종료 하 고 드라이버에서 발생 한 오류가 발생 했습니다. 암호화 속성을 설정 하지는 [getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md) 메서드는 기본값인을 반환 **false**합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  