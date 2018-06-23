---
title: '작업 속성: 새 작업 (알림 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 39dd7fe869b89b7793e2128c619beb4ec9c36a84
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36079681"
---
# <a name="job-properties-new-job-notifications-page"></a>작업 속성: 새 작업 (알림 페이지)
  이 페이지를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 작업이 완료되었을 때 수행할 동작을 설정할 수 있습니다.  
  
## <a name="options"></a>변수  
 **전자 메일**  
 작업이 완료되었을 때 전자 메일을 보내려면 이 옵션을 선택합니다. 이 옵션을 선택한 후 알릴 운영자와 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 알림을 트리거할 조건을 선택합니다.  
  
 **호출**  
 작업이 완료되었을 때 운영자의 호출기로 전자 메일을 보내려면 이 옵션을 선택합니다. 이 옵션을 선택한 후 알릴 운영자와 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 알림을 트리거할 조건을 지정합니다.  
  
 **Net Send**  
 작업이 완료되었을 때 Net Send를 사용하여 운영자에게 알리려면 이 옵션을 선택합니다. 이 옵션을 선택한 후 알릴 운영자와 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 알림을 트리거할 조건을 지정합니다.  
  
 **Windows 응용 프로그램 이벤트 로그에 쓰기**  
 작업이 완료되었을 때 응용 프로그램 이벤트 로그에 항목을 쓰려면 이 옵션을 선택합니다. 이 옵션을 선택한 후 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 항목을 쓰도록 할 조건을 지정합니다.  
  
 **자동으로 작업 삭제**  
 작업이 완료되었을 때 작업을 삭제하려면 이 옵션을 선택합니다. 이 옵션을 선택한 후 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 작업 삭제를 트리거할 조건을 지정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [작업 구현](implement-jobs.md)   
 [데이터베이스 메일을 사용하도록 SQL Server 에이전트 메일 구성](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  