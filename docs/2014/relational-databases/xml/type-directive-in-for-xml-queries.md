---
title: FOR XML 쿼리의 TYPE 지시어 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
caps.latest.revision: 40
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3e5a3ffe184513bce9f331f5d905a0587897e64a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36185361"
---
# <a name="type-directive-in-for-xml-queries"></a>FOR XML 쿼리의 TYPE 지시어
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대 한 지원의 [xml &#40;Transact SQL&#41; ](/sql/t-sql/xml/xml-transact-sql) 선택적으로 FOR XML 쿼리의 결과가 반환 되도록 요청에 사용 하면 `xml` TYPE 지시어를 지정 하 여 데이터 형식입니다. 그러면 서버에서 FOR XML 쿼리 결과를 처리할 수 있습니다. 예를 들어, 수 있습니다에 대해 XQuery를 지정 합니다. 결과를 할당 한 `xml` 유형 변수에 또는 쓰기 [중첩 FOR XML 쿼리](use-nested-for-xml-queries.md)합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] TYPE 지시어를 사용 하는 FOR XML 쿼리와 같은 하거나 XML 데이터 형식 인스턴스 데이터를 다른 서버 생성 결과로 클라이언트에 반환 된 `xml` SQL 테이블 열 및 출력의 XML 인스턴스 데이터 값을 반환 데이터 형식이 사용 됩니다 매개 변수입니다. 클라이언트 응용 프로그램 코드에서 ADO.NET 공급자가 이 XML 데이터 형식 정보를 서버에서 이진 인코딩으로 보내도록 요청합니다. 그러나 TYPE 지시어 없이 FOR XML을 사용하면 XML 데이터가 문자열 유형으로 반환됩니다. 클라이언트 공급자는 항상 두 XML 유형 중 하나를 처리할 수 있습니다. TYPE 지시어가 없는 최상위 FOR XML은 커서와 함께 사용할 수 없습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 TYPE 지시어를 FOR XML 쿼리와 함께 사용하는 방법을 보여 줍니다.  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a>FOR XML 쿼리 결과를 xml 유형으로 검색  
 다음 쿼리에서는 `Contacts` 테이블에서 고객 연락처 정보를 검색합니다. `TYPE`에 `FOR XML` 지시어가 지정되어 있으므로 결과는 `xml` 유형으로 반환됩니다.  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 다음은 결과의 일부입니다.  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a>xml 유형 변수에 FOR XML 쿼리 결과 할당  
 다음 예제에서는 FOR XML 결과에 할당 됩니다는 `xml` 유형 변수 `@x`합니다. 와 같은 연락처 정보를 검색 하는 쿼리는 `BusinessEntityID`, `FirstName`, `LastName`, 및 추가 전화 번호와에서 `AdditionalContactInfo` 의 열 `xml``TYPE`합니다. `FOR XML` 절은 `TYPE` 지시어를 지정하므로 XML은 `xml` 유형으로 반환되며 변수에 할당됩니다.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a>FOR XML 쿼리 결과 쿼리  
 FOR XML 쿼리가 XML을 반환하므로 따라서 적용할 수 있습니다 `xml` 유형 메서드를 같은 `query()` 및 `value()`, FOR XML 쿼리에 의해 반환 된 XML 결과에 있습니다.  
  
 다음 쿼리에서 `query()` 의 메서드는 `xml` 데이터 형식은 결과를 하는 데 사용 되는 `FOR XML` 쿼리 합니다. 자세한 내용은 [query&#40;&#41; 메서드&#40;xml 데이터 형식&#41;](/sql/t-sql/xml/query-method-xml-data-type)를 참조하세요.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 내부 `SELECT … FOR XML` 쿼리에서 반환은 `xml` 유형 결과를 외부 `SELECT` 적용 되는 `query()` 메서드를는 `xml` 유형입니다. 지정된 `TYPE` 지시어에 유의하십시오.  
  
 다음은 결과입니다.  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 다음 쿼리에서는 `xml` 데이터 형식의 `value()` 메서드를 사용하여 `SELECT…FOR XML` 쿼리가 반환한 XML 결과에서 값을 검색합니다. 자세한 내용은 [value&#40;&#41; 메서드&#40;xml 데이터 형식&#41;](/sql/t-sql/xml/value-method-xml-data-type)를 참조하세요.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 `value()` 메서드의 XQuery 경로 식이 `BusinessEntityID` 가 `1`인 고객 연락처의 첫 번째 전화 번호를 검색합니다.  
  
> [!NOTE]  
>  TYPE 지시어를 지정 하지 않으면 FOR XML 쿼리 결과 형식으로 반환 `nvarchar(max)`합니다.  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a>INSERT, UPDATE 및 DELETE(Transact-SQL DML)에 FOR XML 쿼리 결과 사용  
 다음 예에서는 DML(데이터 조작 언어) 문에 FOR XML 쿼리를 사용할 수 있는 방법을 보여 줍니다. 예제에서는 `FOR XML` 의 인스턴스를 반환 `xml` 유형입니다. `INSERT` 문은 이 XML을 테이블에 삽입합니다.  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [FOR XML&#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  