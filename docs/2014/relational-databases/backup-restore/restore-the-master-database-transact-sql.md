---
title: master 데이터베이스 복원(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], restoring
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7834ce4de7b4fa788dcdfb72c9f38510a11a9fac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187013"
---
# <a name="restore-the-master-database-transact-sql"></a>master 데이터베이스 복원(Transact-SQL)
  이 항목에서는 전체 데이터베이스 백업에서 **master** 데이터베이스를 복원하는 방법에 대해 설명합니다.  
  
### <a name="to-restore-the-master-database"></a>master 데이터베이스를 복원하려면  
  
1.  서버 인스턴스를 단일 사용자 모드로 시작합니다.  
  
     단일 사용자 시작 매개 변수(**-m**)를 지정하는 방법은 [서버 시작 옵션 구성&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)을 참조하세요.  
  
2.  **master**의 전체 데이터베이스 백업을 복원하려면 다음 [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.  
  
     `RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`  
  
     REPLACE 옵션은 동일한 이름을 가진 데이터베이스가 이미 있는 경우에도 지정된 데이터베이스를 복원하도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 지시합니다. 이 경우 기존 데이터베이스는 삭제됩니다. 단일 사용자 모드에서는 [sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)에 RESTORE DATABASE 문을 입력하는 것이 좋습니다. 자세한 내용은 [sqlcmd 유틸리티 사용](../scripting/sqlcmd-use-the-utility.md)을 참조하세요.  
  
    > [!IMPORTANT]  
    >  **마스터** 를 복원한 후 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 종료되고 **sqlcmd** 프로세스가 종료됩니다. 서버 인스턴스를 다시 시작하기 전에 단일 사용자 시작 매개 변수를 제거하십시오. 자세한 내용은 [서버 시작 옵션 구성&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)을 참조하세요.  
  
3.  서버 인스턴스를 다시 시작하고 다른 데이터베이스 복원, 데이터베이스 연결 및 사용자 불일치 교정 등의 기타 복구 단계를 계속합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 기본 서버 인스턴스에 `master` 데이터베이스를 복원합니다. 이 예에서는 서버 인스턴스가 이미 단일 사용자 모드로 실행되고 있다고 가정합니다. 다음 예에서는 `sqlcmd` 를 시작하고 디스크 장치에서 `RESTORE DATABASE` 의 전체 데이터베이스 백업을 복원하는 `master` 문을 실행합니다. `Z:\SQLServerBackups\master.bak`  
  
> [!NOTE]  
>  명명된 인스턴스의 경우 **sqlcmd** 명령에 **-S***\<ComputerName>*\\*\<InstanceName>* 옵션을 지정해야 합니다.  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [전체 데이터베이스 복원&#40;단순 복구 모델&#41;](complete-database-restores-simple-recovery-model.md)   
 [전체 데이터베이스 복원&#40;전체 복구 모델&#41;](complete-database-restores-full-recovery-model.md)   
 [분리된 사용자 문제 해결&#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [데이터베이스 분리 및 연결&#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md)   
 [시스템 데이터베이스 다시 작성](../databases/system-databases.md)   
 [데이터베이스 엔진 서비스 시작 옵션](../../database-engine/configure-windows/database-engine-service-startup-options.md)   
 [SQL Server 구성 관리자](../sql-server-configuration-manager.md)   
 [시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md)   
 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [단일 사용자 모드로 SQL Server 시작](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
