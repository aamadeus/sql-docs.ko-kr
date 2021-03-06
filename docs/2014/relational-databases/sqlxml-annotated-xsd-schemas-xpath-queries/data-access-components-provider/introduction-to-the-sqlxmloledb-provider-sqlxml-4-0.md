---
title: SQLXMLOLEDB 공급자 (SQLXML 4.0)에 대 한 소개 | Microsoft 문서
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, properties
- adExecuteStream flag
- SQLXMLOLEDB Provider, about SQLXMLOLEDB Provider
ms.assetid: 2e3f3817-4209-4bf4-9f46-248c95bc6f1b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 63badb45984b754e8f586e30f2d659a840db5d43
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134729"
---
# <a name="introduction-to-the-sqlxmloledb-provider-sqlxml-40"></a>SQLXMLOLEDB 공급자 소개(SQLXML 4.0)
  SQLXMLOLEDB 공급자는 ADO(ActiveX Data Objects)를 통해 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 기능을 노출하는 OLE DB Provider입니다. 하지만 이 공급자는 ADO의 "출력 스트림에 쓰기" 모드에서만 명령을 실행할 수 있습니다. SQLXMLOLEDB 공급자는 행 집합 공급자가 아닙니다. 명령을 실행 하면, 지정한 출력 스트림을 사용 하 여 ADO 맵으로 adExecuteStream 플래그를 지정 해야 합니다.  
  
 AdExecuteStream 플래그가 지정 된 명령 실행 하는 구문은 다음과 같습니다.  
  
```  
Dim oTestCommand As New ADODB.Command  
...  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Execute , , adExecuteStream  
...  
```  
  
## <a name="sqlxmloledb-provider-specific-properties"></a>SQLXMLOLEDB 공급자별 속성  
 SQLXMLOLEDB 공급자는 다음과 같은 공급자별 연결 속성을 노출합니다.  
  
|연결<br /><br /> 속성|Default<br /><br /> (있는 경우)|Description|  
|-----------------------------|----------------------------|-----------------|  
|데이터 공급자||SQLXMLOLEDB에서 명령을 실행하는 데 사용하는 OLE DB Provider의 PROGID를 제공합니다. SQLXML 4.0 및 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]부터 이 공급자는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 내에 포함되어 있으므로 이 속성 값은 "SQLNCLI11"으로 제한됩니다. 자세한 내용은 [SQL Server Native Client 프로그래밍](../../native-client/sql-server-native-client-programming.md)을 참조하세요.|  
  
 SQLXMLOLEDB 공급자는 다음과 같은 공급자별 명령 속성을 노출합니다.  
  
