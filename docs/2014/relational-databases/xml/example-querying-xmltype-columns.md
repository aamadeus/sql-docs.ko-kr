---
title: '예: XMLType 열 쿼리 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, querying XML example
ms.assetid: d9f3710d-7a2e-4abe-9c02-3e3c0df4d620
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3ae1077d933d9872e3b5691e6233af4b82d61d58
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218163"
---
# <a name="example-querying-xmltype-columns"></a>예: XMLType 열 쿼리
  다음 쿼리는 열이 포함 되어 `xml` 형식입니다. 이 쿼리는 `xml` 유형의 `Instructions` 열로부터 첫 번째 위치에서 제품 모델 ID, 이름 및 제조 단계를 검색합니다.  
  
## <a name="example"></a>예제  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
')   
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
GO  
```  
  
 다음은 결과입니다. 테이블에는 일부 제품 모델에 대해서만 제조 지침이 저장되어 있습니다. 제조 단계는 <`ProductModelData`> 요소의 하위 요소로 결과에 반환됩니다.  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
    <MI:step> ... </MI:step>  
    <MI:step> ... </MI:step>  
 </ProductModelData>  
```  
  
 다음 `SELECT` 문에 지정된 것과 같이 쿼리가 XQuery에 의해 반환된 XML에 대한 열 이름을 지정하는 경우 제조 단계는 지정된 이름이 포함된 요소에 래핑됩니다.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
go  
```  
  
 다음은 결과입니다.  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
  <ManuSteps>  
    <MI:step ... </MI:step>  
    <MI:step ... </MI:step>  
  </ManuSteps>  
</ProductModelData>  
```  
  
 다음 쿼리는 `ELEMENTS` 지시어를 지정합니다. 따라서 반환된 결과는 요소 중심입니다. `XSINIL` 지시어와 함께 지정된 `ELEMENTS` 옵션은 행 집합의 해당 열이 NULL인 경우에도 <`ManuSteps`> 요소를 반환합니다.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData'), root('MyRoot'), ELEMENTS XSINIL  
go  
```  
  
 다음은 결과입니다.  
  
```  
<MyRoot xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   ...  
  <ProductModelData>  
    <ProductModelID>6</ProductModelID>  
    <Name>HL Road Frame</Name>  
    <ManuSteps xsi:nil="true" />  
  </ProductModelData>  
  <ProductModelData>  
    <ProductModelID>7</ProductModelID>  
    <Name>HL Touring Frame</Name>  
    <ManuSteps>  
      <MI:step ... </MI:step>  
      <MI:step ...</MI:step>  
       ...  
    </ManuSteps>  
  </ProductModelData>  
</MyRoot>  
```  
  
## <a name="see-also"></a>관련 항목  
 [FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md)  
  
  
