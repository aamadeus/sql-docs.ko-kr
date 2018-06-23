---
title: 스키마 캐싱 (SQLXML 4.0) | Microsoft Docs
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
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ddf2b95f9b72a0def960f6159cd8646a6b4439c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36091029"
---
# <a name="schema-caching-sqlxml-40"></a>스키마 캐싱(SQLXML 4.0)
  Microsoft SQL Server 2000 웹 릴리스 1, Microsoft SQLXML 2.0 및 SQLXML 3.0에 대 한 XML의-나란히 설치의 경우 스키마는 다음 레지스트리 키를 사용 하 여 모든 버전에서 캐싱을 명시적으로 제어할 수 있습니다.  
  
 웹 릴리스 1:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 나란히 설치에 대 한 자세한 내용은 참조 [SQLXML 4.0 s p 1의 새로운](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md)합니다.  
  
 스키마 캐싱은 XPath 쿼리의 성능을 크게 개선합니다. 매핑 스키마에 대해 XPath 쿼리를 실행하면 스키마가 메모리에 저장되고 필요한 데이터 구조가 메모리에 구성됩니다. 스키마 캐싱이 설정되면 스키마가 메모리에 유지되므로 후속 XPath 쿼리의 성능이 개선됩니다.  
  
 스키마 캐시 크기를 설정하려면 레지스트리에 위의 키를 추가합니다.  
  
 스키마 크기는 사용 가능한 메모리와 사용 중인 스키마 개수에 따라 설정합니다. 기본 **SchemaCacheSize** 크기는 31입니다. 설정한 경우 **SchemaCacheSize** 이상 버전에서 더 많은 메모리가 사용 됩니다. 따라서 스키마 액세스 속도가 느리면 캐시 크기를 늘리고 메모리가 부족하면 캐시 크기를 줄일 수 있습니다.  
  
 성능상의 이유로, 얻으려면 설정 하는 것이 좋습니다 **SchemaCacheSize** 일반적으로 사용 하는 매핑 스키마의 번호 보다 높은 합니다. 스키마 개수 증가 하는 경우 **SchemaCacheSize** 작으면 있는 스키마 개수 보다 성능이 저하 됩니다.  
  
> [!NOTE]  
>  스키마를 변경하더라도 2분 여 동안은 캐시에 반영되지 않으므로 개발 중에는 스키마를 캐싱하지 않는 것이 좋습니다.  
  
## <a name="see-also"></a>관련 항목  
 [템플릿 캐싱은 &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [XSL 캐싱 &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  