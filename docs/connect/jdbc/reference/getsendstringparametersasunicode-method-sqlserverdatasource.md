---
title: getSendStringParametersAsUnicode 메서드 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3dedc988bd4ddf32046a9a29abe5b83b293bf04
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683141"
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>getSendStringParametersAsUnicode 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  문자열 매개 변수를 서버에 유니코드 형식으로 보낼 수 있는지 여부를 나타내는 **boolean** 값을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>반환 값  
 문자열 매개 변수를 서버에 유니코드 형식으로 보낼 수 있으면 **true**이고, 그렇지 않으면 **false**입니다.  
  
## <a name="remarks"></a>Remarks  
 sendStringParametersAsUnicode 속성이 기본값인 **true**로 설정되어 있으면 문자열 매개 변수가 서버에 유니코드 형식으로 보내집니다. sendStringParametersAsUnicode 속성이 **false**로 설정되어 있으면 문자열 매개 변수가 서버에 유니코드 형식이 아닌 ASCII/MBCS 형식으로 보내집니다. sendStringParametersAsUnicode 속성이 설정되어 있지 않으면 getSendStringParametersAsUnicode는 기본값인 **true**를 반환합니다.  
  
 SendStringParametersAsUnicode 연결 속성에 대 한 자세한 내용은 참조 하세요. [연결 속성 설정](../../../connect/jdbc/setting-the-connection-properties.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
