---
title: "관계형 데이터를 처리 하는 XQueries | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7765f20211ebd1278136f198b6957d674c52871c
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="xqueries-handling-relational-data"></a>관계형 데이터에 대한 XQuery 처리
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  에 대해 XQuery를 지정 하는 **xml** 유형 열 또는 변수 중 하나를 사용 하 여는 [XML 데이터 형식 메서드](../t-sql/xml/xml-data-type-methods.md)합니다. 여기에 **query ()**, **value ()**, **exist ()**, 또는 **modify ()**합니다. XQuery는 XML을 생성하는 쿼리에서 식별된 XML 인스턴스에 대해 실행됩니다.  
  
 XQuery 실행으로 생성된 XML에는 다른 Transact-SQL 변수 또는 행 집합 열로부터 검색된 값이 포함될 수 있습니다. 비-XML 관계형 데이터를 결과 XML에 바인딩하기 위해 SQL Server는 XQuery 확장으로 다음과 같은 의사 함수를 제공합니다.  
  
-   **sql: column** 함수  
  
-   **variable ()** 함수  
  
 XQuery를 지정할 때 이러한 XQuery 확장을 사용할 수 있습니다는 **query ()** 의 메서드는 **xml** 데이터 형식입니다. 결과적으로 **query ()** 메서드는 XML 및 비 데이터를 결합 하는 XML을 만들 수 있습니다-**xml** 데이터 형식입니다.  
  
 사용 하는 경우 이러한 함수를 사용할 수도 있습니다는 **xml** 데이터 형식 메서드 **modify ()**, **value ()**, **query ()**, 및  **exist ()**XML 내 관계형 값을 제공할 합니다.  
  
 자세한 내용은 참조 [: column () 함수 (XQuery)](../xquery/xquery-extension-functions-sql-column.md) 및 [variable () 함수 (XQuery)](../xquery/xquery-extension-functions-sql-variable.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [XML 데이터&#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery 언어 참조&#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XML 생성 &#40; XQuery &#41;](../xquery/xml-construction-xquery.md)  
  
  