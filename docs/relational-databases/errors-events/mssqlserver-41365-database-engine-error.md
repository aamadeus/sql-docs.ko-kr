---
title: "MSSQLSERVER_41365 | Microsoft 문서"
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
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 80b892c4627af5fd2db098c4e815f315d0bb85e1
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41365"></a>MSSQLSERVER_41365
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41365|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|HK_MERGE_SCHEDULE_ERROR|  
|메시지 텍스트|%.*ls 데이터베이스의 트랜잭션 범위 [%ld, %ld]에 대한 병합 요청이 예약되지 않았습니다. 범위를 나타내는 검사점 파일이 병합에 사용할 수 없거나 진행 중인 병합의 일부가 아닙니다.|  
  
## <a name="explanation"></a>설명  
범위를 나타내는 검사점 파일이 병합에 사용할 수 없거나 진행 중인 병합의 일부가 아닙니다.  
  
## <a name="user-action"></a>사용자 동작  
같은 요청을 다시 실행하기 전에 병합/대기에 사용할 더 나은 트랜잭션 범위를 제공합니다. 자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[메모리 내 OLTP&#40;메모리 내 최적화&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
