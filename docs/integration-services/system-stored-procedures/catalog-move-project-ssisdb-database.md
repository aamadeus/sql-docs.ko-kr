---
title: "catalog.move_project (SSISDB 데이터베이스) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ef3b0325-d8e9-472b-bf11-7d3efa6312ff
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5b091ccea1f733ebbf6e52308d17c7bdb7449cbe
ms.contentlocale: ko-kr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogmoveproject---ssisdb-database"></a>catalog.move_project-SSISDB 데이터베이스
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 카탈로그 내에서 폴더 간에 프로젝트를 이동합니다.  
  
## <a name="syntax"></a>구문  
  
```tsql  
move_project [ @source_folder = ] source_folder  
    , [ @project_name = ] project_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>인수  
 [ @source_folder =] *source_folder*  
 이동하기 전의 프로젝트가 있는 원본 폴더의 이름입니다. *source_folder* 은 **nvarchar (128)**합니다.  
  
 [ @project_name =] *project_name*  
 이동할 프로젝트의 이름입니다. *project_name* 은 **nvarchar (128)**합니다.  
  
 [ @destination_folder =] *destination_folder*  
 이동한 후의 프로젝트가 있는 대상 폴더의 이름입니다. *destination_folder* 은 **nvarchar (128)**합니다.  
  
## <a name="return-code-value"></a>반환 코드 값  
 0(성공)  
  
## <a name="result-sets"></a>결과 집합  
 없음  
  
## <a name="permissions"></a>Permissions  
 이 저장 프로시저를 실행하려면 다음 권한 중 하나가 필요합니다.  
  
-   이동할 프로젝트에 대한 READ 및 MODIFY 권한과 대상 폴더에 대한 CREATE_OBJECTS 권한  
  
-   멤버 자격에는 **ssis_admin** 데이터베이스 역할  
  
-   멤버 자격에는 **sysadmin** 서버 역할  
  
## <a name="errors-and-warnings"></a>오류 및 경고  
 다음 목록에서는 이 저장 프로시저에서 오류가 발생하는 몇 가지 조건을 설명합니다.  
  
-   프로젝트가 없는 경우  
  
-   원본 폴더가 없는 경우  
  
-   대상 폴더가 없거나 대상 폴더에 이름이 같은 프로젝트가 이미 있는 경우  
  
-   사용자에게 적절한 권한이 없는 경우  
  
## <a name="remarks"></a>주의  
 프로젝트가 원본 폴더에서 대상 폴더로 이동되면 원본 폴더 및 해당 환경 참조에서 프로젝트가 삭제됩니다. 대상 폴더에는 동일한 프로젝트 및 환경 참조가 생성됩니다. 상대 환경 참조는 이동 후 다른 폴더로 확인되고, 절대 참조는 이동 후 같은 폴더로 확인됩니다.  
  
> [!NOTE]  
>  프로젝트에는 상대 환경 참조 또는 절대 환경 참조가 있을 수 있습니다. 상대 참조는 환경을 이름으로 참조하며 환경이 프로젝트와 같은 폴더에 있어야 합니다. 절대 참조는 환경을 이름과 폴더로 참조하며 프로젝트와 다른 폴더에 있는 환경을 참조합니다.  
  
  