---
title: sp_audit_write (TRANSACT-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
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
- sp_audit_write
- sp_audit_write_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_audit_write
ms.assetid: 4c523848-1ce6-49ad-92b3-e0e90f24f1c2
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10c74597481f6274485b894c30ac6946bb75fd8a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2017
---
# <a name="spauditwrite-transact-sql"></a>sp_audit_write(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  사용자 정의 감사 이벤트를 추가 **USER_DEFINED_AUDIT_GROUP**합니다. 경우 **USER_DEFINED_AUDIT_GROUP** 활성화 되지 않으면 **sp_audit_write** 는 무시 됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_audit_write [ @user_defined_event_id =  ] user_defined_event_id ,   
        [ @succeeded =  succeeded   
    [ , [ @user_defined_information =  ] 'user_defined_information' ]   
    [ ; ]  
```  
  
## <a name="arguments"></a>인수  
 **@user_defined_event_id**  
 매개 변수는 사용자에 의해 정의 되며에 기록 된 **user_defined_event_id** 감사 로그의 열입니다. *@user_defined_event_id*형식이 **smallint**합니다.  
  
 **@succeeded**  
 이벤트 성공 여부를 표시하기 위해 사용자가 전달하는 매개 변수입니다. 이 매개 변수는 감사 로그의 succeeded 열에 표시됩니다. *@succeeded***비트**합니다.  
  
 **@user_defined_information**  
 사용자가 정의하며 감사 로그의 새 user_defined_event_id 열에 기록되는 텍스트입니다. *@user_defined_information***nvarchar (4000)**합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
 입력 매개 변수가 잘못되었거나 대상 감사 로그에 쓸 수 없는 경우 실패가 반환됩니다.  
  
## <a name="remarks"></a>주의  
 경우는 **USER_DEFINED_AUDIT_GROUP** 서버 감사 사양 또는 데이터베이스 감사 사양에 따라 트리거되는 이벤트에 추가 됩니다 **sp_audit_write** 감사 로그에 포함 됩니다.  
  
## <a name="permissions"></a>Permissions  
 멤버 자격이 필요는 **공용** 데이터베이스 역할입니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-creating-a-user-defined-audit-event-with-informational-text"></a>1. 정보 텍스트를 포함하여 사용자 정의 감사 이벤트 만들기  
 다음 예에서는 ID가 27인 감사 이벤트, succeeded 값 0, 그리고 선택적으로 포함되는 정보 텍스트를 작성합니다.  
  
```  
EXEC sp_audit_write @user_defined_event_id =  27 ,   
              @succeeded =  0   
            , @user_defined_information = N'Access to a monitored object.' ;  
```  
  
### <a name="b--creating-a-user-defined-audit-event-without-informational-text"></a>2.  정보 텍스트 없이 사용자 정의 감사 이벤트 만들기  
 다음 예에서는 ID가 27인 감사 이벤트와 succeeded 값 0을 작성하되 선택적 정보 텍스트 또는 매개 변수 이름은 포함하지 않습니다.  
  
```  
EXEC sp_audit_write 27, 0;  
  
```  
  
## <a name="see-also"></a>관련 항목:  
 [보안 저장 프로시저 &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER&#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  