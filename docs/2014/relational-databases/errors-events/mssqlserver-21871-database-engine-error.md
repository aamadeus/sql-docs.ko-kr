---
title: MSSQLSERVER_21871 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 910fc06aac87eb846c0db76956eb45377fa3ecdb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36090670"
---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|21871|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQLErrorNum21871|  
|메시지 텍스트|데이터베이스 %s의 게시자 %s이(가) 리디렉션되지 않았습니다.|  
  
## <a name="explanation"></a>설명  
 `sp_validate_replica_hosts_as_publishers` 확인 된 게시자 및 게시자 데이터베이스에 대 한 항목에 대 한 배포 데이터베이스에서 테이블 MSredirected_publishers 확인합니다.  항목이 없으면 `sp_validate_replica_hosts_as_publishers`가 오류 21871을 반환합니다.  
  
## <a name="user-action"></a>사용자 동작  
 `sp_validate_replica_hosts_as_publishers`는 리디렉션된 게시자와만 관련됩니다. 게시자 데이터베이스가 가용성 그룹의 멤버인 경우에는 `sp_redirect_publisher` 저장 프로시저를 사용하여 게시자 및 게시자 데이터베이스에 가용성 그룹의 가용성 그룹 수신기 이름을 연결하십시오.  
  
  