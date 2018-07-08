---
title: 미러된 미디어 세트에 백업(TRANSACT-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fc43a5d-dfd6-4c53-a4ef-3c8da23ccc81
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ee57f4caeba9747e3d4d9b1ac8577d7bf0ca486
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36184510"
---
# <a name="back-up-to-a-mirrored-media-set-transact-sql"></a>미러된 미디어 세트에 백업(TRANSACT-SQL)
  이 항목에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)][데이터베이스를 백업할 때](/sql/t-sql/statements/backup-transact-sql) BACKUP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문을 사용하여 미러된 미디어 세트를 지정하는 방법에 대해 설명합니다. BACKUP 문에서 TO 절에 첫 번째 미러를 지정합니다. 그런 다음 해당 MIRROR TO 절에 각 미러를 지정합니다. TO절과 MIRROR TO 절은 같은 개수와 유형의 백업 장치를 지정해야 합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 이전 그림에 표시된 미러된 미디어 세트를 만들고 두 미러 모두에 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스를 백업합니다.  
  
```  
BACKUP DATABASE AdventureWorks2012  
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1'  
MIRROR TO TAPE = '\\.\tape2', TAPE = '\\.\tape3'  
WITH  
    FORMAT,  
    MEDIANAME = 'AdventureWorks2012Set1';  
GO  
```  
  
## <a name="related-tasks"></a>관련 작업  
 **미러된 백업에서 복원하려면**  
  
-   [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
## <a name="see-also"></a>관련 항목  
 [BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [미러된 백업 미디어 세트&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)  
  
  