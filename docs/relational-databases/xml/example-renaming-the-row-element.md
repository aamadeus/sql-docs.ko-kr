---
title: "예제: &lt;행&gt; 요소 이름 바꾸기 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RAW 모드, <행> 예제 이름 바꾸기"
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# 예제: &lt;행&gt; 요소 이름 바꾸기
  결과 집합의 각 행에 대해 RAW 모드는 `<row>`요소를 생성합니다. 이 쿼리에 표시된 것과 같이 RAW 모드에 선택적 인수를 지정하여 선택적으로 이 요소에 다른 이름을 지정할 수 있습니다. 이 쿼리는 행 집합의 각 행에 대해 <`ProductModel`> 요소를 반환합니다.  
  
## 예제  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 다음은 결과입니다. 쿼리에 `ELEMENTS` 지시어가 추가되었기 때문에 결과는 요소 중심입니다.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## 참고 항목  
 [FOR XML에서 RAW 모드 사용](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  