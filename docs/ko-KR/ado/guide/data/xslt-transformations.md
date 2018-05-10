---
title: XSLT 변환을 | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a86ab0b76dc8bd09cc1c956d743c6e9bb2e330c9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="xslt-transformations"></a>XSLT 변환
XSLT는 다른 형식으로 변환 하는 생성 된 XML에 적용할 수 있습니다. XSLT 템플릿 보다 친숙 한 형식으로 변환할 수 있는 개발에 도움이 ADO의 XML 형식을 이해 합니다.  
  
 예를 들어 알고 레코드 집합의 각 행 z: 행 요소 rs: 데이터 요소 안에 저장 됩니다. 마찬가지로, 레코드 집합의 각 필드는이 요소에 대 한 특성-값 쌍으로 저장 됩니다.  
  
## <a name="remarks"></a>주의  
 다음 XSLT 스크립트는 브라우저에 표시할 HTML 테이블로 변환 하는 이전 섹션에 표시 된 XML에 적용할 수 있습니다.  
  
```  
<?xml version="1.0" encoding="ISO-8859-1"?>  
<html xmlns:xsl="http://www.w3.org/TR/WD-xsl">  
<body STYLE="font-family:Arial, helvetica, sans-serif; font-size:12pt; background-color:white">  
<table border="1" style="table-layout:fixed" width="600">  
  <col width="200"></col>  
  <tr bgcolor="teal">  
    <th><font color="white">CustomerId</font></th>  
    <th><font color="white">CompanyName</font></th>  
    <th><font color="white">ContactName</font></th>  
  </tr>  
<xsl:for-each select="xml/rs:data/z:row">  
  <tr bgcolor="navy">  
    <td><font color="white"><xsl:value-of select="@CustomerID"/></font></td>  
    <td><font color="white"><xsl:value-of select="@CompanyName"/></font></td>  
    <td><font color="white"><xsl:value-of select="@ContactName"/></font></td>   
  </tr>  
</xsl:for-each>  
</table>  
</body>  
</html>  
```  
  
 XSLT 변환 표 제목 함께 레코드 집합의 각 필드를 표시 하는 HTML 표로 ADO 저장 메서드에 의해 생성 된 XML 스트림을 합니다. 테이블 머리글 및 행도 할당 된 다양 한 글꼴 및 색입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [XML 형식으로 레코드 유지](../../../ado/guide/data/persisting-records-in-xml-format.md)