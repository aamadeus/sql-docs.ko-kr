---
title: 주석 스키마 보안 고려 사항 (SQLXML 4.0) | Microsoft Docs
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
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7a53645c4b6115a7859b6c07a78c300f902e9111
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36090397"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>주석 스키마 보안 고려 사항(SQLXML 4.0)
  다음은 주석 스키마를 사용하기 위한 보안 지침입니다.  
  
-   매핑 스키마에서는 기본 매핑 사용을 사용하지 마십시오. 기본 매핑은 기본적으로 요소 이름을 테이블 이름에 매핑하고 특성 이름을 열 이름에 매핑하므로 결과 XML 문서에서 데이터베이스 정보(테이블 및 열 이름)가 공개됩니다. 따라서 XML 문서를 보는 모든 사용자가 데이터베이스의 테이블 및 열 정보에 액세스할 수 있으므로 보안 문제가 발생할 수 있습니다. 이러한 위험을 방지하려면 스키마에 임의의 요소 및 특성 이름을 지정하고 주석을 사용하여 이를 명시적으로 테이블 및 열에 매핑하십시오. XSD 스키마를 만들 때 기본 매핑을 사용 하 여는 방법에 대 한 자세한 내용은 참조 [XSD의 매핑 기본 요소 및 특성 테이블 및 열 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)합니다.  
  
-   주석을 사용하여 명시적 매핑을 지정하면 테이블 이름 및 열 이름과 같은 데이터베이스 정보가 공개됩니다. 따라서 이러한 스키마가 공개되지 않도록 해야 합니다.  
  
-   재귀(`max-depth` 주석을 더 높은 값으로 설정하여 지정)를 사용하여 매핑 스키마에 대해 지정한 특정 쿼리는 실행하는 데 오랜 시간이 걸릴 수 있습니다. 필요에 따라 명령 제한 시간 속성을 초 단위로 설정 하 여 제한 시간을 지정할 수 있습니다. 예를 들어:  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>관련 항목  
 [SQLXML 4.0의 주석이 추가된 XSD 스키마](../../sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  