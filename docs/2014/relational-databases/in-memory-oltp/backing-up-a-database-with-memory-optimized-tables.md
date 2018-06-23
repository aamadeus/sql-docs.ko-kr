---
title: 메모리 액세스에 최적화된 테이블이 포함된 데이터베이스 백업 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83d47694-e56d-4dae-b54e-14945bf8ba31
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 6d9f0a4fd663cfcd6bf3e3bad827429bc2f0133b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36090430"
---
# <a name="backing-up-a-database-with-memory-optimized-tables"></a>메모리 액세스에 최적화된 테이블이 포함된 데이터베이스 백업
  메모리 액세스에 최적화된 테이블은 일반적인 데이터베이스 백업의 일부로 백업됩니다. 디스크 기반 테이블의 경우 저장소 손상을 검색하기 위해 데이터베이스 백업의 일부로 데이터 및 델타 파일 쌍의 CHECKSUM 유효성이 검사됩니다.  
  
> [!NOTE]  
>  백업하는 동안 메모리 최적화 파일 그룹의 하나 이상의 파일에서 CHECKSUM 오류가 발견되면 데이터베이스를 복원 및 다시 시작할 수 없습니다. 이 경우 마지막 양호한 백업으로 데이터베이스를 복원해야 합니다. 백업이 없는 경우 메모리 최적화 테이블 및 디스크 기반 테이블에서 데이터를 내보낼 수 있으며, 데이터베이스를 삭제하고 다시 만든 뒤 다시 로드할 수 있습니다.  
  
 메모리 최적화 테이블이 하나 이상인 데이터베이스의 전체 백업은 디스크 기반 테이블의 할당된 저장소(있는 경우), 활성 트랜잭션 로그, 메모리 최적화 테이블의 데이터 및 델타 파일 쌍(검사점 파일 쌍이라고도 함)으로 구성됩니다. 그러나 [메모리 최적화 테이블에 대한 내구성](memory-optimized-tables.md)에 설명된 대로 메모리 최적화 테이블에서 사용하는 저장소는 메모리 내의 해당 크기보다 훨씬 클 수 있으며, 이는 데이터베이스 백업의 크기에 영향을 미칩니다.  
  
## <a name="full-database-backup"></a>전체 데이터베이스 백업  
 여기에서는 디스크 기반 테이블의 백업이 동일하기 때문에 메모리 최적화 영구 테이블이 포함된 데이터베이스의 백업을 중점적으로 살펴봅니다. 메모리 최적화 파일 그룹의 검사점 파일 쌍은 다양한 상태에 있을 수 있습니다. 아래의 표에서는 백업되는 파일의 부분에 대해 설명합니다.  
  
|검사점 파일 쌍 상태|백업|  
|--------------------------------|------------|  
|PRECREATED|파일 메타데이터만|  
|UNDER CONSTRUCTION|파일 메타데이터만|  
|활성|파일 메타데이터와 사용된 바이트|  
|MERGE SOURCE|파일 메타데이터와 사용된 바이트|  
|MERGE TARGET|파일 메타데이터만|  
|REQUIRED FOR BACKUP/HA|파일 메타데이터와 사용된 바이트|  
|IN TRANSITION TO TOMBSTONE|파일 메타데이터만|  
|TOMBSTONE|파일 메타데이터만|  
  
 메모리 최적화 테이블이 하나 이상 포함된 데이터베이스 백업의 크기는 일반적으로 메모리 내의 해당 크기보다 크지만 디스크상 저장소보다는 작습니다. 추가 크기는 삭제된 행 수와 작업에 간접적으로 의존하는 REQUIRED FOR BACKUP/HA 및 MERGE SOURCE 상태의 검사점 파일 쌍 수에 따라 달라집니다. 검사점 파일 쌍의 상태에 대 한 설명은 참조 하십시오. [sys.dm_db_xtp_checkpoint_files &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql)합니다.  
  
