---
title: "catalog.packages (SSISDB 데이터베이스) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f836c2b1bdf59f157f10abb708ed55f99dfc9f0f
ms.contentlocale: ko-kr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages(SSISDB 데이터베이스)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  에 표시 되는 모든 패키지에 대 한 세부 정보가 표시 됩니다는 **SSISDB** 카탈로그입니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|패키지의 고유 식별자(ID)입니다.|  
|name|**nvarchar(256)**|패키지의 고유 이름입니다.|  
|package_guid|**uniqueidentifier**|패키지를 식별하는 GUID(Globally Unique Identifier)입니다.|  
|description|**nvarchar (1024)**|패키지에 대한 설명(옵션)입니다.|  
|package_format_version|**int**|패키지를 개발하는 데 사용된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 버전입니다.|  
|version_major|**int**|패키지의 주 버전입니다.|  
|version_minor|**int**|패키지의 부 버전입니다.|  
|version_build|**int**|패키지의 빌드 버전입니다.|  
|version_comments|**nvarchar (1024)**|패키지 버전에 대한 설명(옵션)입니다.|  
|version_guid|**uniqueidentifier**|패키지 버전을 고유하게 식별하는 GUID입니다.|  
|project_id|**bigint**|프로젝트의 고유 ID입니다.|  
|entry_point|**bit**|값 `1`은 패키지가 직접 시작되도록 만들어졌음을 의미하고, 값 `0`은 패키지가 패키지 실행 태스크로 다른 패키지에 의해 시작되도록 만들어졌음을 의미합니다. 기본값은 `1`합니다.|  
|validation_status|**char(1)**|유효성 검사의 상태입니다.|  
|last_validation_time|**(7)**|마지막 유효성 검사 시간입니다.|  
  
## <a name="remarks"></a>주의  
 이 뷰는 카탈로그에 있는 각 패키지에 대한 행을 표시합니다.  
  
## <a name="permissions"></a>Permissions  
 이 뷰를 보려면 다음 권한 중 하나가 필요합니다.  
  
-   해당 프로젝트에 대한 READ 권한  
  
-   멤버 자격에는 **ssis_admin** 데이터베이스 역할  
  
-   멤버 자격에는 **sysadmin** 서버 역할입니다.  
  
> [!NOTE]  
>  프로젝트에 대한 READ 권한이 있으면 해당 프로젝트와 연결된 모든 패키지 및 환경 참조에 대해서도 READ 권한을 가집니다. 행 수준 보안이 적용됩니다. 따라서 볼 수 있는 권한이 있는 행만 표시됩니다.  
  
  