|Command<br /><br /> 속성|Default<br /><br /> (있는 경우)|Description|  
|--------------------------|----------------------------|-----------------|  
|기본 경로|""|기본 파일 경로를 지정합니다. 기본 파일 경로는 XSL(XML Stylesheet Language) 또는 매핑 스키마 파일의 위치를 지정하는 데 사용됩니다. 기본 파일 경로 또한 XSL 또는 매핑 매핑 스키마 또는 XSL 속성에 지정 된 스키마 파일의 상대 경로 확인 합니다.<br /><br /> 이 속성을 사용 하는 예제를 보려면 [실행 되는 XPath 쿼리 &#40;SQLXMLOLEDB 공급자&#41;](executing-xpath-queries-sqlxmloledb-provider.md).|  
|ClientSideXML|False|행 집합을 XML로 변환하는 프로세스가 서버 대신 클라이언트에서 수행되도록 하려면 이 속성을 True로 설정합니다. 이 속성은 성능 부하를 중간 계층으로 이동하려는 경우에 유용합니다.<br /><br /> 이 속성을 사용 하는 예제를 보려면 [SQL 쿼리 실행 &#40;SQLXMLOLEDB 공급자&#41; ](executing-sql-queries-sqlxmloledb-provider.md) 또는 [실행 서식 파일에 포함 되어 SQL 쿼리 &#40;SQLXMLOLEDB 공급자&#41; ](executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md).|  
|내용 유형||출력 내용 유형을 반환합니다. READ ONLY 속성입니다.<br /><br /> 이 속성은 내용 유형(예: TEXT/XML, TEXT/HTML, image/jpeg 등)에 대한 정보를 브라우저에 제공합니다. 이 속성의 값이 있는 **콘텐츠 형식** 문서의 본문으로 전송 되는 MIME 형식 (다목적 인터넷 메일 확장)이 포함 된 HTTP 헤더의 일부로 브라우저에 보낸 필드.|  
|매핑 스키마|NULL|클라이언트 응용 프로그램이 매핑 스키마(XDR 또는 XSD)에 대해 XPath 쿼리를 실행하는 경우 이 속성은 매핑 스키마의 이름을 지정하는 데 사용됩니다.<br /><br /> 지정된 경로는 상대 경로(xyz/abc/MySchema.xml) 또는 절대 경로(C:\MyFolder\abc\MySchema.xml)일 수 있습니다.<br /><br /> 상대 경로 지정 하는 경우 기본 경로 속성으로 지정 된 기본 경로 상대 경로 확인 하는 데 사용 됩니다. 자료 Path 속성에 지정 된 경로가 없는 경우 상대 경로 현재 디렉터리에 상대적입니다.<br /><br /> 매핑 스키마 속성에 값을 지정 하는 로컬 디렉터리 경로 또는 URL (http://)을 지정할 수 있습니다. URL을 지정하는 경우 프록시 서버를 통해 HTTP 및 HTTPS 서버에 액세스하도록 WinHTTP를 구성해야 합니다. Proxycfg.exe 유틸리티를 실행하여 이 작업을 수행할 수 있습니다. 자세한 내용은 MSDN 라이브러리의 "WinHTTP 프록시 구성 유틸리티 사용"을 참조하십시오.<br /><br /> 이 속성을 사용 하는 예제를 보려면 [실행 되는 XPath 쿼리 &#40;SQLXMLOLEDB 공급자&#41;](executing-xpath-queries-sqlxmloledb-provider.md).|  
|네임스페이스||이 속성을 사용하면 네임스페이스를 사용하는 XPath 쿼리를 실행할 수 있습니다. 이 속성을 사용 하는 예제를 보려면 [네임 스페이스를 사용 하 여 XPath 쿼리 실행 &#40;SQLXMLOLEDB 공급자&#41;](executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md).|  
|ss Stream Flags||이 속성은 보안 제한의 특정 유형을 지정하는 데 사용됩니다. 예를 들어 파일에 대한 URL 참조나 파일(예: 외부 사이트)에 대한 절대 경로를 허용하지 않을 수 있습니다. 또는 템플릿에서 쿼리를 허용하지 않을 수도 있습니다.<br /><br /> 이 속성에는 다음과 같은 값을 할당할 수 있습니다.<br /><br /> 1 = 2 STREAM_FLAGS_DISALLOW_URL STREAM_FLAGS_DISALLOW_ABSOLUTE_PATH 4 = 8 STREAM_FLAGS_DISALLOW_QUERY = STREAM_FLAGS_ DONTCACHEMAPPINGSCHEMA 16 = STREAM_FLAGS_DONTCACHETEMPLATE 32 = STREAM_FLAGS_DONTCACHEXSL =<br /><br /> 다음 표에서는 이러한 값에 대한 추가 정보를 제공합니다.|  
|xml root||이 속성은 결과 XML의 루트 태그를 정의하는 데 사용됩니다. 예를 들어 데이터베이스에 대해 SQL 쿼리를 실행하고 결과 XML 문서에 단일 루트 요소가 없는 경우 이 속성 값을 사용하여 문서에 단일 루트 요소를 추가합니다.<br /><br /> 이 속성을 사용 하는 예제를 보려면 [SQL 쿼리 실행 &#40;SQLXMLOLEDB 공급자&#41;](executing-sql-queries-sqlxmloledb-provider.md).|  
|xsl||이 속성은 쿼리에서 반환된 XML 문서에 XSL 변환을 적용하려는 경우 XSL 파일 이름을 지정하는 데 사용됩니다.<br /><br /> 지정된 경로는 상대 경로(xyz/abc/MyXSL.xsl) 또는 절대 경로(C:\MyFolder\abc\MyXSL.xsl)일 수 있습니다.<br /><br /> 상대 경로 지정 하는 경우 기본 경로 속성으로 지정 된 기본 경로 상대 경로 확인 하는 데 사용 됩니다. 자료 Path 속성에 지정 된 경로가 없는 경우 상대 경로 현재 디렉터리에 상대적입니다.<br /><br /> 예를 들어가이 속성을 사용 하는 XSL 변환 (SQLXMLOLEDB 공급자) 적용을 참조 하십시오.|  
  
 다음 표에서 ss 스트림 플래그 속성 값에 대 한 설명을 포함합니다.  
  
|속성 값|Description|  
|--------------------|-----------------|  
|STREAM_FLAGS_DISALLOW_URL|매핑 스키마 또는 XSL에 URL을 사용할 수 없습니다.|  
|STREAM_FLAGS_DISALLOW_ABSOLTE_PATH|매핑 스키마 또는 XSL에 대해 지정된 경로는 템플릿 자체의 기본 경로에 상대적이어야 합니다.|  
|STREAM_FLAGS_DISALLOW_QUERY|템플릿에 쿼리를 사용할 수 없습니다.|  
|STREAM_FLAGS_DONTCACHEMAPPINGSCHEMA|매핑 스키마가 캐시되지 않습니다. 이 속성 값은 데이터베이스 스키마가 변경될 수 있는 데이터베이스 개발 단계에서 유용합니다.|  
|STREAM_FLAGS_DONTCACHETEMPLATE|템플릿이 캐시되지 않습니다.|  
|STREAM_FLAGS_DONTCACHEXSL|XSL이 캐시되지 않습니다.|  
  
  
