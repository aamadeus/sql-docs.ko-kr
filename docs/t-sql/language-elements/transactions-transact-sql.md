---
title: "트랜잭션 (Transact SQL) | Microsoft Docs"
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
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8660d0ac8d6205a94fdab24f41e41bac40a8671e
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="transactions-transact-sql"></a>트랜잭션(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  트랜잭션은 작업의 한 단위입니다. 트랜잭션이 성공하면 트랜잭션 동안 이루어진 모든 데이터 수정은 커밋되고 데이터베이스의 영구적인 부분이 됩니다. 트랜잭션에 오류가 발생하여 취소되거나 롤백되면 모든 데이터 수정은 지워집니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 다음 트랜잭션 모드에서 작동합니다.  
  
 자동 커밋 트랜잭션  
 개별 문이 바로 트랜잭션에 해당합니다.  
  
 명시적 트랜잭션  
 각 트랜잭션이 BEGIN TRANSACTION 문으로 명시적으로 시작하여 COMMIT 또는 ROLLBACK 문으로 명시적으로 끝납니다.  
  
 암시적 트랜잭션  
 새 트랜잭션은 이전 트랜잭션이 완료되면 암시적으로 시작되지만 각 트랜잭션은 COMMIT 또는 ROLLBACK 문으로 명시적으로 완료됩니다.  
  
 일괄 처리 범위의 트랜잭션  
 MARS(Multiple Active Result Sets)에만 해당되며, MARS 세션에서 시작되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명시적 또는 암시적 트랜잭션이 일괄 처리 범위 트랜잭션이 됩니다. 일괄 처리가 완료될 때 커밋되거나 롤백되지 않은 일괄 처리 범위의 트랜잭션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 자동으로 롤백합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 다음과 같은 트랜잭션 문을 제공합니다.  
  
|||  
|-|-|  
|[BEGIN DISTRIBUTED TRANSACTION](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[트랜잭션 시작](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[트랜잭션 커밋](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[SAVE TRANSACTION](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[COMMIT WORK](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>관련 항목:  
 [SET implicit_transactions 옵션 &#40; Transact SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT&#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  