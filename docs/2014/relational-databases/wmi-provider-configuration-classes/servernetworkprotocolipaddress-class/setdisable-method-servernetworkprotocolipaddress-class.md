---
title: SetDisable 메서드 (ServerNetworkProtocolIPAddress 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocolIPAddress Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 7a7cc8cc-9fb8-4bf5-b483-2150d633ee10
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f556620bb66c087aefc87980e42e7d4a7e23443d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138683"
---
# <a name="setdisable-method-servernetworkprotocolipaddress-class"></a>SetDisable 메서드(ServerNetworkProtocolIPAddress 클래스)
  IP 주소를 해제합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>부분  
 *object*  
 [ServerNetworkProtocolIPAdress 클래스] servernetworkprotocolipaddress-class.md) 인스턴스의 네트워크 프로토콜에 대 한 IP 주소를 나타내는 개체 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 uint32 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>관련 항목  
 [서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
