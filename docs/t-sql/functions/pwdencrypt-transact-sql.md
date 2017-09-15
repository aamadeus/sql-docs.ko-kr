---
title: PWDENCRYPT (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dcae01f4b56e022f3b5966acd33877c851d9ae05
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  암호 해시 알고리즘의 현재 버전을 사용하는 입력 값의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 암호 해시를 반환합니다.  
  
 PWDENCRYPT는 오래된 함수로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이후 릴리스에서는 지원되지 않을 수 있습니다. 사용 하 여 [HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md) 대신 합니다. HASHBYTES는 더 많은 해시 알고리즘을 제공합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>인수  
 *암호*  
 암호화할 암호입니다. *암호* 은 **sysname**합니다.  
  
## <a name="return-types"></a>반환 형식  
 **varbinary(128)**  
  
## <a name="permissions"></a>Permissions  
 PWDENCRYPT는 누구나 사용할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [보안 함수&#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40; Transact SQL &#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  