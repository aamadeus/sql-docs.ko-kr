---
title: MDSModelDeploy를 사용하여 모델 배포 패키지 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a9df35b685d9814636acaa194d5cb30741e9b994
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122763"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>MDSModelDeploy를 사용하여 모델 배포 패키지 만들기
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 MDSModelDeploy 도구를 사용하여 패키지를 만들 수 있습니다. 지정한 명령에 따라 패키지는 다음 중 하나를 포함할 수 있습니다.  
  
-   모델 개체만  
  
-   모델 개체 및 데이터  
  
 모델 개체만 포함하는 패키지를 배포하려면 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 응용 프로그램에서 모델 배포 마법사를 대신 사용할 수 있습니다. 자세한 내용은 [마법사를 사용하여 모델 배포 패키지 만들기](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)를 참조하세요.  
> [!NOTE]  
> MDSModelDeploy 도구의이 버전 (기가바이트) 메모리 보다 더 사용할 수 없습니다. 만들거나 사용 하 여 큰 모델을 배포할 **개체와 데이터 모델** 옵션을 "Out of Memory" 또는 "Stream을 너무 오래 되었습니다." 오류가 발생할 수 있습니다. MDS 데이터를 배포할 준비를 사용 하 여이 문제를 해결 하려면 또는 MDS 2016 또는 MDSModelDeploy 도구의 업데이트 된 버전을 포함 하는 이후 버전으로 업그레이드 합니다.
## <a name="prerequisites"></a>사전 요구 사항  
 이 절차를 수행하려면  
  
1.  MDSModelDeploy 도구를 실행하는 데 필요한 기본 권한은 다음과 같습니다.  
  
    -   MDS 구성 관리자와 동일한 Windows 권한(Windows 관리자)  
  
    -   MDS 데이터베이스에 대한 DBA 권한  
  
2.  MDSModelDeploy 도구를 사용하여 패키지를 만드는 데 필요한 권한은 다음과 같습니다.  
  
    -   데이터 모델에 대한 MDS 모델 관리자 권한  
  
    -   MDS 통합 관리 기능 권한  
  
3.  MDSModelDeploy 도구를 사용하여 모델을 배포하는 데 필요한 권한은 다음과 같습니다.  
  
    -   MDS 탐색기 함수 권한  
  
    -   MDS 통합 관리 기능 권한  
  
    -   MDS 시스템 관리 기능 권한  
  
4.  MDSModelDeploy 도구를 사용하여 모델을 나열하는 데 필요한 권한은 다음과 같습니다.  
  
    -   MDS 탐색기 함수 권한  
  
    -   목록의 모델을 보기 위한 데이터 모델에 대한 MDS 모델 관리자 권한  
  
 패키지를 만들 모델이 있어야 합니다. 자세한 내용은 [모델 만들기&#40;Master Data Services&#41;](create-a-model-master-data-services.md)를 참조하세요.  
  
 자세한 내용은 [관리자&#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조하세요.  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>MDSModelDeploy를 사용하여 모델 배포 패키지를 만들려면  
  
1.  명령 프롬프트를 엽니다.  
  
2.  MDSModelDeploy.exe의 위치로 이동합니다.  
  
    -   파일은 MDS를 기본 위치에 설치한 경우 *드라이브*: \Program Files\Microsoft SQL Server\120\Master Data services\configuration에 있습니다.  
  
    -   MDS를 기본 위치에 설치하지 않은 경우 로컬 컴퓨터에서 MDSModelDeploy.exe를 검색하십시오.  
  
3.  (선택 사항) 보기 옵션 및 도움말입니다.  
  
    -   모든 사용 가능한 옵션을 표시하려면 `MDSModelDeploy` 를 입력하고 Enter 키를 누릅니다.  
  
    -   옵션에 대한 도움말을 표시하려면 *과 같이 입력합니다. 여기서* OptionName `MDSModelDeploy help OptionName`은 옵션의 이름입니다.  
  
4.  (선택 사항) 여러 웹 응용 프로그램이 있는 경우 이 명령을 입력하고 Enter 키를 눌러 배포할 서비스의 이름을 결정합니다.  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     값의 목록(예: `MDS1, Default Web Site, MDS`)이 반환됩니다. 이 목록의 첫 번째 값(이 경우 `MDS1`)은 모델을 배포하는 데 필요합니다.  
  
5.  모델 개체와 데이터를 포함하는 패키지를 만들려면 다음과 같이 입력하십시오. 여기서 *ModelName*, *VersionName*, *ServiceName*및 *PackageName* 은 각각 모델, 버전, 서비스 및 .pkg 출력 파일의 이름입니다.  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     데이터를 포함하지 않으려면 `-version` 및 `-includedata` 스위치를 사용하지 마십시오.  
  
6.  Enter 키를 누릅니다. 패키지가 성공적으로 만들어지면 "MDSModelDeploy 작업이 성공적으로 완료되었습니다."라는 메시지가 표시됩니다.  
  
## <a name="next-steps"></a>다음 단계  
  
-   [MDSModelDeploy를 사용하여 모델 배포 패키지 배포](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a>관련 항목  
 [모델 배포 옵션 &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md)   
 [모델 배포 &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  
