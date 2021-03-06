---
title: 문자열 데이터 형식에 대한 FOR XML 지원 | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- strings [SQL Server], XML
ms.assetid: bf069da8-de1e-44d2-a1fb-ade383076ac1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ac660e14fa26c9254072bd2a027d2f8055f671f6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838631"
---
# <a name="for-xml-support-for-string-data-types"></a>문자열 데이터 형식에 대한 FOR XML 지원
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  데이터의 FOR XML 공백 문자로 생성된 XML이 올바르게 수정됩니다.  
  
 다음 예에서는 예제 테이블 **T** 를 만들고 줄 바꿈, 캐리지 리턴 및 탭 문자가 있는 예제 데이터를 삽입합니다. SELECT 문은 테이블에서 데이터를 검색합니다.  
  
```  
CREATE TABLE T  
(  
  c1 int identity primary key,  
  c2 varchar(100)  
);  
go  
  
INSERT T (c2) VALUES ('Special character 0xD for carriage return ' + convert(varchar(10), 0xD) + ' after carriage return');  
INSERT T (c2) VALUES ('Special character 0x9 for tab ' + convert(varchar(10), 0x9) + ' after tab' );  
INSERT T (c2) VALUES ('Special character 0xA for line feed ' + convert(varchar(10), 0xA) + ' after line feed');  
go  
SELECT *   
FROM T  
FOR XML AUTO;  
go  
```  
  
 다음은 결과입니다.  
  
```  
 <T c1="1" c2="Special character 0xD for carriage return   
 after carriage return" />  
 <T c1="2" c2="Special character 0x9 for tab     after tab" />  
 <T c1="3" c2="Special character 0xA for line feed   
after line feed" />  
```  
  
 이전 쿼리에서 다음을 유의하세요.  
  
-   첫 행의 캐리지 리턴은 &#xD로 수정됩니다.  
  
-   두 번째 행의 탭 문자는 &#x09로 수정됩니다.  
  
-   세 번째 행의 줄 바꿈 문자는 &#xA로 수정됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [다양한 SQL Server 데이터 형식에 대한 FOR XML 지원](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
