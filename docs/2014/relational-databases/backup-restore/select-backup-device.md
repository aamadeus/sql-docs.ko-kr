---
title: 백업 장치 선택 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6135239b182c66ae4622dcf9af704fb30f167f6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36090220"
---
# <a name="select-backup-device"></a>백업 장치 선택
  **백업 장치 선택** 대화 상자를 사용하여 복원 작업에 사용할 논리적 백업 장치를 선택할 수 있습니다.  
  
 논리적 백업 장치는 운영 체제가 제공하는 물리적 장치인 테이프 드라이브 또는 디스크 드라이브에 해당하는 사용자 정의된 논리적 장치입니다.  
  
> [!NOTE]  
>  백업에 여러 개의 백업 장치가 사용될 경우 이러한 장치는 하나로 일치해야 합니다.  
  
 **SQL Server Management Studio를 사용하여 백업 장치의 내용을 보려면**  
  
-   [백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [논리적 백업 장치의 속성 및 내용 보기&#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>변수  
 **백업 장치**  
 목록 상자에서 복원할 논리적 백업 장치의 이름을 선택합니다.  
  
 백업 장치의 내용을 보는 방법은 [논리적 백업 장치의 속성 및 내용 보기&#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)를 참조하세요.  
  
## <a name="remarks"></a>Remarks  
 목록에서 찾고 있는 백업이 포함된 논리적 백업 장치가 보이지 않을 경우 백업은 하나 이상의 파일 또는 테이프 드라이브에 직접 기록되었을 수 있습니다. 이 경우에는 **백업 장치 선택** 대화 상자를 취소하고 **백업 지정** 대화 상자의 **백업 미디어** 목록 상자에서 **파일** 또는 **테이프** 를 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [백업 장치&#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  