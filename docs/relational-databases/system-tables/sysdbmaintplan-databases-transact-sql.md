---
title: sysdbmaintplan_databases (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_databases
- sysdbmaintplan_databases_TSQL
dev_langs: TSQL
helpviewer_keywords: sysdbmaintplan_databases system table
ms.assetid: f8413a44-8fcc-4899-84f2-b4afe0f8ec08
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0948ed96497060fac61593b9fb424dfbd6492b78
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdbmaintplandatabases-transact-sql"></a>sysdbmaintplan_databases(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  이 테이블은에서 업그레이드 된 인스턴스에 대 한 기존 정보를 유지 하기 위해 포함 됩니다. 이전 버전의 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이후 버전에서는 이 테이블의 내용을 변경하지 마십시오. 이 테이블에 저장 되는 **msdb** 데이터베이스입니다.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**고유 식별자**|유지 관리 계획 ID입니다.|  
|**database_name**|**sysname**|데이터베이스 유지 관리 계획과 연관된 데이터베이스의 이름입니다.|  
  
  