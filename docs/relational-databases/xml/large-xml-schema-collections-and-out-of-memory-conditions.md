---
title: "대형 XML 스키마 컬렉션 및 메모리 부족 상태 | Microsoft Docs"
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
  - "메모리 부족 상태"
  - "XML 스키마 컬렉션 [SQL Server], 대형"
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# 대형 XML 스키마 컬렉션 및 메모리 부족 상태
  대형 XML 스키마 컬렉션에서 기본 제공 XML_SCHEMA_NAMESPACE() 함수를 호출하거나 대형 XML 스키마 컬렉션을 삭제하려고 하면 메모리가 부족해질 수 있습니다. 이러한 문제를 처리할 수 있는 해결책은 다음과 같습니다.  
  
-   시스템 로드가 많지 않은 경우 DROP_XML_SCHEMA_COLLECTION 명령을 사용합니다. 이 명령이 실패하면 ALTER DATABASE 문을 사용하고 DROP XML SCHEMA COLLECTION을 다시 시도하여 데이터베이스를 단일 사용자 모드로 설정합니다. 해당 XML 스키마 컬렉션이 **master**, **model** 또는 **tempdb**에 있을 경우 단일 사용자 모드로 설정하려면 서버를 다시 시작해야 합니다.  
  
-   XML_SCHEMA_NAMESPACE를 호출할 경우 하나의 XML 스키마 네임스페이스만 검색하거나 시스템 로드가 더 적을 때 호출을 시도하거나 단일 사용자 모드로 호출을 시도할 수 있습니다.  
  
## 참고 항목  
 [서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  