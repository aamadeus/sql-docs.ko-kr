---
title: BEGIN DIALOG CONVERSATION (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DIALOG CONVERSATION
- DIALOG
- BEGIN_DIALOG_TSQL
- BEGIN_DIALOG_CONVERSATION_TSQL
- DIALOG_CONVERSATION_TSQL
- DIALOG_TSQL
- BEGIN DIALOG
- BEGIN DIALOG CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker]
- beginning dialogs
- dialogs [Service Broker], beginning
- BEGIN DIALOG CONVERSATION statement
- cryptography [SQL Server], conversations
- opening conversations
- encryption [SQL Server], conversations
- starting conversations
ms.assetid: 8e814f9d-77c1-4906-b8e4-668a86fc94ba
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6e1f746ea0607759329b32499aed5887ee44b650
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="begin-dialog-conversation-transact-sql"></a>BEGIN DIALOG CONVERSATION(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  서비스 간 대화를 시작합니다. 대화는 두 서비스 간에 정확한 순서대로 한 번 메시징을 제공하는 대화 방법입니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
BEGIN DIALOG [ CONVERSATION ] @dialog_handle  
   FROM SERVICE initiator_service_name  
   TO SERVICE 'target_service_name'  
       [ , { 'service_broker_guid' | 'CURRENT DATABASE' }]   
   [ ON CONTRACT contract_name ]  
   [ WITH  
   [  { RELATED_CONVERSATION = related_conversation_handle   
      | RELATED_CONVERSATION_GROUP = related_conversation_group_id } ]   
   [ [ , ] LIFETIME = dialog_lifetime ]   
   [ [ , ] ENCRYPTION = { ON | OFF }  ] ]  
[ ; ]  
```  
  
## <a name="arguments"></a>인수  
 **@***dialog_handle*  
 BEGIN DIALOG CONVERSATION 문에서 반환하는 새 대화에 대한 시스템 생성 대화 핸들을 저장하는 데 사용되는 변수입니다. 변수 형식 이어야 합니다 **uniqueidentifier**합니다.  
  
 서비스에서 *initiator_service_name*  
 대화를 시작하는 서비스를 지정합니다. 지정된 이름은 현재 데이터베이스에 있는 서비스의 이름이어야 합니다. 시작자 서비스에 지정된 큐는 대상 서비스에서 반환하는 메시지와 이 대화에 대해 Service Broker에서 생성하는 메시지를 받습니다.  
  
 서비스에 **'***target_service_name***'**  
 대화를 시작하는 데 사용할 대상 서비스를 지정합니다. *target_service_name* 유형의 **nvarchar (256)**합니다. [!INCLUDE[ssSB](../../includes/sssb-md.md)]바이트 단위 비교를 사용 하 여 일치 하는 *target_service_name* 문자열입니다. 즉, 비교 시 대/소문자가 구분되고 현재 데이터 정렬은 고려되지 않습니다.  
  
 *service_broker_guid*  
 대상 서비스를 호스팅하는 데이터베이스를 지정합니다. 제공 하 여 특정 데이터베이스와 통신할 수 대상 서비스의 인스턴스를 호스트 하는 여러 개의 데이터베이스는 *service_broker_guid*합니다.  
  
 *service_broker_guid* 유형의 **nvarchar (128)**합니다. 찾을 *service_broker_guid* 는 데이터베이스에 대 한 데이터베이스에서 다음 쿼리를 실행 합니다.  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID() ;  
```  
  
> [!NOTE]  
>  포함된 데이터베이스에서는 이 옵션을 사용할 수 없습니다.  
  
 **'**현재 데이터베이스**'**  
 대화를 사용 하도록 지정 된 *service_broker_guid* 현재 데이터베이스에 대 한 합니다.  
  
 ON CONTRACT *contract_name*  
 이 대화가 따르는 계약을 지정합니다. 계약은 현재 데이터베이스에 있어야 합니다. 대상 서비스가 지정된 계약에서 새 대화를 수락하지 않으면 [!INCLUDE[ssSB](../../includes/sssb-md.md)]는 대화에 대한 오류 메시지를 반환합니다. 이 절을 생략 하는 경우 대화 라는 계약을 따릅니다. **기본**합니다.  
  
 RELATED_CONVERSATION  **=**  *related_conversation_handle*  
 기존 대화 그룹에서 새 대화를 추가할 그룹을 지정합니다. 이 절이 있으면 새 대화 상자로 지정한 대화와 같은 대화 그룹에 속하게 *related_conversation_handle*합니다. *related_conversation_handle*형식으로 암시적으로 변환할 유형 이어야 **uniqueidentifier**합니다. 문이 실패 하는 경우는 *related_conversation_handle* 기존 대화를 참조 하지 않습니다.  
  
 RELATED_CONVERSATION_GROUP  **=**  *related_conversation_group_id*  
 기존 대화 그룹에서 새 대화를 추가할 그룹을 지정합니다. 이 절이 있으면 새 대화 상자에서 지정한 대화 그룹에 추가 됩니다 *related_conversation_group_id*합니다. *related_conversation_group_id*형식으로 암시적으로 변환할 유형 이어야 **uniqueidentifier**합니다. 경우 *related_conversation_group_id*가 기존 대화 그룹, service broker 참조 하지 않습니다 새 대화 그룹을 만듭니다 지정 된 *related_conversation_group_id* 및 해당 대화 그룹을 새 대화를 연결합니다.  
  
 수명  **=**  *dialog_lifetime*  
 대화가 열려 있는 최대 시간을 지정합니다. 대화를 완료하려면 수명이 만료되기 전에 두 끝점에서 대화를 명시적으로 종료해야 합니다. *dialog_lifetime* 값을 초 단위로 표시 해야 합니다. 형식의 수명은 **int**합니다. 대화 수명은의 최대값 없음 수명 절을 지정 하는 경우는 **int** 데이터 형식입니다.  
  
 ENCRYPTION  
 인스턴스 외부로 보낼 때이 대화 상자에서 보내고 받는 메시지를 암호화 해야 여부 지정 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 암호화 해야 하는 대화 상자는는 *보안된 대화*합니다. ENCRYPTION = ON인 경우 암호화 지원에 필요한 인증서가 구성되어 있지 않으면 [!INCLUDE[ssSB](../../includes/sssb-md.md)]는 대화에 대한 오류 메시지를 반환합니다. 하는 경우 암호화 = OFF, 원격 서비스 바인딩에 대해 구성 된 경우 암호화가 사용 되는 *target_service_name*; 그렇지 않으면 메시지가 암호화 되지 않은 상태로 전송 됩니다. 이 절이 없으면 기본값은 ON입니다.  
  
> [!NOTE]  
>  같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 서비스와 주고받는 메시지는 암호화되지 않습니다. 그러나 대화에 대한 서비스가 다른 데이터베이스에 있는 경우 암호화를 사용하는 대화에는 암호화에 대한 데이터베이스 마스터 키와 인증서가 계속 필요합니다. 따라서 대화가 진행 중인 동안 데이터베이스 중 하나를 다른 인스턴스로 이동해도 대화를 계속할 수 있습니다.  
  
## <a name="remarks"></a>주의  
 모든 메시지는 대화의 일부입니다. 따라서 시작 서비스는 대상 서비스로 메시지를 보내기 전에 대상 서비스와 대화를 시작해야 합니다. BEGIN DIALOG CONVERSATION 문에서 지정한 정보는 편지의 주소와 유사합니다. [!INCLUDE[ssSB](../../includes/sssb-md.md)]는 이 정보를 사용하여 올바른 서비스로 메시지를 배달합니다. TO SERVICE 절에서 지정한 서비스는 메시지가 전달되는 주소이고, FROM SERVICE 절에서 지정한 서비스는 회신 메시지에 사용되는 반송 주소입니다.  
  
 대화의 대상이 BEGIN DIALOG CONVERSATION을 호출할 필요는 없습니다. [!INCLUDE[ssSB](../../includes/sssb-md.md)]는 시작자로부터 대화의 첫 번째 메시지가 도착하면 대상 데이터베이스에 대화를 만듭니다.  
  
 대화를 시작하면 시작 서비스에 대해 데이터베이스에 대화 끝점이 생성되지만 대상 서비스를 호스팅하는 인스턴스에 네트워크로 연결되지는 않습니다. [!INCLUDE[ssSB](../../includes/sssb-md.md)]는 첫 번째 메시지를 보낼 때까지 대화의 대상과 통신을 설정하지 않습니다.  
  
 BEGIN DIALOG CONVERSATION 문에서 관련 대화 또는 관련 대화 그룹을 지정하지 않으면 [!INCLUDE[ssSB](../../includes/sssb-md.md)]는 새 대화에 대해 새로운 대화 그룹을 만듭니다.  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]에서는 대화를 임의로 그룹화할 수 없습니다. 대화 그룹의 모든 대화에는 대화의 시작자 또는 대상으로 FROM 절에 서비스가 지정되어 있어야 합니다.  
  
 BEGIN DIALOG CONVERSATION 명령은 포함 된 대화 그룹을 잠급니다는 *dialog_handle* 반환 합니다. 명령은 RELATED_CONVERSATION_GROUP 절에 대 한 대화 그룹을 포함 하는 경우 *dialog_handle* 대화 그룹에 지정 된 *related_conversation_group_id* 매개 변수입니다. 명령에 RELATED_CONVERSATION 절, 대화 그룹에 대 한 포함 되 면 *dialog_handle* 연결 된 대화 그룹의 *related_conversation_handle* 지정 합니다.  
  
 BEGIN DIALOG CONVERSATION은 사용자 정의 함수에 유효하지 않습니다.  
  
