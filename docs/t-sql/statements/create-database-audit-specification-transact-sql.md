---
title: "데이터베이스 감사 사양 (Transact SQL) 만들기 | Microsoft Docs"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE DATABASE AUDIT
- DATABASE_AUDIT_SPECIFICATION_TSQL
- DATABASE AUDIT SPECIFICATION
- CREATE_DATABASE_AUDIT_SPECIFICATION_TSQL
- CREATE_DATABASE_AUDIT_TSQL
- CREATE DATABASE AUDIT SPECIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- database audit specification
- CREATE DATABASE AUDIT SPECIFICATION statement
ms.assetid: 0544da48-0ca3-4a01-ba4c-940e23dc315b
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a0148505f91cdf572205f34b3854a3c093f5352d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-audit-specification-transact-sql"></a>CREATE DATABASE AUDIT SPECIFICATION(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 감사 기능을 사용하여 데이터베이스 감사 사양 개체를 만듭니다. 자세한 내용은 [SQL Server Audit&#40;데이터베이스 엔진&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)을 참조하세요.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
CREATE DATABASE AUDIT SPECIFICATION audit_specification_name  
{  
    FOR SERVER AUDIT audit_name   
        [ { ADD ( { <audit_action_specification> | audit_action_group_name } )   
      } [, ...n] ]  
    [ WITH ( STATE = { ON | OFF } ) ]  
}  
[ ; ]  
<audit_action_specification>::=  
{  
      action [ ,...n ]ON [ class :: ] securable BY principal [ ,...n ]  
}  
```  
  
## <a name="arguments"></a>인수  
 *audit_specification_name*  
 감사 사양의 이름입니다.  
  
 *audit_name*  
 이 사양이 적용되는 감사의 이름입니다.  
  
 *audit_action_specification*  
 감사에 기록되어야 하는 보안 개체에 대한 보안 주체의 동작 사양입니다.  
  
 *작업*  
 하나 이상의 데이터베이스 수준 감사 가능 동작의 이름입니다. 감사 동작의 목록을 보려면 참조 [SQL Server Audit 동작 그룹 및 동작](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md)합니다.  
  
 *audit_action_group_name*  
 하나 이상의 데이터베이스 수준 감사 가능 동작 그룹의 이름입니다. 감사 동작 그룹의 목록에 대 한 참조 [SQL Server Audit 동작 그룹 및 동작](../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md)합니다.  
  
 *클래스*  
 보안 개체의 클래스 이름(해당되는 경우)입니다.  
  
 *보안 개체*  
 감사 동작 또는 감사 동작 그룹을 적용할 데이터베이스의 테이블, 뷰 또는 기타 보안 개체입니다. 자세한 내용은 [Securables](../../relational-databases/security/securables.md)을 참조하세요.  
  
 *보안 주체*  
 데이터베이스의 이름 적용 감사 동작 또는 감사 동작 그룹을 보안 주체입니다. 자세한 내용은 참조 [보안 주체 &#40; 데이터베이스 엔진 &#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)합니다.  
  
 WITH ( STATE = { ON | OFF } )  
 감사에서 이 감사 사양에 대한 레코드를 수집하거나 수집하지 못하도록 설정합니다.  
  
## <a name="remarks"></a>주의  
 데이터베이스 감사 사양은 지정된 데이터베이스에 있는 비보안 개체입니다. 데이터베이스 감사 사양을 처음 만들 때는 사용할 수 없는 상태입니다.  
  
## <a name="permissions"></a>Permissions  
 사용자에 게는 `ALTER ANY DATABASE AUDIT` 권한이 있고 데이터베이스 감사 사양을 만들어 모든 감사에 바인딩할 합니다.  
  
 데이터베이스 감사 사양을 만든 후 있는 보안 주체가 볼 수 있습니다는 `CONTROL SERVER`, `ALTER ANY DATABASE AUDIT` 사용 권한 또는 `sysadmin` 계정.  
  
## <a name="examples"></a>예  
 다음 예에서는 `Payrole_Security_Audit`라는 서버 감사를 만들고 `Payrole_Security_Audit` 데이터베이스의 `SELECT` 테이블에 대해 `INSERT` 사용자의 `dbo` 및 `HumanResources.EmployeePayHistory` 문을 감사하는 `AdventureWorks2012`라는 데이터베이스 감사 사양을 만듭니다.  
  
```  
USE master ;  
GO  
-- Create the server audit.  
CREATE SERVER AUDIT Payrole_Security_Audit  
    TO FILE ( FILEPATH =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA' ) ;  
GO  
-- Enable the server audit.  
ALTER SERVER AUDIT Payrole_Security_Audit   
WITH (STATE = ON) ;  
GO  
-- Move to the target database.  
USE AdventureWorks2012 ;  
GO  
-- Create the database audit specification.  
CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
FOR SERVER AUDIT Payrole_Security_Audit  
ADD (SELECT , INSERT  
     ON HumanResources.EmployeePayHistory BY dbo )  
WITH (STATE = ON) ;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [서버 감사 &#40; 만들기 Transact SQL &#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER audit&#40; Transact SQL &#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER audit&#40; Transact SQL &#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [SERVER AUDIT specification&#40; 만들기 Transact SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT specification&#40; Transact SQL &#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT specification&#40; Transact SQL &#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [데이터베이스 감사 사양 (Transact SQL) 만들기](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT specification&#40; Transact SQL &#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT specification&#40; Transact SQL &#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER authorization&#40; Transact SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file&#40; Transact SQL &#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status&#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions&#40; Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [서버 감사 및 서버 감사 사양 만들기](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
