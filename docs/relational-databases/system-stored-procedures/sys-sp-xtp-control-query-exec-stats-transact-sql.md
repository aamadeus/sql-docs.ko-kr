---
title: sys.sp_xtp_control_query_exec_stats (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/13/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_query_exec_stats_TSQL
- sys.sp_xtp_control_query_exec_stats
dev_langs: TSQL
helpviewer_keywords: sys.sp_xtp_control_query_exec_stats
ms.assetid: 4838125d-ad1e-479e-b7d2-42655e8f4f02
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f4bcc1bb453783a38c4b23e6526de1a804bde8f1
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2017
---
# <a name="sysspxtpcontrolqueryexecstats-transact-sql"></a>sys.sp_xtp_control_query_exec_stats(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  인스턴스에 대해 고유하게 컴파일된 모든 저장 프로시저 또는 고유하게 컴파일된 특정 저장 프로시저에 대해 쿼리별 통계 컬렉션을 설정합니다.  
  
 통계 컬렉션을 설정하면 성능이 저하됩니다. 한 개나 몇 개의 고유하게 컴파일된 저장 프로시저 문제만 해결하면 되는 경우에는 해당하는 몇 개의 고유하게 컴파일된 저장 프로시저에 대해서만 통계 컬렉션을 설정할 수 있습니다.  
  
 고유 하 게 컴파일된 모든 저장된 프로시저에 대 한 프로시저 수준 통계 컬렉션을 사용 하려면 참조 [sys.sp_xtp_control_proc_exec_stats&#40; Transact SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>구문  
  
```  
sp_xtp_control_query_exec_stats [ [ @new_collection_value = ] collection_value ],  
[ [ @database_id = ] database_id   
[ , [ @xtp_object_id = ] procedure_id ] ,   
[ @old_collection_value] ]  
```  
  
## <a name="arguments"></a>인수  
 @new_collection_value= *값*  
 프로시저 수준 통계 컬렉션이 설정(1)되었는지 아니면 해제(0)되었는지를 결정합니다.  
  
 @new_collection_value때 0으로 설정 되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시작 합니다.  
  
 @database_id= = *database_id*, @xtp_object_id = *procedure_id*  
 고유하게 컴파일된 저장 프로시저에 대한 데이터베이스 ID 및 개체 ID입니다. 인스턴스에 대 한 통계 컬렉션을 설정 하는 경우 ([sys.sp_xtp_control_proc_exec_stats&#40; Transact SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md)), 고유 하 게 컴파일된 저장된 프로시저에 대 한 통계가 수집 됩니다. 인스턴스에 대해 통계 컬렉션을 해제하는 경우 개별적으로 고유하게 컴파일된 저장 프로시저에 대한 통계 컬렉션은 해제되지 않습니다.  
  
 사용 하 여 [sys.databases&#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md), [sys.procedures &#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md), [DB_ID &#40; Transact SQL &#41; ](../../t-sql/functions/db-id-transact-sql.md), 또는 [OBJECT_ID &#40; Transact SQL &#41; ](../../t-sql/functions/object-id-transact-sql.md) 데이터베이스와 저장된 프로시저에 대 한 Id를 가져오려는 합니다.  
  
 @old_collection_value= *값*  
 현재 상태를 반환합니다.  
  
## <a name="return-code"></a>반환 코드  
 성공의 경우 0이고, 실패의 경우 0이 아닙니다.  
  
## <a name="permissions"></a>Permissions  
 고정 sysadmin 역할의 멤버 자격이 필요합니다.  
  
## <a name="code-sample"></a>코드 예제  
 다음 코드 예제에서는 인스턴스에 대해 고유하게 컴파일된 모든 저장 프로시저에 대해 통계 컬렉션을 설정한 다음 고유하게 컴파일된 특정 저장 프로시저에 대해 통계 컬렉션을 설정하는 방법을 보여 줍니다.  
  
```tsql   
DECLARE @c bit  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1;  
  
EXEC sp_xtp_control_query_exec_stats @old_collection_value=@c output;  
SELECT @c AS 'collection status';  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1,   
@database_id = 5, @xtp_object_id = 341576255;  
  
EXEC sp_xtp_control_query_exec_stats @database_id = 5,   
@xtp_object_id = 341576255, @old_collection_value=@c output;  
  
SELECT @c AS 'collection status';  
```  
  
## <a name="see-also"></a>관련 항목:  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  