---
title: "작업 구현 | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 30b61e4aa32828763d4531c53cb7f308a926798b
ms.lasthandoff: 04/11/2017

---
# <a name="implement-jobs"></a>작업 구현
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트 작업을 사용하여 일상적인 관리 태스크를 자동화하고 정기적으로 실행함으로써 좀 더 효율적인 관리를 할 수 있습니다.  
  
작업이란 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트가 순차적으로 수행하는 일련의 지정된 작업입니다. 작업은 [!INCLUDE[tsql](../../includes/tsql_md.md)] 스크립트, 명령줄 응용 프로그램, Microsoft ActiveX 스크립트, Integration Services 패키지, Analysis Services 명령 및 쿼리 또는 복제 태스크를 실행하는 등 광범위한 활동을 수행합니다. 작업은 반복적인 태스크나 예약 가능한 작업을 실행하고, 경고를 생성하여 작업 상태를 사용자에게 자동으로 알림으로써 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 관리를 간단하게 만들어 줍니다.  
  
작업을 수동으로 실행하거나 일정에 따라 또는 경고에 응답하여 실행되도록 구성할 수 있습니다.  
  
## <a name="related-tasks"></a>관련 작업  
  
|||  
|-|-|  
|**Description**|**항목**|  
|작업을 만들고 소유권을 할당하는 방법에 대해 설명합니다.|[작업 만들기](../../ssms/agent/create-jobs.md)|  
|범주에 작업을 구성하는 방법에 대해 설명합니다.|[작업 구성](../../ssms/agent/organize-jobs.md)|  
|사용자가 만들 수 있는 작업 단계의 여러 가지 종류와 관리하는 방법에 대해 설명합니다.|[작업 단계 관리](../../ssms/agent/manage-job-steps.md)|  
|작업의 실행 시작 시간 및 실행 빈도를 정의하는 방법에 대해 설명합니다.|[일정을 만들고 작업에 연결](../../ssms/agent/create-and-attach-schedules-to-jobs.md)|  
|예약 없이 작업을 수동으로 실행하는 방법에 대해 설명합니다.|[작업 실행](../../ssms/agent/run-jobs.md)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트가 작업에 응답하도록 구성하는 방법에 대해 설명합니다. 예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트를 구성하여 작업이 끝났을 때 관리자에게 통보하도록 구성할 수 있습니다.|[작업 응답 지정](../../ssms/agent/specify-job-responses.md)|  
|기존 작업을 보거나 실행 시 작업 기록을 보거나 작업을 수정하는 방법에 대해 설명합니다.|[작업 보기 또는 수정](../../ssms/agent/view-or-modify-jobs.md)|  
|작업을 삭제하는 방법에 대해 설명합니다.|[작업 삭제](../../ssms/agent/delete-jobs.md)|  
  
## <a name="see-also"></a>참고 항목  
[SQL Server 에이전트 보안 구현](../../ssms/agent/implement-sql-server-agent-security.md)  
  
