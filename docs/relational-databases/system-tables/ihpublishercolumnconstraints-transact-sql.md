---
title: IHpublishercolumnconstraints (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnconstraints
- IHpublishercolumnconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnconstraints system table
ms.assetid: d7a41da6-e067-430a-8da2-3f6745b8a4f3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00b937c949019bf1952977685cf063bf05c23e73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724861"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **IHpublishercolumnconstraints** 시스템 테이블에 있는 SQL Server 이외 게시 열을 매핑하는 [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) 시스템 테이블의 제약 조건에는 [IHpublisherconstraints ](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) 시스템 테이블입니다. 이 테이블은 배포 데이터베이스에 저장됩니다.  
  
## <a name="definition"></a>정의  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|열을 식별 [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) 연결 제약 조건입니다.|  
|**publisherconstraint_id**|**int**|제약 조건을 식별 [IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) 열과 연결 합니다.|  
|**indid**|**int**|게시된 테이블에서 열의 위치를 나타냅니다.|  
  
## <a name="see-also"></a>관련 항목  
 [다른 유형의 데이터베이스 복제](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [복제 테이블 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
