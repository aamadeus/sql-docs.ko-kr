---
title: "새 별칭(별칭 탭) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# 새 별칭(별칭 탭)
  별칭은 연결 설정에 사용할 수 있는 대체 이름입니다. 별칭은 연결 문자열의 필수 요소를 캡슐화하고 사용자가 선택한 이름으로 나타납니다. **별칭 - 새로 만들기** 대화 상자의 **별칭** 페이지를 사용하여 별칭에 대한 연결 문자열의 요소를 지정할 수 있습니다. 기존 별칭의 연결 문자열을 변경하려면 [&#60;Alias&#62; 속성&#40;별칭 탭&#41;](../../tools/configuration-manager/alias-properties-alias-tab.md)을 참조하세요.  
  
 **속성** 표의 모든 값을 채울 필요는 없습니다. 선택한 프로토콜에 따라 유효한 값 조합이 달라집니다. 유효한 값 조합의 예는 아래 항목을 참조하십시오.  
  
 **별칭**  
 이 연결을 나타내는 데 사용할 이름(별칭)입니다.  
  
 **파이프 이름** / **포트 번호**  
 연결 문자열의 추가 요소입니다. 이 상자의 이름은 선택한 프로토콜에 따라 달라집니다.  
  
 **프로토콜**  
 연결에 사용된 프로토콜입니다.  
  
 **Server**  
 연결 중인 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.  
  
## 별칭을 사용하는 경우  
 기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 로컬 인스턴스에 연결할 때는 **공유 메모리** 프로토콜을 사용하고 다른 컴퓨터의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 때는 **TCP/IP** 또는 **명명된 파이프**를 사용합니다. TCP/IP 또는 명명된 파이프를 사용할 때, 사용자 지정 연결 문자열을 제공하려고 할 때 또는 연결에 대해 서버 이름 외에 다른 이름을 사용하려고 할 때 별칭을 만듭니다.  
  
### 예  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 기본 TCP/IP 포트인 1433에서 수신하지 않고 다른 포트 번호를 사용하여 연결 문자열을 제공하려고 합니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 기본 명명된 파이프에서 수신하지 않고 다른 파이프 이름을 사용하여 연결 문자열을 제공하려고 합니다.  
  
-   응용 프로그램이 서버의 `ACCT`라는 데이터베이스에 연결하려고 하는데 이 데이터베이스가 `ACCT` 이라는 서버의 `CENTRAL`라는 인스턴스로 통합되었습니다. 응용 프로그램은 쉽게 변경할 수 없으므로 `ACCT`를 가리키는 문자열을 사용하여 `CENTRAL\ACCT`라는 별칭을 만듭니다.  
  
## 유효한 연결 문자열 만들기  
 유효한 별칭 속성 조합에 대한 설명과 예는 다음 항목을 참조하십시오.  
  
-   [공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [TCP/IP를 사용하여 유효한 연결 문자열 만들기](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [명명된 파이프를 사용하여 유효한 연결 문자열 만들기](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  