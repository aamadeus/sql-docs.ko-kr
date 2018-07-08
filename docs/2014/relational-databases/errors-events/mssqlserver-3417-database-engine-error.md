---
title: MSSQLSERVER_3417 | Microsoft 문서
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
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0792994bf2d821ae51e8a490e3e093544b81cf88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36184714"
---
# <a name="mssqlserver3417"></a>MSSQLSERVER_3417
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|3417|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|REC_BADMASTER|  
|메시지 텍스트|master 데이터베이스를 복구할 수 없습니다. SQL Server를 실행할 수 없습니다. 전체 백업에서 master 데이터베이스를 복원하거나 master 데이터베이스를 복구 또는 다시 작성하십시오. master 데이터베이스를 다시 작성하는 방법은 SQL Server 온라인 설명서를 참조하십시오.|  
  
## <a name="explanation"></a>설명  
 SQL Server에서 **master** 데이터베이스를 시작할 수 없습니다. **master** 또는 **tempdb**를 온라인 상태로 만들 수 없으면 SQL Server를 실행할 수 없습니다. 이 오류는 보통 다른 오류 뒤에 나옵니다. 오류 로그를 검토하여 근본 원인을 찾으십시오.  
  
## <a name="user-action"></a>사용자 동작  
 데이터베이스 백업을 복원하거나 데이터베이스를 복구하십시오.  
  
  