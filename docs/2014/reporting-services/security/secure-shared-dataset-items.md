---
title: 공유 데이터 집합 항목 보안 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08e6d8b5-d88c-4ed2-9c05-55c757e00014
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 69369e5f1701ea1807a42bfb426f8cd26073e2c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080133"
---
# <a name="secure-shared-dataset-items"></a>공유 데이터 집합 항목 보안 설정
  보고서 서버에서 공유 데이터 집합 항목을 여러 보고서에서 사용할 수 있습니다. 공유 데이터 집합에 보안을 설정하여 사용자가 해당 항목에 대해 갖는 액세스 수준을 제어할 수 있습니다. 기본적으로 **Administrators** 기본 제공 그룹의 멤버인 사용자만 공유 데이터 집합 보기, 속성 수정, 캐싱 설정, 캐시 새로 고침 계획 만들기, 항목 삭제 등의 작업을 수행할 수 있습니다. 다른 모든 사용자에 대해서는 공유 데이터 집합에 대한 액세스를 허용하는 역할 할당을 만들어야 합니다.  
  
 보안을 설정하려면 공유 데이터 집합에 대한 액세스 권한이 있는 사용자 또는 그룹 계정을 지정하는 역할 할당을 만듭니다.  
  
## <a name="role-based-access-to-shared-datasets"></a>공유 데이터 집합에 대한 역할 기반 액세스  
 공유 데이터 집합에 대한 액세스 권한을 부여하려면 사용자가 부모 폴더에서 기존 역할 할당을 상속할 수 있도록 하거나 항목 자체에 대한 새 역할 할당을 만듭니다.  
  
 항목 속성 추가, 삭제 및 편집, 관련 보고서 및 공유 데이터 집합의 공유 데이터 원본 보기를 가능하게 하는 기본 역할 할당은 내용 관리자, 내 보고서 및 게시자입니다. 공유 데이터 집합 정의를 편집하려면 기본 역할 할당 보고서 작성기 또는 내용 관리자를 사용합니다.  
  
 역할 할당은 일반적으로 부모 노드로부터 상속되므로 **보고서 보기** 태스크가 설정된 폴더는 해당 권한을 이 폴더 내의 공유 데이터 집합 및 보고서로 전달합니다.  
  
 공유 데이터 집합 및 이에 대한 쿼리 결과에 대한 추가적인 제어를 제공하려면 공유 데이터 집합 항목에서 항목 수준의 보안을 구성하거나 공유 데이터 집합을 폴더에 저장하고 해당 폴더에서 항목 수준의 보안을 구성합니다.  
  
## <a name="shared-dataset-parameters"></a>공유 데이터 집합 매개 변수  
 공유 데이터 집합 매개 변수를 특정 사용자에 대한 데이터를 제한하기 위해 사용할 수 없습니다. 공유 데이터 집합 매개 변수는 공유 데이터 집합을 처리할 때 포함할 데이터를 지정하는 방법을 제공하기 위한 것입니다. 보고서 서버에서 공유 데이터 집합 매개 변수에 대한 값에 보안을 설정할 수 없습니다.  
  
 공유 데이터 집합 정의에서 매개 변수를 읽기 전용으로 표시하고 기본값을 지정할 수 있습니다. 읽기 전용으로 표시된 매개 변수는 서버에서 재정의할 수 없습니다. 예를 들어 공유 데이터 집합에 대한 캐시 새로 고침 계획에서 읽기 전용 매개 변수에 대해 값을 지정할 수 없습니다. 공유 데이터 집합 매개 변수에 User 전역 컬렉션을 참조하는 식이 포함되거나 다른 사용자 종속성이 있는 경우 해당 공유 데이터 집합에 대한 캐시 새로 고침 계획을 만들 수 없습니다.  
  
## <a name="tasks-access-to-items-and-default-roles"></a>태스크, 항목 액세스 및 기본 역할  
 공유 데이터 집합은 보고서와 동일한 보안 모델을 사용합니다. 사용자에게 특정 동작에 대한 권한을 부여하려면 이러한 권한이 있는 해당 태스크가 포함된 역할을 선택합니다. 다음 표에서는 태스크와 태스크에 포함된 동작을 나열합니다.  
  
|태스크 선택|사용자에게 제공되는 사용 권한|태스크가 포함된 기본 역할|  
|----------------------|---------------------------------|-----------------------------------------|  
|보고서 보기|폴더 계층 구조에 있는 공유 데이터 집합 항목을 봅니다. 이 태스크가 없으면 항목이 사용자에게 표시되지 않으므로 데이터 집합이 사용 가능한지 여부를 알 수 없습니다.|브라우저<br /><br /> 내용 관리자<br /><br /> 보고서 작성기<br /><br /> 내 보고서|  
|보고서 관리|이름, 설명 및 연결 정보를 지정하는 속성을 봅니다. 이 태스크는 폴더 계층 구조에 공유 데이터 집합 항목을 표시하는 데에도 사용됩니다. 이 태스크를 선택하면 "보고서 보기" 태스크를 생략할 수 있습니다.|내용 관리자<br /><br /> 게시자<br /><br /> 내 보고서|  
|보고서 사용|공유 데이터 집합의 정의를 봅니다.|내용 관리자<br /><br /> 보고서 작성기|  
|항목의 보안 설정|공유 데이터 집합에 대한 액세스를 제어하는 역할 할당을 만들고 수정합니다. 이 태스크는 "보고서 보기" 또는 "보고서 관리" 태스크와 함께 사용해야 합니다. 그렇지 않으면 사용자가 항목을 선택할 수 없으므로 효과가 없습니다.|내용 관리자|  
  
 자세한 내용은 참조 [항목 수준의 태스크](tasks-and-permissions-item-level-tasks.md) 및 [미리 정의 된 역할](role-definitions-predefined-roles.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [공유 데이터 집합 관리](../report-data/manage-shared-datasets.md)   
 [보안 폴더](secure-folders.md)   
 [보고서 및 리소스 보안](secure-reports-and-resources.md)   
 [기본 모드 보고서 서버에 대한 사용 권한 부여](granting-permissions-on-a-native-mode-report-server.md)   
 [기본 모드 보고서 서버에 대한 사용 권한 부여](granting-permissions-on-a-native-mode-report-server.md)  
  
  