### <a name="estimating-size-of-full-database-backup"></a>전체 데이터베이스 백업의 크기 예측  
  
> [!IMPORTANT]  
>  메모리 내 OLTP에 대한 백업 크기를 추정하려면 BackupSizeInBytes 값을 사용하지 않는 것이 좋습니다.  
  
 첫 번째 작업 시나리오는 대부분 삽입에 해당합니다. 이 시나리오에서 대부분의 데이터 파일은 활성 상태이고 완전히 로드되며 삭제된 행이 매우 적습니다. 데이터베이스 백업의 크기는 메모리 내의 데이터 크기에 가깝습니다.  
  
 두 번째 작업 시나리오는 빈번한 삽입, 삭제 및 업데이트 작업에 해당합니다. 최악의 경우 각 검사점 파일 쌍은 삭제된 행을 고려한 후 50% 로드됩니다. 따라서 데이터베이스 백업의 크기는 적어도 메모리 내 데이터 크기의 2배입니다. 또한 데이터베이스 백업의 크기에 추가될 MERGE SOURCE 및 REQUIRED FOR BACKUP/HA 상태의 몇몇 검사점 파일 쌍이 있습니다.  
  
## <a name="differential-backups-of-databases-with-memory-optimized-tables"></a>메모리 액세스에 최적화된 테이블이 있는 데이터베이스의 차등 백업  
 메모리 최적화 테이블의 저장소는 [메모리 최적화 테이블에 대한 내구성](memory-optimized-tables.md)에 설명된 대로 데이터 및 델타 파일로 구성되어 있습니다. 메모리 최적화 테이블이 있는 데이터베이스의 차등 백업에는 다음 데이터가 포함됩니다.  
  
-   메모리 최적화 테이블이 있어도 디스크를 기반으로 테이블을 저장하는 파일 차등 백업은 영향을 받지 않습니다.  
  
-   활성 트랜잭션 로그는 전체 데이터베이스 백업에서 동일합니다.  
  
-   메모리 최적화 데이터 파일 그룹의 경우 차등 백업은 전체 데이터베이스 백업과 동일한 알고리즘을 사용하여 백업 데이터 및 델타 파일을 식별하지만, 그 후에 다음과 같이 하위 집합을 필터링합니다.  
  
    -   데이터 파일에 새로 삽입된 행이 있고 가득 찬 경우 이 데이터 파일은 닫히고 읽기 전용으로 표시됩니다. 데이터 파일은 마지막 전체 데이터베이스 백업 후 닫힌 경우에만 백업됩니다. 차등 백업은 업데이트 및 삭제 시나리오 예외 조항이 있는 마지막 전체 데이터베이스 백업 이후에 삽입된 행을 포함하는 백업 데이터 파일만 백업하는데, 이때 삽입된 행 중 일부가 이미 가비지 수집으로 표시되었거나 이미 가비지 수집되었을 수 있습니다.  
  
    -   델타 파일은 삭제된 데이터 행에 대한 참조를 저장합니다. 향후의 트랜잭션에서 행을 삭제할 수 있으므로 델타 파일은 언제든지 수정 가능하며 절대로 닫히지 않습니다. 델타 파일은 항상 백업됩니다. 델타 파일은 일반적으로 10% 미만의 저장소를 사용하므로 차등 백업의 크기에 미치는 영향이 최소화됩니다.  
  
 메모리 최적화 테이블이 데이터베이스 크기의 상당 부분을 차지하는 경우 차등 백업으로 데이터베이스 백업의 크기를 대폭 줄일 수 있습니다.  
  
 일반적인 OLTP 작업의 경우 차등 백업이 전체 데이터베이스 백업보다 상당히 작습니다.  
  
## <a name="see-also"></a>관련 항목  
 [메모리 액세스에 최적화된 테이블의 백업, 복원 및 복구](restore-and-recovery-of-memory-optimized-tables.md)  
  
  