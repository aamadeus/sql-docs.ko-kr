---
title: sysmail_help_status_sp (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_status_sp
- sysmail_help_status_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_status_sp
ms.assetid: b44277c6-81e8-4b4d-85b3-a2f04d602e7a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c08985b4fe50a657c08de40f112776cf064b2846
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614268"
---
# <a name="sysmailhelpstatussp-transact-sql"></a>sysmail_help_status_sp(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  데이터베이스 메일 큐의 상태를 표시합니다. 사용 하 여 **sysmail_start_sp** 데이터베이스 메일 큐를 시작 하 고 **sysmail_stop_sp** 데이터베이스 메일 큐를 중지 하려면.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sysmail_help_status_sp  
```  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-set"></a>결과 집합  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**상태**|**nvarchar(7)**|데이터베이스 메일의 상태입니다. 가능한 값은 **STARTED** 하 고 **STOPPED**합니다.|  
  
## <a name="permissions"></a>사용 권한  
 기본적으로의 멤버만 합니다 **sysadmin** 고정된 서버 역할에서이 절차를 사용할 수 있습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 데이터베이스 메일의 상태를 표시합니다.  
  
```  
EXECUTE msdb.dbo.sysmail_help_status_sp ;  
GO  
```  
  
 결과 집합은 다음과 같습니다.  
  
```  
Status  
-------  
STARTED  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 메일 외부 프로그램](../../relational-databases/database-mail/database-mail-external-program.md)   
 [sysmail_start_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [sysmail_stop_sp&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)  
  
  
