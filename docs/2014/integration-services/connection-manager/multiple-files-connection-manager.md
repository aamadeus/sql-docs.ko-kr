---
title: 다중 파일 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- Multiple Files connection manager
- connection managers [Integration Services], Multiple Files
- connections [Integration Services], files
- multiple file connections
ms.assetid: 10bdc56e-c5cd-4ddb-b2f7-375fe57fe8b2
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 22fe47c60aadc0f5014b7aef2171399f8ea0d22a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36092459"
---
# <a name="multiple-files-connection-manager"></a>다중 파일 연결 관리자
  다중 파일 연결 관리자를 사용하면 패키지에서 기존 파일 및 폴더를 참조하거나 런타임에 파일 및 폴더를 만들 수 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 기본 제공 태스크 및 데이터 흐름 구성 요소는 다중 파일 연결 관리자를 사용하지 않습니다. 그러나 스크립트 태스크와 스크립트 구성 요소에서 이 연결 관리자를 사용할 수 있습니다. 스크립트 태스크에서 연결 관리자를 사용하는 방법은 [스크립트 태스크에서 데이터 원본에 연결](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)을 참조하십시오. 스크립트 구성 요소에서 연결 관리자를 사용 하는 방법에 대 한 내용은 [스크립트 구성 요소에서 데이터 원본에 연결]을 참조 (... / extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md 합니다.  
  
## <a name="usage-types-of-the-multiple-files-connection-manager"></a>다중 파일 연결 관리자의 사용 유형  
 다중 파일 연결 관리자의 `FileUsageType` 속성은 연결 사용 방법을 지정합니다. 다중 파일 연결 관리자에서는 파일이나 폴더를 만들고 기존 파일 또는 기존 폴더를 사용할 수 있습니다.  
  
 다음 표에서 값을 나열 `FileUsageType`합니다.  
  
|값|Description|  
|-----------|-----------------|  
|**0**|다중 파일 연결 관리자에서 기존 파일을 사용합니다.|  
|**1**|다중 파일 연결 관리자에서 파일을 만듭니다.|  
|**2**|다중 파일 연결 관리자에서 기존 폴더를 사용합니다.|  
|**3**|다중 파일 연결 관리자에서 폴더를 만듭니다.|  
  
## <a name="configuration-of-the-multiple-files-connection-manager"></a>다중 파일 연결 관리자 구성  
 패키지에 다중 파일 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 다중 파일 연결로 확인되는 연결 관리자를 만들고, 다중 파일 연결 속성을 설정하고, 다중 파일 연결을 패키지의 `Connections` 컬렉션에 추가합니다.  
  
 `ConnectionManagerType` 연결 관리자의 속성이로 설정 되어 `MULTIFILE`합니다.  
  
 다음과 같은 방법으로 다중 파일 연결 관리자를 구성할 수 있습니다.  
  
-   파일 및 폴더의 사용 유형을 지정합니다.  
  
-   파일 및 폴더를 지정합니다.  
  
-   다중 파일 또는 폴더를 사용하는 경우 파일 및 폴더가 액세스되는 순서를 지정합니다.  
  
 다중 파일 연결 관리자에서 다중 파일 및 폴더를 참조하는 경우 파일 및 폴더의 경로는 세로줄 문자(|)로 구분됩니다. 연결 관리자의 `ConnectionString` 속성은 다음 형식을 갖습니다.  
  
 \<*경로*>|\<*경로*>  
  
 또한 와일드카드 문자를 사용하여 다중 파일이나 폴더를 지정할 수 있습니다. 예를 들어 모든 텍스트 파일에는 C 드라이브의 값 참조는 `ConnectionString` 를 c: 속성을 설정할 수 있습니다\\*.txt 합니다.  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [파일 연결 관리자 추가 대화 상자 UI 참조](add-file-connection-manager-dialog-box-ui-reference.md)를 참조하세요.  
  
 연결 관리자를 프로그래밍 방식으로 구성 하는 방법에 대 한 정보를 참조 하십시오. <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)합니다.  
  
  