---
title: sp_check_for_sync_trigger (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d274e25b3a12a4fdd60c32365626bcb9ba912848
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628701"
---
# <a name="spcheckforsynctrigger-transact-sql"></a>sp_check_for_sync_trigger(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  사용자 정의 트리거 또는 저장 프로시저가 즉시 업데이트 구독에 사용되는 복제 트리거의 컨텍스트에서 호출되고 있는지 여부를 결정합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자 또는 구독 데이터베이스의 구독자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>인수  
 [ **@tabid =** ] '*tabid*'  
 즉시 업데이트 트리거의 발생 여부가 확인되는 테이블의 개체 ID입니다. *tabid* 됩니다 **int** 기본값은 없습니다.  
  
 [ **@trigger_op =** ] '*trigger_output_parameters*' 출력  
 출력 매개 변수에서 호출되고 있는 트리거 유형을 반환할지 여부를 지정합니다. *trigger_output_parameters* 됩니다 **char(10)** 이며 다음이 값 중 하나일 수 있습니다.  
  
|값|Description|  
|-----------|-----------------|  
|**기능**|INSERT 트리거|  
|**Upd**|UPDATE 트리거|  
|**Del**|DELETE 트리거|  
|NULL(기본값)||  
  
 [  **@fonpublisher =** ] *fonpublisher*  
 저장 프로시저를 실행하는 위치를 지정합니다. *fonpublisher* 됩니다 **비트**을 기본값인 0 사용 하 여 합니다. 값이 0인 경우 구독자에서 실행되며 값이 1인 경우 게시자에서 실행됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0은 저장 프로시저가 즉시 트리거 업데이트의 컨텍스트 내에서 호출되지 않고 있음을 의미합니다. 즉시 업데이트 트리거의 컨텍스트 내에서 호출 되 고에서 반환 되는 트리거 유형의 1 나타냅니다 *@trigger_op*합니다.  
  
## <a name="remarks"></a>Remarks  
 **sp_check_for_sync_trigger** 스냅숏 복제 및 트랜잭션 복제에 사용 됩니다.  
  
 **sp_check_for_sync_trigger** 복제 및 사용자 정의 트리거 사이 조정 하는 데 사용 됩니다. 이 저장 프로시저는 복제 트리거의 컨텍스트 내에서 호출되고 있는지 확인합니다. 예를 들어, 프로시저를 호출할 수 있습니다 **sp_check_for_sync_trigger** 사용자 정의 트리거 본문에서 합니다. 하는 경우 **sp_check_for_sync_trigger** 반환 **0**, 사용자 정의 트리거가 처리를 계속 합니다. 하는 경우 **sp_check_for_sync_trigger** 반환 **1**, 사용자 정의 트리거가 종료 됩니다. 따라서 복제 트리거에 의해 테이블이 업데이트될 때 사용자 정의 트리거가 실행되지 않습니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 구독자 테이블의 트리거에 사용될 수 있는 코드를 보여 줍니다.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>예제  
 코드; 게시자의 테이블에 트리거를 추가할 수도 있습니다. 코드는 유사 하지만 호출 **sp_check_for_sync_trigger** 추가 매개 변수를 포함 합니다.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>사용 권한  
 **sp_check_for_sync_trigger** SELECT 권한이 있는 모든 사용자가 저장된 프로시저를 실행할 수 있습니다 합니다 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) 시스템 뷰.  
  
## <a name="see-also"></a>관련 항목  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
