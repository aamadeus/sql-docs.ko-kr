---
title: Session Events Data Columns | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Session Events event category
ms.assetid: 35853451-6768-4a02-8b8f-81a8ae37a333
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 555a9eb950a2dcd70935964a8a6f3237f8abb76d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36093396"
---
# <a name="session-events-data-columns"></a>Session Events 데이터 열
  Session Events 이벤트 범주에는 다음과 같은 이벤트 클래스가 있습니다.  
  
|**이벤트 ID**|**이벤트 이름**|**이벤트 설명**|  
|------------------|--------------------|---------------------------|  
|41|Existing Connection|기존 사용자 연결입니다.|  
|42|Existing Session|기존 세션입니다.|  
|43|Session Initialize|세션을 초기화합니다.|  
  
 다음 표에서는 이 이벤트 클래스에 대한 데이터 열을 나열합니다.  
  
## <a name="existing-connection"></a>Existing Connection  
  
|**열 이름**|**열 ID**|**열 유형**|**열 설명**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|사용 가능한 경우 이벤트가 시작된 시간입니다. 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|StartTime|3|5|사용 가능한 경우 이벤트가 시작된 시간입니다. 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|ConnectionID|25|1|고유 연결 ID입니다.|  
|NTUserName|32|8|Windows 사용자 이름입니다.|  
|NTDomainName|33|8|사용자가 속한 Windows 도메인입니다.|  
|ClientHostName|35|8|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공하면 이 데이터 열이 채워집니다.|  
|ClientProcessID|36|1|클라이언트 응용 프로그램의 프로세스 ID입니다.|  
|ApplicationName|37|8|서버 연결을 만든 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 응용 프로그램에서 전달한 값으로 채워집니다.|  
|SPID|41|1|서버 프로세스 ID로, 사용자 세션을 고유하게 식별합니다. 이 SPI는 XML/A에서 사용하는 세션 GUID와 정확히 일치합니다.|  
|데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면|43|8|이벤트를 생성하는 서버의 이름입니다.|  
  
## <a name="existing-session"></a>Existing Session  
  
|**열 이름**|**열 ID**|**열 유형**|**열 설명**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|사용 가능한 경우 이벤트가 시작된 시간입니다. 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|StartTime|3|5|사용 가능한 경우 이벤트가 시작된 시간입니다. 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|Duration|5|2|이벤트에 의해 사용된 시간(밀리초)입니다.|  
|CPUTime|6|2|이벤트에 의해 사용된 CPU 시간(밀리초)입니다.|  
|ConnectionID|25|1|고유 연결 ID입니다.|  
|DatabaseName|28|8|사용자 문이 실행되는 데이터베이스의 이름입니다.|  
|NTUserName|32|8|Windows 사용자 이름입니다.|  
|NTDomainName|33|8|사용자가 속한 Windows 도메인입니다.|  
|ClientHostName|35|8|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공하면 이 데이터 열이 채워집니다.|  
|ClientProcessID|36|1|클라이언트 응용 프로그램의 프로세스 ID입니다.|  
|ApplicationName|37|8|서버 연결을 만든 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 응용 프로그램에서 전달한 값으로 채워집니다.|  
|NTCanonicalUserName|40|8|정식 사용자 이름(예: engineering.microsoft.com/software/someone)입니다.|  
|SPID|41|1|서버 프로세스 ID로, 사용자 세션을 고유하게 식별합니다. 이 SPI는 XML/A에서 사용하는 세션 GUID와 정확히 일치합니다.|  
|TextData|42|9|이벤트와 연결된 텍스트 데이터입니다.|  
|데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면|43|8|이벤트를 생성하는 서버의 이름입니다.|  
|RequestProperties|45|9|XMLA 요청 속성입니다.|  
  
## <a name="session-initialize"></a>Session Initialize  
  
|||||  
|-|-|-|-|  
|**열 이름**|**열 ID**|**열 유형**|**열 설명**|  
|CurrentTime|2|5|사용 가능한 경우 이벤트가 시작된 시간입니다. 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|StartTime|3|5|사용 가능한 경우 이벤트가 시작된 시간입니다. 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|ConnectionID|25|1|고유 연결 ID입니다.|  
|DatabaseName|28|8|사용자 문이 실행되는 데이터베이스의 이름입니다.|  
|NTUserName|32|8|Windows 사용자 이름입니다.|  
|NTDomainName|33|8|사용자가 속한 Windows 도메인입니다.|  
|ClientHostName|35|8|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공하면 이 데이터 열이 채워집니다.|  
|ClientProcessID|36|1|클라이언트 응용 프로그램의 프로세스 ID입니다.|  
|ApplicationName|37|8|서버 연결을 만든 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 응용 프로그램에서 전달한 값으로 채워집니다.|  
|NTCanonicalUserName|40|8|정식 사용자 이름(예: engineering.microsoft.com/software/someone)입니다.|  
|SPID|41|1|서버 프로세스 ID로, 사용자 세션을 고유하게 식별합니다. 이 SPI는 XML/A에서 사용하는 세션 GUID와 정확히 일치합니다.|  
|TextData|42|9|이벤트와 연결된 텍스트 데이터입니다.|  
|데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면|43|8|이벤트를 생성하는 서버의 이름입니다.|  
|RequestProperties|45|9|XMLA 요청 속성입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [Security Audit 이벤트 범주](security-audit-event-category.md)  
  
  