---
title: XPath 쿼리 (SQLXML 4.0)를 사용 하는 소개 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 382fd81302cfccb378ef6c1a52cf996857cd2dcb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091935"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a>XPath 쿼리 사용 소개(SQLXML 4.0)
  XPath(XML Path Language) 쿼리는 URL의 일부로 지정하거나 템플릿 내에 지정할 수 있습니다. 매핑 스키마에 따라 이 결과 조각의 구조가 결정되고 값은 데이터베이스에서 검색됩니다. 이 프로세스는 CREATE VIEW 문을 사용하여 뷰를 만들고 이러한 뷰에 대한 SQL 쿼리를 작성하는 것과 개념적으로 유사합니다.  
  
> [!NOTE]  
>  SQLXML 4.0의 XPath 쿼리를 이해하려면 템플릿 및 매핑 스키마와 같은 관련 개념과 XML 뷰에 대해 잘 알고 있어야 합니다. 자세한 내용은 참조 [주석이 추가 된 XSD 스키마 소개 &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md), 및 World Wide Web Consortium (W3C)에서 정의한 XPath 표준을 합니다.  
  
 XML 문서는 요소 노드, 특성 노드, 텍스트 노드 등과 같은 노드로 구성됩니다. 예를 들어 다음 XML 문서를 참조하십시오.  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 이 문서에서는  **\<고객 >** 요소 노드인지를 **cid** 는 특성 노드 및 **"중요"** 는 텍스트 노드입니다.  
  
 XPath는 XML 문서에서 노드 집합을 선택하는 데 사용되는 그래프 탐색 언어입니다. 각 XPath 연산자는 이전 XPath 연산자에서 선택한 노드 집합을 기반으로 노드 집합을 선택합니다. 예를 들어 집합이 제공 된  **\<고객 >** XPath 노드 모두를 선택할 수  **\<순서 >** 노드는 **날짜** 특성 값 **"7/14/1999"** 합니다. 결과 노드 집합에는 주문 날짜가 1999년 7월 14일인 모든 주문이 포함됩니다.  
  
 XPath 언어는 W3C(World Wide Web Consortium)에서 표준 탐색 언어로 정의됩니다. 에 있는 W3C XPath 사양의 하위 집합을 구현 하는 SQLXML 4.0 http://www.w3.org/TR/1999/PR-xpath-19991008.html합니다.  
  
 다음은 W3C XPath 구현과 SQLXML 4.0 구현 간의 주요 차이점입니다.  
  
-   **루트 쿼리**  
  
     SQLXML 4.0은 루트 쿼리(/)를 지원하지 않습니다. 각 XPath 쿼리는 최상위에서 시작 하도록  **\<ElementType >** 스키마에 있습니다.  
  
-   **오류 보고**  
  
     W3C XPath 사양에서는 오류 조건을 정의하지 않습니다. 따라서 노드를 선택하지 못하는 XPath 쿼리는 빈 노드 집합을 반환합니다. SQLXML 4.0에서는 쿼리에서 여러 가지 오류 메시지를 반환할 수 있습니다.  
  
