---
title: MSSQLSERVER_10061 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b8aa0fa832c39339c1653ab78a166bd7dfb821dc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079521"
---
# <a name="mssqlserver10061"></a>MSSQLSERVER_10061
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|10061|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름||  
|메시지 텍스트|서버에 대한 연결을 구성하는 동안 오류가 발생했습니다.  SQL Server에 연결할 때 기본 설정에서 SQL Server가 원격 연결을 허용하지 않기 때문에 이 오류가 발생할 수 있습니다. (공급자: TCP 공급자, 오류: 0 - 대상 컴퓨터에서 연결을 거부했으므로 연결하지 못했습니다.) (Microsoft SQL Server, 오류: 10061)|  
  
## <a name="explanation"></a>설명  
 서버가 클라이언트 요청에 응답하지 않았습니다. 서버가 시작되지 않았기 때문에 이 오류가 발생했을 수 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
 서버가 시작되었는지 확인합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 엔진 서비스 관리](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md)   
 [네트워크 프로토콜 및 네트워크 라이브러리](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [클라이언트 네트워크 구성](../../database-engine/configure-windows/client-network-configuration.md)   
 [클라이언트 프로토콜 구성](../../database-engine/configure-windows/configure-client-protocols.md)   
 [서버 네트워크 프로토콜 설정 또는 해제](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  