## <a name="permissions"></a>Permissions  
 대화를 시작하려면 현재 사용자는 명령의 FROM 절에서 지정한 서비스의 큐에 대한 RECEIVE 권한과 지정한 계약에 대한 REFERENCES 권한이 있어야 합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-beginning-a-dialog"></a>1. 대화 시작  
 다음 예에서는 대화를 시작하고 `@dialog_handle.`에 대화 식별자를 저장합니다. `//Adventure-Works.com/ExpenseClient` 서비스는 대화의 시작자이고 `//Adventure-Works.com/Expenses` 서비스는 대화의 대상입니다. 대화는 `//Adventure-Works.com/Expenses/ExpenseSubmission` 계약을 따릅니다.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
### <a name="b-beginning-a-dialog-with-an-explicit-lifetime"></a>2. 명시적으로 수명을 지정하고 대화 시작  
 다음 예에서는 대화를 시작하고 `@dialog_handle`에 대화 식별자를 저장합니다. `//Adventure-Works.com/ExpenseClient` 서비스는 대화의 시작자이고 `//Adventure-Works.com/Expenses` 서비스는 대화의 대상입니다. 대화는 `//Adventure-Works.com/Expenses/ExpenseSubmission` 계약을 따릅니다. END CONVERSATION 명령으로 `60`초 내에 대화가 닫히지 않으면 Broker에서 오류가 발생하여 대화가 종료됩니다.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH LIFETIME = 60 ;  
