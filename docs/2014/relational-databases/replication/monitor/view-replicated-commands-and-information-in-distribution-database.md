---
title: 복제 된 명령 및 기타 정보 (복제 TRANSACT-SQL 프로그래밍) 배포 데이터베이스에서 보기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- sp_browsereplcmds
- transactional replication, monitoring
- distribution databases [SQL Server replication], viewing replicated commands
- viewing replicated commands
ms.assetid: 9c20acec-8fab-4483-b9c1-dfe3768f85dd
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c902d09512ae0c3ede9a7831908c41ab704628f3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091053"
---
# <a name="view-replicated-commands-and-other-information-in-the-distribution-database-replication-transact-sql-programming"></a>배포 데이터베이스의 복제된 명령 및 기타 정보 보기(복제 Transact-SQL 프로그래밍)
  트랜잭션 복제를 사용하는 경우 트랜잭션 명령은 배포 에이전트에서 해당 명령을 모든 구독자에 전파하거나 구독자의 배포 에이전트에서 변경 내용을 끌어올 때까지 배포 데이터베이스에 저장됩니다. 이와 같이 배포 데이터베이스에서 보류 중인 명령은 복제 저장 프로시저를 사용하여 프로그래밍 방식으로 볼 수 있습니다. 자세한 내용은 [복제 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)를 참조하세요.  
  
### <a name="to-view-replicated-commands-from-all-transactional-publications-in-the-distribution-database"></a>배포 데이터베이스의 모든 트랜잭션 게시에서 복제된 명령을 보려면  
  
1.  배포 데이터베이스의 배포자에서 [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)를 실행합니다.  
  
### <a name="to-view-replicated-commands-in-the-distribution-database-from-a-specific-article-or-from-a-specific-database-published-using-transactional-replication"></a>트랜잭션 복제를 사용하여 게시된 특정 데이터베이스 또는 특정 아티클에서 배포 데이터베이스의 복제된 명령을 보려면  
  
1.  (옵션) 게시 데이터베이스의 게시자에서 [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)을 실행합니다. **@publication** 및 **@article**을 지정합니다. 결과 집합의 **article id** 값을 확인합니다.  
  
2.  배포 데이터베이스의 배포자에서 [sp_browsereplcmds](/sql/relational-databases/system-stored-procedures/sp-browsemergesnapshotfolder-transact-sql)를 실행합니다. (옵션) **@article_id**을 참조하세요. (옵션) **@publisher_database_id**에 게시 데이터베이스의 ID를 지정합니다. 이 ID는 **sys.databases** 카탈로그 뷰의 [database_id](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 열에서 얻을 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [프로그래밍 방식으로 복제 모니터링](monitoring-replication-overview.md)  
  
  