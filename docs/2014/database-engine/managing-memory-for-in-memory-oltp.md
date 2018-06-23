---
title: 메모리 내 OLTP에 대 한 메모리 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 365d51004820d3b8c18a9f7667e1328d5bc10143
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36089376"
---
# <a name="managing-memory-for-in-memory-oltp"></a>메모리 내 OLTP의 메모리 관리
  메모리 액세스에 최적화된 테이블을 사용하려면 모든 행과 인덱스를 메모리 내에 유지하는 데 충분한 메모리가 있어야 합니다. 메모리는 한정된 리소스이므로 시스템에서 메모리 사용량을 파악하고 관리해야 합니다. 이 섹션의 항목에서는 일반적인 메모리 사용 및 관리 시나리오를 다룹니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|섹션|Description|  
|-------------|-----------------|  
|[메모리 액세스에 최적화된 테이블에 필요한 메모리 예측](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|테이블에 필요한 메모리를 예측합니다.|  
|[메모리 액세스에 최적화된 테이블이 있는 데이터베이스를 리소스 풀에 바인딩](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|데이터베이스를 리소스 풀과 바인딩하기 위한 단계별 연습입니다.|  
|[메모리 사용량 모니터링 및 문제 해결](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|메모리 사용량을 모니터링하는 데 사용할 수 있는 도구입니다. 메모리 사용량이 너무 증가하는 경우 문제 해결도 다룹니다.|  
|[OOM(메모리 부족) 문제 해결](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|OOM(메모리 부족) 상황에서 복구하는 단계입니다.|  
|[데이터베이스를 복원하여 리소스 풀에 바인딩](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|[!INCLUDE[hek_2](../includes/hek-2-md.md)] 데이터베이스를 복원하고 명명된 리소스 풀에 바인딩하는 단계입니다.|  
|[메모리 내 OLTP 가비지 수집](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|삭제된 행에서 가비지 수집이 작동하는 방법을 이해합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  