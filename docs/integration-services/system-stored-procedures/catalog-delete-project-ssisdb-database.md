---
title: catalog.delete_project(SSISDB 데이터베이스) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: f3431445-8dd2-443b-813e-b99db893977e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2b6235eadbbc2dea71ca809be42c3f81934c4495
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628351"
---
# <a name="catalogdeleteproject-ssisdb-database"></a>catalog.delete_project(SSISDB 데이터베이스)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 카탈로그에 있는 폴더에서 기존 프로젝트를 삭제합니다.  
  
## <a name="syntax"></a>구문  
  
```sql  
catalog.delete_project [ @folder_name = ] folder_name , [ @project_name = ] project_name  
```  
  
## <a name="arguments"></a>인수  
 [ @folder_name = ] *folder_name*  
 프로젝트가 있는 폴더의 이름입니다. *folder_name*은 **nvarchar(128)** 입니다.  
  
 [ @project_name = ] *project_name*  
 삭제할 프로젝트의 이름입니다. *project_name*은 **nvarchar(128)** 입니다.  
  
## <a name="return-code-value"></a>반환 코드 값  
 0(성공)  
  
## <a name="result-sets"></a>결과 집합  
 없음  
  
## <a name="permissions"></a>Permissions  
 이 저장 프로시저를 실행하려면 다음 권한 중 하나가 필요합니다.  
  
-   프로젝트에 대한 READ 및 MODIFY 권한  
  
-   **ssis_admin** 데이터베이스 역할에 대한 멤버 자격  
  
-   **sysadmin** 서버 역할에 대한 멤버 자격  
  
## <a name="errors-and-warnings"></a>오류 및 경고  
 다음 목록에서는 delete_project 저장 프로시저에서 오류가 발생하는 몇 가지 조건을 설명합니다.  
  
-   프로젝트가 없는 경우  
  
-   폴더가 없는 경우  
  
-   사용자에게 적절한 권한이 없는 경우  
  
## <a name="remarks"></a>Remarks  
 해당 프로젝트의 모든 개체 및 환경 참조는 프로젝트와 함께 삭제됩니다. 그러나 프로젝트 버전 및 관련 작업 레코드는 다음에 작업 정리 작업을 실행할 때까지 유지됩니다.  
  
  
