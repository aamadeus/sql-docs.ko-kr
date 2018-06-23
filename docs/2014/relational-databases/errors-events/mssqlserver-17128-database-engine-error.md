---
title: MSSQLSERVER_17128 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e94a837f68b0a4951d51367477e28e64d1e9f081
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36181594"
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|17128|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|INIT_NOBUFSPACE|  
|메시지 텍스트|initdata: 커널 버퍼용 메모리가 없습니다.|  
  
## <a name="explanation"></a>설명  
 버퍼 풀의 초기 메모리 할당 및 예약이 실패했고 SQL Server가 종료되었습니다.  
  
## <a name="user-action"></a>사용자 동작  
 일반적으로 이 오류는 최소 시스템 요구 사항보다 훨씬 작은 매우 작은 시스템에서 SQL Server를 시작하는 경우에 발생합니다.  
  
  