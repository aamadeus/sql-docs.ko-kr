---
title: SetDisable 메서드 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- SetDisable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: bce69ab9-ea5b-43fd-8114-08b1b5890755
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6fac31f7faccf6b2c3c4f81c4aadaa69a2223d93
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116445"
---
# <a name="setdisable-method-clientnetworkprotocol-class"></a>SetDisable 메서드(ClientNetworkProtocol 클래스)
  지정 된 클라이언트 네트워크 프로토콜을 사용 하지 않도록 설정 합니다 [Configure Client Protocols](http://technet.microsoft.com/library/ms181035.aspx)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a>부분  
 *object*  
 A [ClientNetworkProtocol 클래스](clientnetworkprotocol-class.md) 사용 되는 네트워크 프로토콜을 나타내는 개체를 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 클라이언트입니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 `uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>관련 항목  
 [클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
