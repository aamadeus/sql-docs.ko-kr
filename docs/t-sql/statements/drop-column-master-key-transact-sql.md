---
title: DROP COLUMN MASTER KEY(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP COLUMN MASTER KEY
- DROP_COLUMN_MASTER_KEY_TSQL
- DROP COLUMN MASTER
- DROP_COLUMN_MASTER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_keys catalog view
ms.assetid: fd5e77c8-a3ae-4795-bb46-b322c0500041
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d6272567d4aab9a078fe35b1bcc07e9617c2ed36
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608647"
---
# <a name="drop-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  데이터베이스에서 열 마스터 키를 삭제합니다. 메타데이터 작업입니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
DROP COLUMN MASTER KEY key_name;  
```  
  
## <a name="arguments"></a>인수  
 *key_name*  
 열 마스터 키의 이름입니다.  
  
## <a name="remarks"></a>Remarks  
 열 암호화 키를 사용해 암호화된 열 암호화 키 값이 없는 경우 열 마스터 키를 삭제할 수 있습니다. 열 암호화 키 값을 삭제하려면 [DROP COLUMN ENCRYPTION KEY](../../t-sql/statements/drop-column-encryption-key-transact-sql.md) 문을 사용하세요.  
  
## <a name="permissions"></a>Permissions  
 데이터베이스에 대한 **ALTER ANY COLUMN MASTER KEY** 권한이 필요합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-dropping-a-column-master-key"></a>1. 열 마스터 키 삭제  
 다음 예에서는 `MyCMK`이라고 하는 열 마스터 키를 삭제합니다.  
  
```  
DROP COLUMN MASTER KEY MyCMK;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [CREATE COLUMN MASTER KEY&#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [CREATE COLUMN ENCRYPTION KEY&#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY&#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [상시 암호화&#40;데이터베이스 엔진&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)  
  
  
