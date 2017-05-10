---
title: "경고 속성 - 새 경고(일반 페이지) | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 59001ff22217993697aeb76b754d894fdb9103ed
ms.lasthandoff: 04/11/2017

---
# <a name="alert-properties---new-alert-general-page"></a>경고 속성 - 새 경고(일반 페이지)
이 페이지를 사용하여 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트 경고의 일반 속성을 확인하고 수정할 수 있습니다.  
  
## <a name="options"></a>옵션  
**이름**  
경고 이름을 변경합니다.  
  
**사용**  
경고를 설정합니다. 경고를 설정하지 않으면 경고에 지정된 동작이 수행되지 않습니다.  
  
**형식**  
경고 유형을 선택합니다.  
  
-   **SQL Server 이벤트 경고** - [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 이벤트 로그의 메시지에 응답합니다.  
  
-   **SQL Server 성능 조건 경고** - 성능 카운터의 특정 조건에 응답합니다.  
  
-   **WMI 이벤트 경고** - WMI(Windows Management Instrumentation) 이벤트에 응답합니다.  
  
## <a name="sql-server-event-alert-options"></a>SQL Server 이벤트 경고 옵션  
**데이터베이스 이름**  
이벤트에 대한 데이터베이스를 지정하거나, 이벤트가 발생하는 데이터베이스에 관계없이 메시지에 응답하도록 하려면 **모든 데이터베이스** 를 지정합니다.  
  
**오류 번호**  
이 이벤트가 오류에 응답하도록 지정하고 오류 번호를 지정합니다.  
  
**Severity**  
이 이벤트가 특정 심각도를 지닌 메시지에 응답하도록 지정하고 심각도를 지정합니다.  
  
**메시지에 다음 텍스트가 포함될 때 경고 발생**  
특정 문자열로 이벤트를 필터링합니다. 이 옵션을 선택하면 경고가 특정 문자열을 포함하는 이벤트에 대해서만 응답합니다.  
  
**메시지 텍스트**  
이벤트를 필터링할 때 사용할 문자열을 지정합니다.  
  
## <a name="sql-server-performance-condition-alerts"></a>SQL Server 성능 조건 경고  
**개체**  
모니터링할 성능 개체를 지정합니다.  
  
**카운터**  
모니터링할 성능 개체 내의 카운터를 지정합니다.  
  
**인스턴스**  
모니터링할 카운터의 인스턴스를 지정합니다.  
  
**경고 발생 카운터**  
경고가 응답하는 카운터의 동작을 지정합니다. 예를 들어 경고를 **Free space in tempdb (KB)** 카운터의 값이 특정 값 미만이 될 때 응답하도록 지정하거나 **SQL Compilations/sec** 가 특정 값을 초과할 때 응답하도록 지정할 수 있습니다.  
  
**Value**  
카운터에 대한 값을 지정합니다.  
  
## <a name="wmi-event-alert-options"></a>WMI 이벤트 경고 옵션  
**네임스페이스**  
WQL(WMI Query Language) 문에 사용할 네임스페이스를 지정합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트를 실행하는 컴퓨터의 네임스페이스만 지원됩니다.  
  
**Query**  
경고 응답 이벤트를 식별하는 WQL 문을 지정합니다.  
  
## <a name="see-also"></a>참고 항목  
[경고](../../ssms/agent/alerts.md)  
[서버 이벤트용 WMI 공급자에 WQL 사용](http://msdn.microsoft.com/en-us/58b67426-1e66-4445-8e2c-03182e94c4be)  
[오류 번호를 사용하여 경고 만들기](../../ssms/agent/create-an-alert-using-an-error-number.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
