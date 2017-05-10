---
title: "MSSQLSERVER_21871 | Microsoft 문서"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1538eba494fcad374dd0454ed519777466317b0f
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|21871|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQLErrorNum21871|  
|메시지 텍스트|데이터베이스 %s의 게시자 %s이(가) 리디렉션되지 않았습니다.|  
  
## <a name="explanation"></a>설명  
**sp_validate_replica_hosts_as_publishers**는 배포 데이터베이스의 MSredirected_publishers에서 식별된 게시자 및 게시자 데이터베이스에 대한 항목을 확인합니다.  항목이 없으면 **sp_validate_replica_hosts_as_publishers**가 오류 21871을 반환합니다.  
  
## <a name="user-action"></a>사용자 동작  
**sp_validate_replica_hosts_as_publishers**는 리디렉션된 게시자와만 관련됩니다. 게시자 데이터베이스가 가용성 그룹의 멤버인 경우에는 저장 프로시저 **sp_redirect_publisher**를 사용하여 게시자 및 게시자 데이터베이스를 가용성 그룹의 가용성 그룹 수신기 이름과 연결하세요.  
  
