---
title: MSSQLSERVER_41368 | Microsoft 문서
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
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 96d33fc176330efe93077c02c6abfed3c137e33c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36081105"
---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41368|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|메시지 텍스트|READ COMMITTED 격리 수준을 사용한 메모리 액세스에 최적화된 테이블 액세스는 자동 커밋 트랜잭션에서만 지원됩니다. 명시적 또는 암시적 트랜잭션에서는 지원되지 않습니다. WITH (SNAPSHOT) 같은 테이블 힌트를 사용하여 메모리 액세스에 최적화된 테이블에 대해 지원되는 격리 수준을 제공합니다.|  
  
## <a name="explanation"></a>설명  
 READ COMMITTED 격리 수준을 사용한 메모리 최적화 테이블 액세스는 자동 커밋 트랜잭션에서만 지원됩니다. 자세한 내용은 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)을 참조하세요.  
  
 BEGIN TRANSACTION으로 시작된 명시적 트랜잭션에서 메모리 최적화 테이블에 액세스할 때 IMPLICIT_TRANSACTIONS가 ON으로 설정되어 있으면 READ COMMITTED 격리 수준이 지원되지 않습니다.  
  
## <a name="user-action"></a>사용자 동작  
 명시적 또는 암시적 READ COMMITTED 트랜잭션에서 메모리 최적화 테이블에 액세스할 때는 SNAPSHOT을 사용하여 테이블에 액세스합니다. 테이블 힌트 WITH (SNAPSHOT)을 사용 하 여 수행할 수 있습니다 (자세한 내용은 참조 [트랜잭션 격리 수준에 메모리 최적화 된 테이블에 대 한 지침이](../in-memory-oltp/memory-optimized-tables.md)) 또는 데이터베이스를 설정 하 여 MEMORY_OPTIMIZED_ELEVATE_TO_ 옵션 ON으로 스냅숏 (자세한 내용은 참조 [ALTER DATABASE SET 옵션 &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).  
  
## <a name="see-also"></a>관련 항목  
 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  