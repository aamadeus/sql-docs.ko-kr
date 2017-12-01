---
title: sp_replmonitorchangepublicationthreshold (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords: sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e24fd4746ee5a93489e55b6cf16edc0150c647b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="spreplmonitorchangepublicationthreshold-transact-sql"></a>sp_replmonitorchangepublicationthreshold(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  게시에 대한 모니터링 임계값 메트릭을 변경합니다. 복제 모니터링에 사용되는 이 저장 프로시저는 배포 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_replmonitorchangepublicationthreshold [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @metric_id = ] metric_id ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'   
    [ , [ @value = ] value ]   
    [ , [ @shouldalert = ] shouldalert ]   
    [ , [ @mode = ] mode ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@publisher**  =] **'***게시자***'**  
 게시자의 이름입니다. *게시자* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@publisher_db**  =] **'***publisher_db***'**  
 게시된 데이터베이스의 이름입니다. *publisher_db* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@publication**  =] **'***게시***'**  
 모니터링 임계값 특성이 변경되는 게시의 이름입니다. *게시* 은 **sysname**, 기본값은 없습니다.  
  
 [  **@publication_type**  =] *publication_type*  
 게시의 유형입니다. *publication_type* 은 **int**, 다음이 값 중 하나일 수 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|**0**|트랜잭션 게시|  
|**1**|스냅숏 게시|  
|**2**|병합 게시|  
|NULL(기본값)|복제에서 게시 유형을 확인하려고 합니다.|  
  
 [  **@metric_id**  =] *metric_id*  
 변경될 게시 임계값 메트릭의 ID입니다. *metric_id* 은 **int**, 기본값은 NULL 이며 다음이 값 중 하나일 수 있습니다.  
  
|값|메트릭 이름|  
|-----------|-----------------|  
|**1**|**expiration** - 트랜잭션 게시에 대한 구독의 만료가 임박했는지 모니터링합니다.|  
|**2**|**latency** - 트랜잭션 게시에 대한 구독의 성능을 모니터링합니다.|  
|**4**|**mergeexpiration** - 병합 게시에 대한 구독의 만료가 임박했는지 모니터링합니다.|  
|**5**|**mergeslowrunduration** -저대역폭 (전화 접속) 연결을 통한 병합 동기화의 기간을 모니터링 합니다.|  
|**6**|**mergefastrunduration** -고대역폭 local area network (LAN) 연결을 통한 병합 동기화의 기간을 모니터링 합니다.|  
|**7**|**mergefastrunspeed** - 고대역폭(LAN) 연결을 통한 병합 동기화의 동기화 속도를 모니터링합니다.|  
|**8**|**mergeslowrunspeed** -저대역폭 (전화 접속) 연결을 통한 병합 동기화의 동기화 속도 모니터링 합니다.|  
  
 지정 해야 *metric_id* 또는 *thresholdmetricname*합니다. 경우 *thresholdmetricname* 을 지정할 경우 *metric_id* NULL 이어야 합니다.  
  
 [  **@thresholdmetricname**  =] **'***thresholdmetricname***'**  
 변경될 게시 임계값 메트릭의 이름입니다. *thresholdmetricname* 은 **sysname**, 기본값은 NULL입니다. 지정 해야 *thresholdmetricname* 또는 *metric_id*합니다. 경우 *metric_id* 을 지정할 경우 *thresholdmetricname* NULL 이어야 합니다.  
  
 [  **@value**  =] *값*  
 게시 임계값 메트릭의 새 값입니다. *값* 은 **int**, 기본값은 NULL입니다. 경우 **null**, 다음 메트릭 값이 업데이트 되지 않습니다.  
  
 [  **@shouldalert**  =] *shouldalert*  
 게시 임계값 메트릭에 도달하면 경고가 생성되는지 여부를 나타냅니다 *shouldalert* 은 **비트**, 기본값은 NULL입니다. 값이 **1** 이면 경고가 생성 되 고 값이 **0** 의미 경고가 생성 되지 않습니다.  
  
 [  **@mode**  =] *모드*  
 게시 임계값 메트릭이 사용되는지 여부를 나타냅니다. *모드* 은 **tinyint**, 기본값은 **1**합니다. 값이 **1** 이 메트릭의 모니터링이 사용 하는 의미 하 고 값의 **2** 이 메트릭에 대 한 모니터링을 사용할 수 없다는 것을 의미 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>주의  
 **sp_replmonitorchangepublicationthreshold** 모든 유형의 복제와 함께 사용 됩니다.  
  
## <a name="permissions"></a>Permissions  
 구성원만는 **db_owner** 또는 **replmonitor** 고정된 데이터베이스 역할이 배포 데이터베이스에서 실행할 수 있는 **sp_replmonitorchangepublicationthreshold**합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [프로그래밍 방식으로 복제 모니터링](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  