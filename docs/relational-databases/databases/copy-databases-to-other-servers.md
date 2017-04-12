---
title: "데이터베이스를 다른 서버로 복사 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "서버 [SQL Server], 데이터베이스 복사"
  - "대량 내보내기 [SQL Server], 서버 간"
  - "데이터베이스 복사 [SQL Server]"
  - "데이터베이스 마이그레이션 [SQL Server]"
  - "데이터베이스 이동"
  - "데이터베이스 복사"
  - "대량 가져오기 [SQL Server], 서버 간"
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
caps.latest.revision: 42
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 42
---
# 데이터베이스를 다른 서버로 복사
  데이터베이스를 한 컴퓨터에서 다른 컴퓨터로 복사하는 기능은 경우에 따라 유용하게 사용됩니다(예: 테스트, 일관성 검사, 소프트웨어 개발, 보고서 실행, 미러 데이터베이스 만들기 또는 원격 분기 작업에서 사용할 수 있도록 데이터베이스 설정 등).  
  
 다음과 같은 여러 방법으로 데이터베이스를 복사할 수 있습니다.  
  
-   데이터베이스 복사 마법사 사용  
  
     데이터베이스 복사 마법사를 사용하여 서버 간에 데이터베이스를 복사 또는 이동하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 이후 버전으로 업그레이드할 수 있습니다. 자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.  
  
-   데이터베이스 백업 복원  
  
     전체 데이터베이스를 복사하려면 BACKUP 및 RESTORE [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다. 일반적으로 데이터베이스의 전체 백업 복원은 여러 가지 이유로 데이터베이스를 한 컴퓨터에서 다른 컴퓨터로 복사하는 데 사용됩니다. 백업 및 복원을 사용하여 데이터베이스를 복사하는 방법은 [백업 및 복원으로 데이터베이스 복사](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)를 참조하세요.  
  
    > [!NOTE]  
    >  데이터베이스 미러링에 사용할 미러 데이터베이스를 설정하려면 RESTORE DATABASE *<database_name>* WITH NORECOVERY를 사용하여 데이터베이스를 미러 서버로 복원해야 합니다. 자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)를 참조하세요.  
  
-   스크립트 생성 마법사를 사용하여 데이터베이스 게시  
  
     스크립트 생성 마법사를 사용하여 데이터베이스를 로컬 컴퓨터에서 웹 호스팅 공급자로 전송할 수 있습니다. 자세한 내용은 [스크립트 생성 및 게시 마법사](../../relational-databases/scripting/generate-and-publish-scripts-wizard.md)를 참조하세요.  
  
  