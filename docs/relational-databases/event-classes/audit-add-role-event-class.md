---
title: Audit Add Role 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Audit Add Role event class
ms.assetid: 4ea55922-608c-4db2-8b3f-873862755bba
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d75b377008825f64c703bcf949064b5b34796ccf
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52405960"
---
# <a name="audit-add-role-event-class"></a>Audit Add Role 이벤트 클래스
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **Audit Add Role** 이벤트 클래스는 데이터베이스에서 데이터베이스 역할이 추가되거나 제거될 때 발생합니다. 이 이벤트 클래스는 **sp_addrole** 및 **sp_droprole** 저장 프로시저에서 사용됩니다.  
  
 이 이벤트 클래스는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 이후 버전에서 제거될 수도 있습니다. **Audit Database Principal Management** 이벤트 클래스를 대신 사용하는 것이 좋습니다.  
  
## <a name="audit-add-role-event-class-data-columns"></a>Audit Add Role 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|설명|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 응용 프로그램에서 전달한 값으로 채워집니다.|10|예|  
|**ClientProcessID**|**int**|클라이언트 응용 프로그램이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다. 클라이언트가 클라이언트 프로세스 ID를 제공하면 이 데이터 열이 채워집니다.|9|예|  
|**DatabaseID**|**int**|USE *database* 문에서 지정한 데이터베이스 ID이거나, 지정한 인스턴스에 대해 USE *database* 문을 실행하지 않은 경우 기본 데이터베이스입니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ServerName **데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면** 에 데이터베이스 이름이 표시됩니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|예|  
|**DatabaseName**|**nvarchar**|사용자 문이 실행되는 데이터베이스의 이름입니다.|35|예|  
|**DBUserName**|**nvarchar**|데이터베이스에 있는 발급자의 사용자 이름입니다.|40|예|  
|**EventClass**|**int**|이벤트 유형 = 111|27|아니오|  
|**EventSequence**|**int**|요청 내에 지정된 이벤트 시퀀스입니다.|51|아니오|  
|**EventSubClass**|**int**|이벤트 하위 클래스의 유형입니다.<br /><br /> 1=추가<br /><br /> 2=삭제|21|예|  
|**HostName**|**nvarchar**|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공할 경우 이 데이터 열이 채워집니다. 호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.|8|예|  
|**IsSystem**|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|예|  
|**LoginName**|**nvarchar**|사용자 로그인 이름(DOMAIN\username 형식의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 로그인 자격 증명 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 보안 로그인)입니다.|11|예|  
|**LoginSid**|**image**|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 **sys.server_principals** 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|예|  
|**NTDomainName**|**nvarchar**|사용자가 속한 Windows 도메인입니다.|7|예|  
|**NTUserName**|**nvarchar**|Windows 사용자 이름입니다.|6|예|  
|**RequestID**|**int**|문을 포함하는 요청의 ID입니다.|49|예|  
|**RoleName**|**nvarchar**|추가 또는 제거되는 데이터베이스 역할의 이름입니다.|38|예|  
|**데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면**|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니오|  
|**SessionLoginName**|**Nvarchar**|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 **SessionLoginName** 은 Login1을 표시하고 **LoginName** 은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|예|  
|**SPID**|**int**|이벤트가 발생한 세션의 ID입니다.|12|예|  
|**StartTime**|**datetime**|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|예|  
|**성공**|**int**|1 = 성공, 0 = 실패. 예를 들어 값 1은 사용 권한 확인이 성공했음을 의미하고, 0은 확인이 실패했음을 의미합니다.|23|예|  
|**TransactionID**|**bigint**|시스템이 할당한 트랜잭션의 ID입니다.|4|예|  
|**XactSequence**|**bigint**|현재 트랜잭션을 설명하는 토큰입니다.|50|예|  
  
## <a name="see-also"></a>참고 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_addrole&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [sp_droprole&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [Audit Database Principal Management 이벤트 클래스](../../relational-databases/event-classes/audit-database-principal-management-event-class.md)  
  
  
