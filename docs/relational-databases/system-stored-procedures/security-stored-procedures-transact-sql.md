---
title: 보안 저장 프로시저 (거래 SQL) | Microsoft 문서
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system stored procedures [SQL Server], security
- stored procedures [SQL Server], security
- security [SQL Server], stored procedures
ms.assetid: 62b72907-7e95-4c97-9891-0c45d5b678ce
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1ae83ce706d58e627f52fb06120d297c3ae26a82
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624121"
---
# <a name="security-stored-procedures-transact-sql"></a>보안 저장 프로시저(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 다음과 같은 시스템 저장 프로시저 보안을 관리 하는 데 사용 되는. 이러한 저장된 프로시저 중 일부는 사용 되지 않지만 이전 버전과 호환성을 지원 하기 위해 사용할 수 있습니다. 사용되지 않는 프로시저에 대한 항목에는 대신 사용 가능한 프로시저가 나와 있습니다.  

|||  
|-|-|  
[sys.sp_add_trusted_assembly]( sys-sp-add-trusted-assembly-transact-sql.md) |[sp_addapprole](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md) (사용 되지 않음)|
|[sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)|[sp_addlinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)
|[sp_addlogin](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md) (사용 되지 않음) |[sp_addremotelogin](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md) (사용 되지 않음)
|[sp_addrole](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md) (사용 되지 않음) |[sp_addrolemember](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) (사용 되지 않음)
|[sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md) (사용 되지 않음) |[sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md) (사용 되지 않음)
|[sp_adduser](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md) (사용 되지 않음) |[sp_approlepassword](../../relational-databases/system-stored-procedures/sp-approlepassword-transact-sql.md) (사용 되지 않음)
|[sp_audit_write](../../relational-databases/system-stored-procedures/sp-audit-write-transact-sql.md) |[sp_change_users_login](../../relational-databases/system-stored-procedures/sp-change-users-login-transact-sql.md)
|[sp_changedbowner](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md) |[sp_changeobjectowner](../../relational-databases/system-stored-procedures/sp-changeobjectowner-transact-sql.md) (사용 되지 않음)
|[sp_control_dbmasterkey_password](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md) |[sp_dbfixedrolepermission](../../relational-databases/system-stored-procedures/sp-dbfixedrolepermission-transact-sql.md) (사용 되지 않음)
|[sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md) (사용 되지 않음) |[sp_defaultlanguage](../../relational-databases/system-stored-procedures/sp-defaultlanguage-transact-sql.md) (사용 되지 않음)
|[sp_denylogin](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md) (사용 되지 않음) |[sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)
|[sp_dropalias](../../relational-databases/system-stored-procedures/sp-dropalias-transact-sql.md) (사용 되지 않음) |[sys.sp_drop_trusted_assembly]( sys-sp-drop-trusted-assembly-transact-sql.md) |
|[sp_dropapprole](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md) (사용 되지 않음) |[sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) |
|[sp_droplogin](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md) (사용 되지 않음) |[sp_dropremotelogin](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md) (사용 되지 않음) |
|[sp_droprole](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md) (사용 되지 않음) |[sp_droprolemember](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md) (사용 되지 않음) |
|[sp_dropserver](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md) |[sp_dropsrvrolemember](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md) (사용 되지 않음) |
|[sp_dropuser](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md) (사용 되지 않음) |[sp_grantdbaccess](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md) (사용 되지 않음) |
|[sp_grantlogin](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md) (사용 되지 않음) |[sp_helpdbfixedrole](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md) |
|[sp_helplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-helplinkedsrvlogin-transact-sql.md) |[sp_helplogins](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md) |
|[sp_helpntgroup](../../relational-databases/system-stored-procedures/sp-helpntgroup-transact-sql.md) |[sp_helpremotelogin](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md) (사용 되지 않음) |
|[sp_helprole](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md) |[sp_helprolemember](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md) |
|[sp_helprotect](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md) (사용 되지 않음) |[sp_helpsrvrole](../../relational-databases/system-stored-procedures/sp-helpsrvrole-transact-sql.md) |
|[sp_helpsrvrolemember](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md) |[sp_helpuser](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md) (사용 되지 않음) |
|[sp_migrate_user_to_contained](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md)|[sp_MShasdbaccess](../../relational-databases/system-stored-procedures/sp-mshasdbaccess-transact-sql.md) |
|[sp_password](../../relational-databases/system-stored-procedures/sp-password-transact-sql.md) (사용 되지 않음)|[sp_refresh_parameter_encryption](../../relational-databases/system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md) |
|[sp_remoteoption](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md) (사용 되지 않음)|[sp_revokedbaccess](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md) (사용 되지 않음) |
|[sp_revokelogin](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md) (사용 되지 않음)|[sp_setapprole](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md) |
|[sp_srvrolepermission](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md) (사용 되지 않음)|[sp_testlinkedserver](../../relational-databases/system-stored-procedures/sp-testlinkedserver-transact-sql.md) |
|[sp_unsetapprole](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md) |[sp_validatelogins](../../relational-databases/system-stored-procedures/sp-validatelogins-transact-sql.md) |
|[sp_xp_cmdshell_proxy_account](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md) | |

 
  
## <a name="see-also"></a>관련 항목  
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [보안 함수&#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
