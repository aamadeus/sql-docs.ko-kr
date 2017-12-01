---
title: sys.sql_logins (TRANSACT-SQL) | Microsoft Docs
ms.custom: 
ms.date: 01/20/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs: TSQL
helpviewer_keywords: sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 12dcc799255ebc44ed2b8d6401de80a98d83bcbb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="syssqllogins-transact-sql"></a>sys.sql_logins(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인에 대해 행을 반환합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**\<열을 상속 >**|--|상속 **sys.server_principals**합니다.|  
|**is_policy_checked**|**bit**|암호 정책이 확인됩니다.|  
|**is_expiration_checked**|**bit**|암호 만기가 확인됩니다.|  
|**password_hash**|**varbinary(256)**|SQL 로그인 암호의 해시입니다. 부터는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]저장 된 암호 정보가 솔트된 암호의 s h A-512를 사용 하 여 계산 됩니다.|  
  
 이 뷰가 상속 하는 열 목록은 참조 [sys.server_principals&#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="remarks"></a>주의  
 모두 보려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인 및 Windows 인증 로그인 참조 [sys.server_principals&#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 에 포함 된 경우 데이터베이스 사용자를 활성화, 로그인이 없는 연결을 만들 수 있습니다. 해당 계정을 확인 하려면 [sys.database_principals&#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인은 자체 로그인 이름과 sa 로그인을 볼 수 있습니다. 다른 로그인을 보려면 로그인할 때 ALTER ANY LOGIN 또는 사용 권한이 필요합니다.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목:  
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [보안 카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [암호 정책](../../relational-databases/security/password-policy.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  