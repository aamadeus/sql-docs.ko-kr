---
title: Azure Data Studio를 사용 하 여 데이터베이스를 백업 및 복원 | Microsoft Docs
description: Azure Data Studio를 사용 하 여 데이터베이스를 백업 및 복원 하는 방법을 알아봅니다
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2d9b4cbee5ab4da44961927809bf1fb4c771cc1
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49355914"
---
# <a name="backup-and-restore-using-includename-sosincludesname-sos-shortmd"></a>백업 및 복원을 사용 하 여 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

이 자습서에서 [!INCLUDE[name-sos](../includes/name-sos-short.md)] 사용법을 알아봅니다.
> [!div class="checklist"]
> * 데이터베이스 백업 
> * 백업 상태를 보려면
> * 백업 하는 데 사용 되는 스크립트를 생성 합니다.
> * 데이터베이스 복원
> * 복원 작업의 상태를 보려면

## <a name="prerequisites"></a>사전 요구 사항

이 자습서에서는 SQL Server *TutorialDB*합니다. *TutorialDB* 데이터베이스를 만들려면, 다음 빠른 시작 중 하나를 수행합니다.

- [연결 및 SQL Server를 사용 하 여 쿼리 [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)


## <a name="backup-a-database"></a>데이터베이스 백업

1. TutorialDB 데이터베이스 대시보드를 엽니다 (엽니다는 **서버** 사이드바 (**CTRL + G**)를 확장 하 고 **데이터베이스**를 마우스 오른쪽 단추로 클릭 **TutorialDB**, 선택한 **관리**). 

2. 열기는 **Backup database** 대화 상자 (클릭 **백업** 에 **작업** 위젯).

   ![작업 위젯](./media/tutorial-backup-restore-sql-server/tasks.png)

3. 이 자습서에서는 기본 백업 옵션, 클릭 **백업**합니다.
   ![백업 대화 상자](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

클릭 한 후 **백업**서 **Backup database** 대화 사라지고 백업 프로세스가 시작 됩니다.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>백업 상태를 확인 하 고 백업 스크립트를 보려면

1. 엽니다는 **작업 기록** 사이드바에 시계 아이콘을 클릭 하 여는 *작업 모음* 누르거나 **CTRL + T**합니다.

   ![작업 기록](./media/tutorial-backup-restore-sql-server/task-history.png)

2. 백업 스크립트를 편집기에서를 보려면 마우스 오른쪽 단추로 클릭 **성공 하는 데이터베이스 백업** 선택한 **스크립트**합니다.

   ![백업 스크립트](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>백업 파일에서 데이터베이스를 복원 합니다.


1. 엽니다는 **서버** 사이드바 (**CTRL + G**), 서버를 마우스 오른쪽 단추로 **관리**합니다. 

2. 열기는 **데이터베이스 복원** 대화 상자 (클릭 **복원** 에 **작업** 위젯).

2. 선택 **백업 파일** 에 **에서 복원** 필드입니다. 

3. 에 있는 줄임표 (...)를 **백업 파일 경로** 의 최신 백업 파일을 선택한 필드 *TutorialDB*합니다.

3. 형식 **TutorialDB_Restored** 에 **대상 데이터베이스** 필드에 **대상** 새 데이터베이스로 복원할 백업 파일에 섹션.

   ![복원(restore)](./media/tutorial-backup-restore-sql-server/restore.png)

4. 클릭 **복원**

5. 복원 작업의 상태를 확인 하려면 키를 누릅니다 **CTRL + T** 열려는 합니다 **작업 기록** 세로 막대입니다.

   ![복원(restore)](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


이 자습서에서는 학습 하는 방법.
> [!div class="checklist"]
> * 데이터베이스 백업 
> * 백업 상태를 보려면
> * 백업 하는 데 사용 되는 스크립트를 생성 합니다.
> * 데이터베이스 복원
> * 복원 작업의 상태를 보려면