```  
  
### <a name="c-beginning-a-dialog-with-a-specific-broker-instance"></a>3. 특정 Broker 인스턴스로 대화 시작  
 다음 예에서는 대화를 시작하고 `@dialog_handle`에 대화 식별자를 저장합니다. `//Adventure-Works.com/ExpenseClient` 서비스는 대화의 시작자이고 `//Adventure-Works.com/Expenses` 서비스는 대화의 대상입니다. 대화는 `//Adventure-Works.com/Expenses/ExpenseSubmission` 계약을 따릅니다. Broker는 `a326e034-d4cf-4e8b-8d98-4d7e1926c904.` GUID에 의해 식별되는 Broker로 이 대화의 메시지를 라우팅합니다.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses',   
              'a326e034-d4cf-4e8b-8d98-4d7e1926c904'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
### <a name="d-beginning-a-dialog-and-relating-it-to-an-existing-conversation-group"></a>4. 대화를 시작하여 기존 대화 그룹에 연결  
 다음 예에서는 대화를 시작하고 `@dialog_handle`에 대화 식별자를 저장합니다. `//Adventure-Works.com/ExpenseClient` 서비스는 대화의 시작자이고 `//Adventure-Works.com/Expenses` 서비스는 대화의 대상입니다. 대화는 `//Adventure-Works.com/Expenses/ExpenseSubmission` 계약을 따릅니다. Broker는 새 대화 그룹을 만들지 않고 `@conversation_group_id`로 식별되는 대화 그룹에 대화를 연결합니다.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_group_id = <retrieve conversation group ID from database>  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH RELATED_CONVERSATION_GROUP = @conversation_group_id ;  
```  
  
### <a name="e-beginning-a-dialog-with-an-explicit-lifetime-and-relating-the-dialog-to-an-existing-conversation"></a>5. 명시적으로 수명을 지정하여 대화를 시작하고 기존 대화에 대화 연결  
 다음 예에서는 대화를 시작하고 `@dialog_handle`에 대화 식별자를 저장합니다. `//Adventure-Works.com/ExpenseClient` 서비스는 대화의 시작자이고 `//Adventure-Works.com/Expenses` 서비스는 대화의 대상입니다. 대화는 `//Adventure-Works.com/Expenses/ExpenseSubmission` 계약을 따릅니다. 새 대화는 `@existing_conversation_handle`이 속하는 대화 그룹에 똑같이 속합니다. END CONVERSATION 명령으로 `600`초 내에 대화가 닫히지 않으면 [!INCLUDE[ssSB](../../includes/sssb-md.md)]에서 오류가 발생하여 대화가 종료됩니다.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER  
DECLARE @existing_conversation_handle UNIQUEIDENTIFIER  
  
SET @existing_conversation_handle = <retrieve conversation handle from database>  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH RELATED_CONVERSATION = @existing_conversation_handle  
   LIFETIME = 600 ;  
```  
  
### <a name="f-beginning-a-dialog-with-optional-encryption"></a>6. 선택적 암호화를 사용하여 대화 시작  
 다음 예에서는 대화를 시작하고 `@dialog_handle`에 대화 식별자를 저장합니다. `//Adventure-Works.com/ExpenseClient` 서비스는 대화의 시작자이고 `//Adventure-Works.com/Expenses` 서비스는 대화의 대상입니다. 대화는 `//Adventure-Works.com/Expenses/ExpenseSubmission` 계약을 따릅니다. 이 예의 대화에서는 암호화를 사용할 수 없는 경우 암호화를 사용하지 않고 네트워크를 통해 메시지를 전달할 수 있습니다.  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH ENCRYPTION = OFF ;  
```  
  
## <a name="see-also"></a>관련 항목:  
 [BEGIN CONVERSATION TIMER &#40; Transact SQL &#41;](../../t-sql/statements/begin-conversation-timer-transact-sql.md)   
 [END CONVERSATION &#40; Transact SQL &#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [MOVE CONVERSATION &#40; Transact SQL &#41;](../../t-sql/statements/move-conversation-transact-sql.md)   
 [sys.conversation_endpoints&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  
