---
title: sys.dm_io_backup_tapes (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_backup_tapes
- dm_io_backup_tapes_TSQL
- sys.dm_io_backup_tapes_TSQL
- dm_io_backup_tapes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_backup_tapes dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 195c8dc2db7011801023e7e21e68ed1f5ed75a6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603471"
---
# <a name="sysdmiobackuptapes-transact-sql"></a>sys.dm_io_backup_tapes(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  백업과 연관된 테이프 장치 목록 및 탑재 요청 상태를 반환합니다.   
 
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**physical_device_name**|**nvarchar(520)**|백업을 수행할 수 있는 실제 물리적 장치의 이름입니다. Null을 허용하지 않습니다.|  
|**logical_device_name**|**nvarchar(256)**|드라이브에 대 한 사용자 지정 이름 (에서 **sys.backup_devices**). 사용자가 지정한 이름이 없으면 NULL입니다. Null을 허용합니다.|  
|**상태**|**int**|테이프의 상태입니다.<br /><br /> 1 = 열려 있음. 사용 가능.<br /><br /> 2 = 탑재 보류 중<br /><br /> 3 = 사용 중<br /><br /> 4 = 로드 중<br /><br /> **참고:** 테이프를 로드 하는 동안 (**상태 = 4**), 미디어 레이블을 읽지 않습니다. 와 같은 미디어 레이블 값을 복사 하는 열 **media_sequence_number**를 예상 하는 표시 값을 테이프에 실제 값에서 다를 수 있습니다. 레이블을 읽은 후 **상태** 변경 내용 **3** (사용)에서 미디어 레이블 열에는 다음 로드 되는 실제 테이프가 반영 합니다.<br /><br /> Null을 허용하지 않습니다.|  
|**status_desc**|**nvarchar(520)**|테이프 상태에 대한 설명입니다.<br /><br /> AVAILABLE<br /><br /> MOUNT PENDING<br /><br /> IN USE<br /><br /> LOADING MEDIA<br /><br /> Null을 허용하지 않습니다.|  
|**mount_request_time**|**datetime**|탑재를 요청한 시간입니다. 보류 중인 탑재 요청이 없을 경우 NULL (**상태! = 2**). Null을 허용합니다.|  
|**mount_expiration_time**|**datetime**|탑재 요청이 만료(시간 초과)되는 시간입니다. 보류 중인 탑재 요청이 없을 경우 NULL (**상태! = 2**). Null을 허용합니다.|  
|**database_name**|**nvarchar(256)**|이 장치에 백업할 데이터베이스입니다. Null을 허용합니다.|  
|**spid**|**int**|세션 ID입니다. 테이프의 사용자를 식별합니다. Null을 허용합니다.|  
|**명령**|**int**|백업을 수행하는 명령입니다. Null을 허용합니다.|  
|**command_desc**|**nvarchar(120)**|명령에 대한 설명입니다. Null을 허용합니다.|  
|**media_family_id**|**int**|미디어 패밀리의 인덱스 (1... *n*), *n* 미디어 세트의 미디어 패밀리 수입니다. Null을 허용합니다.|  
|**media_set_name**|**nvarchar(256)**|미디어 세트를 만들 때 MEDIANAME 옵션으로 지정한 미디어 세트의 이름(있는 경우)입니다. Null을 허용합니다.|  
|**media_set_guid**|**uniqueidentifier**|미디어 세트를 고유하게 식별하는 식별자입니다. Null을 허용합니다.|  
|**media_sequence_number**|**int**|미디어 패밀리 내 볼륨의 인덱스 (1... *n*). Null을 허용합니다.|  
|**tape_operation**|**int**|수행 중인 테이프 작업:<br /><br /> 1 = 읽기<br /><br /> 2 = 포맷<br /><br /> 3 = 초기화<br /><br /> 4 = 추가<br /><br /> Null을 허용합니다.|  
|**tape_operation_desc**|**nvarchar(120)**|수행 중인 테이프 작업입니다.<br /><br /> READ<br /><br /> FORMAT<br /><br /> INIT<br /><br /> APPEND<br /><br /> Null을 허용합니다.|  
|**mount_request_type**|**int**|탑재 요청 유형입니다.<br /><br /> 1 = 특정 테이프. 으로 식별 되는 테이프가 합니다 **media_\***  필드는 필수입니다.<br /><br /> 2 = 다음 미디어 패밀리. 아직 복원되지 않은 다음 미디어 패밀리를 요청합니다. 이 유형은 복원하는 장치 수가 미디어 패밀리 수보다 적을 때 사용됩니다.<br /><br /> 3 = 연속 테이프. 미디어 패밀리를 확장 중이며 연속 테이프를 요청합니다.<br /><br /> Null을 허용합니다.|  
|**mount_request_type_desc**|**nvarchar(120)**|탑재 요청 유형입니다.<br /><br /> SPECIFIC TAPE<br /><br /> NEXT MEDIA FAMILY<br /><br /> CONTINUATION VOLUME<br /><br /> Null을 허용합니다.|  
  
## <a name="permissions"></a>사용 권한  
 서버에 대해 VIEW SERVER STATE 권한이 있어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [I O 관련 동적 관리 뷰 및 함수 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

