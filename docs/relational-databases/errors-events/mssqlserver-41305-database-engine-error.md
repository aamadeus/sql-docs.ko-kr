---
title: "MSSQLSERVER_41305 | Microsoft 문서"
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
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 53bcc12cbb04ebbbc5034dffc0b7ead593a090a8
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41305"></a>MSSQLSERVER_41305
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41305|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|HK_TX_COMMIT_RR_VALIDATION|  
|메시지 텍스트|반복 읽기 유효성 검사 실패로 인해 현재 트랜잭션을 커밋하지 못했습니다.|  
  
## <a name="explanation"></a>설명  
유효성 검사 오류가 발생하여 트랜잭션을 종료합니다.  
  
자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
## <a name="user-action"></a>사용자 동작  
실패한 트랜잭션을 다시 시도합니다.  
  
## <a name="see-also"></a>참고 항목  
[메모리 내 OLTP&#40;메모리 내 최적화&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
