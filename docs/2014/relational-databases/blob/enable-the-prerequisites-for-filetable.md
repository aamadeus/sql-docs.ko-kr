---
title: FileTable의 필수 구성 요소를 사용하도록 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], prerequisites
ms.assetid: 6286468c-9dc9-4eda-9961-071d2a36ebd6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6593b3d209ba04019c4b7e485cb25f2f35312dce
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201823"
---
# <a name="enable-the-prerequisites-for-filetable"></a>FileTable의 필수 구성 요소를 사용하도록 설정
  FileTable을 만들고 사용하기 위한 필수 구성 요소를 사용하도록 설정하는 방법에 대해 설명합니다.  
  
##  <a name="EnablePrereq"></a> FileTable의 필수 구성 요소를 사용하도록 설정  
 FileTable을 만들고 사용하기 위한 필수 구성 요소를 사용하도록 설정하려면 다음 항목을 설정합니다.  
  
-   **인스턴스 수준:**  
  
    -   [인스턴스 수준에서 FILESTREAM을 사용하도록 설정](#BasicsFilestream)  
  
-   **데이터베이스 수준:**  
  
    -   [데이터베이스 수준에서 FILESTREAM 파일 그룹 제공](#filegroup)  
  
    -   [데이터베이스 수준에서 비트랜잭션 액세스를 사용하도록 설정](#BasicsNTAccess)  
  
    -   [데이터베이스 수준에서 FileTable의 디렉터리 지정](#BasicsDirectory)  
  
##  <a name="BasicsFilestream"></a> 인스턴스 수준에서 FILESTREAM을 사용하도록 설정  
 FileTable은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 FILESTREAM 기능을 확장합니다. 따라서 FileTable을 만들고 사용하려면 먼저 Windows 수준과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 파일 I/O 액세스를 위해 FILESTREAM을 사용하도록 설정해야 합니다.  
  
###  <a name="HowToFilestream"></a> 방법: 인스턴스 수준에서 FILESTREAM을 사용하도록 설정  
 FILESTREAM을 사용하도록 설정하는 방법은 [FILESTREAM 사용 및 구성](enable-and-configure-filestream.md)을 참조하세요.  
  
 호출 하는 경우 `sp_configure` 인스턴스 수준에서 FILESTREAM을 사용 하도록 설정 하려면 filestream_access_level 옵션을 2로 설정 해야 합니다. 자세한 내용은 [FILESTREAM 액세스 수준 서버 구성 옵션](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md)을 참조하세요.  
  
###  <a name="firewall"></a> 방법: 방화벽을 통해 FILESTREAM 허용  
 방화벽을 통해 FILESTREAM을 허용하는 방법은 [Configure a Firewall for FILESTREAM Access](configure-a-firewall-for-filestream-access.md)을 참조하세요.  
  
##  <a name="filegroup"></a> 데이터베이스 수준에서 FILESTREAM 파일 그룹 제공  
 데이터베이스에서 FileTables를 만들려면 데이터베이스에 FILESTREAM 파일 그룹이 있어야 합니다. 이 필수 구성 요소에 대한 자세한 내용은 [FILESTREAM 사용 데이터베이스 만들기](create-a-filestream-enabled-database.md)를 참조하세요.  
  
##  <a name="BasicsNTAccess"></a> 데이터베이스 수준에서 비트랜잭션 액세스를 사용하도록 설정  
 FileTable을 사용하면 Windows 응용 프로그램에서 트랜잭션 없이도 FILESTREAM 데이터에 대한 Windows 파일 핸들을 가져올 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장된 파일에 대해 이 비트랜잭션 액세스를 허용하려면 FileTable을 포함할 각 데이터베이스의 데이터베이스 수준에서 원하는 비트랜잭션 액세스 수준을 지정해야 합니다.  
  
###  <a name="HowToCheckAccess"></a> 방법: 데이터베이스에 비트랜잭션 액세스가 사용하도록 설정되어 있는지 확인  
 카탈로그 뷰 [sys.database_filestream_options&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)를 쿼리하고 **non_transacted_access** 및 **non_transacted_access_desc** 열을 확인합니다.  
  
```tsql  
SELECT DB_NAME(database_id), non_transacted_access, non_transacted_access_desc  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="HowToNTAccess"></a> 방법: 데이터베이스 수준에서 비트랜잭션 액세스를 사용하도록 설정  
 사용 가능한 비트랜잭션 액세스 수준은 FULL, READ_ONLY 및 OFF입니다.  
  
 **Transact-SQL을 사용하여 비트랜잭션 액세스 수준 지정**  
 -   **새 데이터베이스를 만들 경우** **NON_TRANSACTED_ACCESS** FILESTREAM 옵션을 사용하여 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 문을 호출합니다.  
  
    ```tsql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
-   **기존 데이터베이스를 변경할 경우** **NON_TRANSACTED_ACCESS** FILESTREAM 옵션을 사용하여 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 문을 호출합니다.  
  
    ```tsql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' )  
    ```  
  
 **SQL Server Management Studio를 사용하여 비트랜잭션 액세스 수준 지정**  
 **데이터베이스 속성** 대화 상자의 **옵션** 페이지에 있는 **FILESTREAM 비트랜잭션 액세스** 필드에서 비트랜잭션 액세스 수준을 지정할 수 있습니다. 이 대화 상자에 대한 자세한 내용은 [데이터베이스 속성&#40;옵션 페이지&#41;](../databases/database-properties-options-page.md)을 참조하세요.  
  
##  <a name="BasicsDirectory"></a> 데이터베이스 수준에서 FileTable의 디렉터리 지정  
 데이터베이스 수준에서 파일에 대한 비트랜잭션 액세스를 사용하도록 설정할 경우 필요에 따라 **DIRECTORY_NAME** 옵션을 사용하여 디렉터리 이름도 함께 제공할 수 있습니다. 비트랜잭션 액세스를 사용하도록 설정할 때 디렉터리 이름을 제공하지 않은 경우 나중에 해당 이름을 제공해야 데이터베이스에 FileTable을 만들 수 있습니다.  
  
 FileTable 폴더 계층 구조에서 이 데이터베이스 수준 디렉터리는 인스턴스 수준에서 FILESTREAM에 대해 지정된 공유 이름의 자식이 되고 데이터베이스에 만들어진 FileTable의 부모가 됩니다. 자세한 내용은 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)을 참조하세요.  
  
###  <a name="HowToDirectory"></a> 방법: 데이터베이스 수준에서 FileTable의 디렉터리 지정  
 지정한 이름은 데이터베이스 수준 디렉터리의 인스턴스 전체에서 고유해야 합니다.  
  
 **Transact-SQL을 사용하여 FileTable의 디렉터리 지정**  
 -   **새 데이터베이스를 만들 경우** **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 문을 호출합니다.  
  
    ```tsql  
    CREATE DATABASE database_name  
        WITH FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   **기존 데이터베이스를 변경할 경우** **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 문을 호출합니다. 이러한 옵션을 사용하여 디렉터리 이름을 변경할 경우 데이터베이스가 단독으로 잠겨 있고 열려 있는 파일 핸들이 없어야 합니다.  
  
    ```tsql  
    ALTER DATABASE database_name  
        SET FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   **데이터베이스를 연결할 경우** **FOR ATTACH** 옵션 및 **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) 문을 호출합니다.  
  
    ```tsql  
    CREATE DATABASE database_name  
        FOR ATTACH WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
-   **데이터베이스를 복원할 경우** **DIRECTORY_NAME** FILESTREAM 옵션을 사용하여 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) 문을 호출합니다.  
  
    ```tsql  
    RESTORE DATABASE database_name  
        WITH FILESTREAM ( DIRECTORY_NAME = N'directory_name' );  
    GO  
    ```  
  
 **SQL Server Management Studio를 사용하여 FileTable의 디렉터리 지정**  
 **데이터베이스 속성** 대화 상자의 **옵션** 페이지에 있는 **FILESTREAM 디렉터리 이름** 필드에서 디렉터리 이름을 지정할 수 있습니다. 이 대화 상자에 대한 자세한 내용은 [데이터베이스 속성&#40;옵션 페이지&#41;](../databases/database-properties-options-page.md)을 참조하세요.  
  
###  <a name="viewnames"></a> 방법: 인스턴스에 대한 기존 디렉터리 이름 보기  
 인스턴스의 기존 디렉터리 이름 목록을 보려면 카탈로그 뷰 [sys.database_filestream_options&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)를 쿼리하고 **filestream_database_directory_name** 열을 확인합니다.  
  
```tsql  
SELECT DB_NAME ( database_id ), directory_name  
    FROM sys.database_filestream_options;  
GO  
```  
  
###  <a name="ReqDirectory"></a> 데이터베이스 수준 디렉터리에 대한 요구 사항 및 제한 사항  
  
-   **CREATE DATABASE** 또는 **ALTER DATABASE** 를 호출할 때 옵션으로 **DIRECTORY_NAME**을 설정할 수 있습니다. **DIRECTORY_NAME**의 값을 지정하지 않으면 디렉터리 이름은 null로 유지됩니다. 그러나 데이터베이스 수준에서 **DIRECTORY_NAME** 의 값을 지정하기 전까지는 데이터베이스에 FileTable을 만들 수 없습니다.  
  
-   제공하는 디렉터리 이름은 올바른 디렉터리 이름에 대한 파일 시스템 요구 사항을 따라야 합니다.  
  
-   데이터베이스에 FileTable이 포함되어 있으면 **DIRECTORY_NAME** 을 다시 null 값으로 설정할 수 없습니다.  
  
-   데이터베이스를 연결하거나 복원할 때 대상 인스턴스에 이미 있는 **DIRECTORY_NAME** 값이 새 데이터베이스에 있으면 작업이 실패합니다. **CREATE DATABASE FOR ATTACH** 또는 **RESTORE DATABASE** 를 호출할 때 **DIRECTORY_NAME**에 고유한 값을 지정해야 합니다.  
  
-   기존 데이터베이스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 경우 **DIRECTORY_NAME** 값은 null입니다.  
  
-   데이터베이스 수준에서 비트랜잭션 액세스를 사용하거나 사용하지 않도록 설정할 때 디렉터리 이름이 지정되었는지 여부나 디렉터리 이름이 고유한지 여부는 확인되지 않습니다.  
  
-   FileTable에 대해 사용하도록 설정된 데이터베이스를 삭제하면 해당 데이터베이스에 있는 데이터베이스 수준 디렉터리와 모든 디렉터리 구조가 제거됩니다.  
  
  
