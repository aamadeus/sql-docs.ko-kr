---
title: xs:QName 형식 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0904dc1a1e79c6f3669992bee19b7489bf0bce42
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227083"
---
# <a name="the-xsqname-type"></a>The xs:QName Type
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 XML 스키마 제한 요소를 사용하는 **xs:QName** 에서 파생된 형식을 지원하지 않습니다. 또한 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 멤버 유형이 **QName** 인 공용 구조체 유형을 사용할 수 없습니다.  
  
## <a name="example"></a>예제  
 다음 `CREATE XML SCHEMA COLLECTION` 문은 공용 구조체의 멤버 유형으로 `xs:QName` 유형을 지정하므로 XML 스키마를 로드할 수 없습니다.  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 두 문은 오류를 발생시키며 실패합니다.  
  
## <a name="see-also"></a>관련 항목  
 [서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
