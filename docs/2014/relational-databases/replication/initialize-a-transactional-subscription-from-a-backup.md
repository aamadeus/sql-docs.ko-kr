---
title: (복제 TRANSACT-SQL 프로그래밍) 백업에서 트랜잭션 구독 초기화 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8996ad69528e739515166311d7de9eae657952c4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165673"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a>백업에서 트랜잭션 구독 초기화(복제 Transact-SQL 프로그래밍)
  일반적으로 트랜잭션 게시에 대한 구독은 스냅숏을 사용하여 초기화하지만 복제 저장 프로시저를 사용하여 백업에서 구독을 초기화할 수도 있습니다. 자세한 내용은 [Initialize a Transactional Subscription Without a Snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)에서 수동으로 구독을 초기화하는 방법에 대해 설명합니다.  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a>백업에서 트랜잭션 구독자를 초기화하려면  
  
1.  기존 게시의 경우 게시 데이터베이스의 게시자에서 [sp_helppublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)을 실행하여 게시가 백업에서 초기화하는 기능을 지원하는지 확인합니다. 결과 집합에서 **allow_initialize_from_backup** 값을 확인합니다.  
  
    -   값이 **1**이면 게시에서 이 기능을 지원하는 것입니다.  
  
    -   값이 **0**이면 게시 데이터베이스의 게시자에서 [sp_changepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행합니다. 값을 지정 **allow_initialize_from_backup** 에 대 한 **@property** 값 `true` 에 대 한 **@value**합니다.  
  
2.  새 게시의 경우 게시 데이터베이스의 게시자에서 [sp_addpublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)을 실행합니다. 값을 지정 `true` 에 대 한 **allow_initialize_from_backup**합니다. 자세한 내용은 [Create a Publication](publish/create-a-publication.md)를 참조하세요.  
  
    > [!WARNING]  
    >  구독자 데이터가 누락되는 것을 방지하려면 **에서** sp_addpublication `@allow_initialize_from_backup = N'true'`을 사용할 때 항상 `@immediate_sync = N'true'`를 사용하십시오.  
  
3.  [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) 문을 사용하여 게시 데이터베이스의 백업을 만듭니다.  
  
4.  [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 문을 사용하여 구독자에서 백업을 복원합니다.  
  
5.  게시 데이터베이스의 게시자에서 [sp_addsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) 저장 프로시저를 실행합니다. 다음 매개 변수를 지정합니다.  
  
    -   **@sync_type** - **initialize with backup**을 참조하세요.  
  
    -   **@backupdevicetype** - 백업 장치의 유형: **논리** (기본값) **디스크**또는 **테이프**을 참조하세요.  
  
    -   **@backupdevicename** - 복원에 사용할 논리적 또는 물리적 백업 장치  
  
         논리적 장치의 경우 **sp_addumpdevice** 를 사용하여 장치를 만들 때 지정한 백업 장치의 이름을 지정합니다.  
  
         물리적 장치의 경우 `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` 또는 `TAPE = '\\.\TAPE0'`과 같이 전체 경로와 파일 이름을 지정합니다.  
  
    -   (옵션) **@password** - 백업 장치를 만들 때 제공한 암호  
  
    -   (옵션) **@mediapassword** - 미디어 세트를 포맷할 때 제공한 암호  
  
    -   (옵션) **@fileidhint** - 복원되는 백업 세트에 대한 식별자. 예를 들어 **1** 을 지정하면 백업 미디어의 첫 번째 백업 세트를 나타내고 **2** 를 지정하면 두 번째 백업 세트를 나타냅니다.  
  
    -   (테이프 장치 옵션) **@unload** - 복원이 완료된 후 드라이브에서 테이프를 언로드해야 하는 경우 **1** (기본값), 언로드하지 않아야 하는 경우 **0** 을 지정합니다.  
  
6.  (옵션) 끌어오기 구독의 경우 구독 데이터베이스의 구독자에서 [sp_addpullsubscription&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) 및 [sp_addpullsubscription_agent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)를 실행합니다. 자세한 내용은 [끌어오기 구독 만들기](create-a-pull-subscription.md)를 참조하세요.  
  
7.  (옵션) 배포 에이전트를 시작합니다. 자세한 내용은 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) 또는 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md)   
 [SQL Server 데이터베이스 백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
