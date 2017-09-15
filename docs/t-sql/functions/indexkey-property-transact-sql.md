---
title: INDEXKEY_PROPERTY (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- INDEXKEY_PROPERTY_TSQL
- INDEXKEY_PROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- index keys [SQL Server]
- INDEXKEY_PROPERTY function
- viewing index keys
- displaying index keys
- keys [SQL Server], index
ms.assetid: 87c0c385-6b2d-4716-ac8c-a3ce6e8d89e9
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4d15a653fbc4954a37e5124a7a24436738ef5c1
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="indexkeyproperty-transact-sql"></a>INDEXKEY_PROPERTY(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  인덱스 키에 대한 정보를 반환합니다. XML 인덱스에 대해서는 NULL을 반환합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]대신를 사용 하 여 [sys.index_columns&#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md).  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
INDEXKEY_PROPERTY ( object_ID ,index_ID ,key_ID ,property )  
```  
  
## <a name="arguments"></a>인수  
 *object_ID*  
 테이블 또는 인덱싱된 뷰의 개체 ID입니다. *object_ID* 은 **int**합니다.  
  
 *index_ID*  
 인덱스 ID입니다. *index_ID* 은 **int**합니다.  
  
 *key_ID*  
 인덱스 키 열 위치입니다. *key_ID* 은 **int**합니다.  
  
 *속성*  
 정보를 반환할 속성의 이름입니다. *속성* 문자 문자열이 며 다음 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**ColumnId**|에 있는 열 ID는 *key_ID* 인덱스 위치입니다.|  
|**IsDescending**|인덱스 열이 저장되는 순서<br /><br /> 1 = 내림차순 0 = 오름차순|  
  
## <a name="return-types"></a>반환 형식  
 **int**  
  
## <a name="exceptions"></a>예외  
 오류가 발생하거나 호출자가 개체를 볼 수 있는 권한을 갖고 있지 않으면 NULL을 반환합니다.  
  
 사용자는 소유하고 있거나 사용 권한을 부여 받은 보안 개체의 메타데이터만 볼 수 있습니다. 즉, 사용자가 개체에 대한 사용 권한이 없으면 INDEXKEY_PROPERTY와 같은 메타데이터 내보내기 기본 제공 함수가 NULL을 반환합니다. 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="examples"></a>예  
 다음 예에서는 `1` 테이블의 인덱스 ID `1`과 키 열 `Production.Location`에 대해 두 속성이 반환됩니다.  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT   
    INDEXKEY_PROPERTY(OBJECT_ID('Production.Location', 'U'),  
        1,1,'ColumnId') AS [Column ID],  
    INDEXKEY_PROPERTY(OBJECT_ID('Production.Location', 'U'),  
        1,1,'IsDescending') AS [Asc or Desc order];  
```  
  
 결과 집합은 다음과 같습니다.  
  
```  
Column ID   Asc or Desc order   
----------- -----------------   
1           0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>관련 항목:  
 [INDEX_COL &#40; Transact SQL &#41;](../../t-sql/functions/index-col-transact-sql.md)   
 [INDEXPROPERTY&#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [sys.objects &#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.indexes&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  