---
title: OPENROWSET (DMX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENROWSET
dev_langs:
- DMX
helpviewer_keywords:
- OPENROWSET statement
ms.assetid: 8c8b61b4-2bf6-46c7-8976-51484004dc22
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 914e1be70255414373fd758301ef0682f3aba6e7
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt---openrowset"></a>&lt;원본 데이터 쿼리와&gt; -OPENROWSET
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  원본 데이터 쿼리를 외부 공급자에 대한 쿼리로 바꿉니다. INSERT, 선택 FROM PREDICTION JOIN 및 선택 FROM NATURAL PREDICTION JOIN 문을 지원 **OPENROWSET**합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
OPENROWSET(provider_name,provider_string,query_syntax)  
```  
  
## <a name="arguments"></a>인수  
 *provider_name*  
 OLE DB 공급자 이름입니다.  
  
 *provider_string*  
 지정한 공급자에 대한 OLE DB 연결 문자열입니다.  
  
 *query_syntax*  
 행 집합을 반환하는 쿼리 구문입니다.  
  
## <a name="remarks"></a>주의  
 데이터 마이닝 공급자를 사용 하 여 데이터 원본 개체에 연결을 설정할 *provider_name* 및 *provider_string* 에 지정 된 쿼리를 실행 하 고 *query_syntax* 를 원본 데이터에서 행 집합을 검색 합니다.  
  
## <a name="examples"></a>예  
 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] SELECT 문을 사용하여 [!INCLUDE[tsql](../includes/tsql-md.md)] 데이터베이스에서 데이터를 검색할 때 PREDICTION JOIN 문 내에서 다음 예를 사용할 수 있습니다.  
  
```  
OPENROWSET  
(  
'SQLOLEDB.1',  
'Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security     Info=False;Initial Catalog=AdventureWorksDW2012;Data Source=localhost',  
'SELECT TOP 1000 * FROM vTargetMail'  
)  
```  
  
## <a name="see-also"></a>관련 항목:  
 [&#60; 원본 데이터 쿼리와 &#62;](../dmx/source-data-query.md)   
 [Data Mining Extensions &#40; DMX &#41; 데이터 조작 문](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40; DMX &#41; 문 참조](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
