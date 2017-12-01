---
title: sp_dbcmptlevel (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
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
- sp_dbcmptlevel
- sp_dbcmptlevel_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_dbcmptlevel
ms.assetid: 508c686d-2bd4-41ba-8602-48ebca266659
caps.latest.revision: "110"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d605927373e0e92397b4f6074264aa2232df3cae
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2017
---
# <a name="spdbcmptlevel-transact-sql"></a>sp_dbcmptlevel(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  특정 데이터베이스 동작이 지정된 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 호환되도록 설정합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]사용 하 여 [ALTER DATABASE 호환성 수준](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)대신 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_dbcmptlevel [ [ @dbname = ] name ]   
    [ , [ @new_cmptlevel = ] version ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@dbname=** ] *이름*  
 호환성 수준을 변경할 데이터베이스의 이름입니다. 데이터베이스 이름은 식별자에 대한 규칙을 따라야 합니다. *이름* 은 **sysname**, 기본값은 NULL입니다.  
  
 [  **@new_cmptlevel=** ] *버전*  
 데이터베이스가 호환되도록 설정할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 버전입니다. *버전* 은 **tinyint**, 기본값은 NULL입니다. 값은 다음 중 하나여야 합니다.  
  
 **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 **110** = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
 **120** = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 **130** = [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
 지정 된 매개 변수가 없는 경우 또는 경우는 *이름* 매개 변수를 지정 하지 않으면 **sp_dbcmptlevel** 에서 오류를 반환 합니다.  
  
 경우 *이름* 없이 지정 된 *버전*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] 지정된 된 데이터베이스의 현재 호환성 수준을 표시 하는 메시지를 반환 합니다.  
  
## <a name="remarks"></a>주의  
 호환성 수준에 대 한 참조 [ALTER DATABASE 호환성 수준 &#40; Transact SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="permissions"></a>Permissions  
 데이터베이스 소유자의 멤버는 **sysadmin** 고정 서버 역할 및 **db_owner** 고정된 데이터베이스 역할 (현재 데이터베이스를 변경 하려는) 하는 경우이 프로시저를 실행할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [데이터베이스 엔진 저장 프로시저 &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE&#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [예약 키워드&#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  