-   **문서 순서**  
  
     SQLXML 4.0에서는 문서 순서가 항상 확실하지는 않습니다. 따라서 `following`과 같이 문서 순서를 사용하는 숫자 조건자와 축은 구현되지 않습니다.  
  
     또한 문서 순서가 없다는 것은 해당 노드가 단일 행의 단일 열에 매핑되는 경우에만 노드의 문자열 값을 평가할 수 있다는 것을 의미하기도 합니다. 자식 요소가 있는 요소, IDREFS 또는 NMTOKENS 노드는 문자열로 변환할 수 없습니다.  
  
    > [!NOTE]  
    >  경우에 따라 `key-fields` 주석이나 `relationship` 주석의 키로 인해 문서 순서가 결정적이 될 수도 있지만 그러나이 자세한 정보에 대 한 이러한 주석의 주된 용도, 참조 [식별 키 열을 사용 하 여 sql:-필드 &#40;SQLXML 4.0&#41; ](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) 및 [지정 관계를 사용 하 여 sql: 관계 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)합니다.  
  
-   **데이터 형식**  
  
     SQLXML 4.0에서는 XPath `string`, `number` 및 `boolean` 데이터 형식의 구현에 제약이 따릅니다. 자세한 내용은 참조 [XPath 데이터 형식에 &#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md)합니다.  
  
-   **교차곱 쿼리**  
  
     SQLXML 4.0에서는 `Customers[Order/@OrderDate=Order/@ShipDate]`와 같은 교차곱 XPath 쿼리를 지원하지 않습니다. 이 쿼리는 Order의 OrderDate가 ShipDate와 동일한 Order가 있는 모든 Customer를 선택합니다.  
  
     그러나 SQLXML 4.0에서는 OrderDate가 ShipDate와 동일한 Order가 있는 Customer를 선택하는 `Customer[Order[@OrderDate=@ShippedDate]]`와 같은 쿼리를 지원하지 않습니다.  
  
-   **오류 처리 및 보안**  
  
     사용되는 스키마 및 XPath 쿼리 식에 따라 특정 조건에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 오류가 사용자에게 표시될 수 있습니다.  
  
 다음 섹션의 표에서는 이러한 영역에서 SQLXML 4.0의 XPath 쿼리 구현이 W3C 사양과 어떻게 다른지 자세히 설명합니다.  
  
## <a name="supported-functionality"></a>지원되는 기능  
 다음 표에서는 SQLXML 4.0에서 구현되는 XPath 언어의 기능을 보여 줍니다.  
  
|기능|항목|샘플 쿼리에 대한 링크|  
|-------------|----------|----------------------------|  
|Axes|`attribute`, `child`, `parent` 및 `self` 축|[XPath 쿼리에 축을 지정 &#40;SQLXML 4.0&#41;](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|연속 및 중첩 조건자를 포함하는 부울 값 조건자||[XPath 쿼리에 산술 연산자 지정 &#40;SQLXML 4.0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|모든 관계 연산자|=, !=, <, \<=, >, >=|[XPath 쿼리에 관계형 연산자 지정 &#40;SQLXML 4.0&#41;](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|산술 연산자|+, -, *, div|[XPath 쿼리에 산술 연산자 지정 &#40;SQLXML 4.0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|명시적 변환 함수|`number()`, `string()`, `Boolean()`|[XPath 쿼리에 명시적 변환 함수 지정 &#40;SQLXML 4.0&#41;](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|부울 연산자|AND, OR|[XPath 쿼리에 부울 연산자 지정 &#40;SQLXML 4.0&#41;](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|부울 함수|`true()`, `false()`, `not()`|[XPath 쿼리에 부울 함수 지정 &#40;SQLXML 4.0&#41;](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|XPath 변수||[XPath 쿼리에 XPath 변수 지정 &#40;SQLXML 4.0&#41;](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a>지원되지 않는 기능  
 다음 표에서는 SQLXML 4.0에서 구현되지 않는 XPath 언어의 기능을 보여 줍니다.  
  
|기능|항목|  
|-------------|----------|  
|Axes|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|숫자 값 조건자||  
|산술 연산자|mod|  
|노드 함수|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|문자열 함수|`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`|  
|부울 함수|`lang()`|  
|숫자 함수|`sum()`, `floor()`, `ceiling()`, `round()`|  
|Union 연산자|&#124;|  
  
 템플릿에 XPath 쿼리를 지정할 때는 다음 동작에 유의하십시오.  
  
-   XPath에는 XML(템플릿은 XML 문서임)에서 특수한 의미를 가지는 < 또는 &와 같은 문자가 포함될 수 있습니다. 이러한 문자를 XML & 인코딩을 사용하여 이스케이프 처리하거나 XPath를 URL에 지정해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQLXML 4.0의 XPath 쿼리 사용](using-xpath-queries-in-sqlxml-4-0.md)  
  
  