---
title: Broker:Message Undeliverable 이벤트 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Message Undeliverable event class
ms.assetid: f532b7c9-ca34-4bac-8dc3-53f9895fd6af
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f74322f4bd8c3a399da975160f08548320279e22
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603231"
---
# <a name="brokermessage-undeliverable-event-class"></a>Broker:Message Undeliverable 이벤트 클래스
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 Service Broker가 이 인스턴스의 서비스에 배달되어야 하는 수신 메시지를 보관할 수 없는 경우 **Broker:Message Undeliverable** 이벤트를 생성합니다. 전달되어야 하는 메시지는 [Broker:Forwarded Message Dropped 이벤트 클래스](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)를 참조하세요.  
  
## <a name="brokermessage-undeliverable-event-class-data-columns"></a>Broker:Message Undeliverable 이벤트 클래스 데이터 열  
  
|데이터 열|형식|설명|열 번호|필터 가능|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**Application Name**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 응용 프로그램에서 전달한 값으로 채워집니다.|10|사용자 계정 컨트롤|  
|**BigintData1**|**bigint**|배달할 수 없는 메시지의 시퀀스 번호입니다.|52|아니오|  
|**BigintData2**|**bigint**|마지막 메시지의 시퀀스 번호를 성공적으로 인식했습니다.|53|아니오|  
|**ClientProcessID**|**int**|클라이언트 응용 프로그램이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다. 클라이언트가 클라이언트 프로세스 ID를 제공하면 이 데이터 열이 채워집니다.|9|사용자 계정 컨트롤|  
|**DatabaseID**|**int**|USE *database* 문으로 지정한 데이터베이스 ID이거나 지정한 인스턴스에 대해 실행된 USE *database* 문이 없는 경우 기본 데이터베이스 ID입니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ServerName **데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면** 에 데이터베이스 이름이 표시됩니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|사용자 계정 컨트롤|  
|**오류**|**int**|이벤트의 텍스트에 대한 **sys.messages** 의 메시지 ID 번호입니다.|31|아니오|  
|**EventClass**|**int**|캡처된 이벤트 클래스 유형입니다. **Broker:MessageUndeliverable**의 경우 항상 **160**입니다.|27|아니오|  
|**EventSequence**|**int**|이 이벤트의 시퀀스 번호입니다.|51|아니오|  
|**EventSubClass**|**nvarchar**|배달할 수 없는 메시지가 순차화된 메시지인지 여부를 나타냅니다. 다음 두 값 중 하나입니다.<br /><br /> **순차화된 메시지**. 배달할 수 없는 메시지가 순차화된 메시지입니다.<br /><br /> **순차화되지 않은 메시지**. 배달할 수 없는 메시지가 순차화된 메시지가 아닙니다.|21|사용자 계정 컨트롤|  
|**GUID**|**uniqueidentifier**|배달할 수 없는 메시지가 속한 대화의 대화 ID입니다. 이 식별자는 메시지의 일부로 전송되며 양쪽 대화 상대 간에 공유합니다.|54|아니오|  
|**HostName**|**nvarchar**|클라이언트를 실행 중인 컴퓨터의 이름입니다. 클라이언트가 호스트 이름을 제공하면 이 데이터 열이 채워집니다. 호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.|8|사용자 계정 컨트롤|  
|**IntegerData**|**int**|배달할 수 없는 메시지의 조각 번호입니다.|25|아니오|  
|**IntegerData2**|**int**|배달할 수 없는 메시지가 인식한 메시지 조각 번호입니다.|55|아니오|  
|**IsSystem**|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|아니오|  
|**LoginName**|**nvarchar**|사용자 로그인 이름( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 로그인 또는 DOMAIN\Username 형식의 Windows 로그인 자격 증명)입니다.|11|아니오|  
|**LoginSid**|**image**|로그인한 사용자의 SID(보안 ID)입니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|사용자 계정 컨트롤|  
|**NTDomainName**|**nvarchar**|사용자가 속한 Windows 도메인입니다.|7|사용자 계정 컨트롤|  
|**NTUserName**|**nvarchar**|이 이벤트를 생성한 연결을 소유하고 있는 사용자의 이름입니다.|6|사용자 계정 컨트롤|  
|**ObjectName**|**nvarchar**|대화 상자의 대화 핸들입니다.|34|아니오|  
|**RoleName**|**nvarchar**|대화 핸들의 역할입니다. 이 역할은 **시작자** 또는 **대상**입니다.|38|아니오|  
|**데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면**|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니오|  
|**Severity**|**int**|이벤트 텍스트의 심각도 숫자입니다.|29|아니오|  
|**SPID**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 클라이언트와 관련된 프로세스에 할당한 서버 프로세스 ID입니다.|12|사용자 계정 컨트롤|  
|**StartTime**|**datetime**|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|사용자 계정 컨트롤|  
|**State**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 코드 내에서 이벤트가 생성된 위치를 나타냅니다. 이 이벤트가 생성될 수 있는 각 위치의 상태 코드는 서로 다릅니다. Microsoft 지원 엔지니어는 이 상태 코드를 사용하여 이벤트가 생성된 위치를 찾을 수 있습니다.|30|아니오|  
|**TextData**|**ntext**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 메시지를 배달할 수 없는 이유입니다.|1|사용자 계정 컨트롤|  
|**TransactionID**|**bigint**|시스템이 할당한 트랜잭션 ID입니다.|4|아니오|  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
