---
title: '2단계: Foreach 루프 컨테이너 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 492691c3fd6c8cd9206b591aa2302bc62a658daa
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527127"
---
# <a name="lesson-2-2---adding-and-configuring-the-foreach-loop-container"></a>2-2단원 - Foreach 루프 컨테이너 추가 및 구성
이 태스크에서는 플랫 파일 폴더를 통해 루핑하고 1단원에서 사용한 것과 같은 데이터 흐름 변환을 각 플랫 파일에 적용합니다. 제어 흐름에 Foreach 루프 컨테이너를 추가하고 구성하여 이 작업을 수행합니다.  
  
추가한 Foreach 루프 컨테이너는 폴더의 각 플랫 파일에 연결할 수 있어야 합니다. 폴더의 파일이 모두 같은 형식이므로 Foreach 루프 컨테이너가 같은 플랫 파일 연결 관리자를 사용하여 이러한 파일에 각각 연결할 수 있습니다. 컨테이너가 사용할 플랫 파일 연결 관리자는 1단원에서 만든 것과 같은 플랫 파일 연결 관리자입니다.  
  
현재 1단원에서 만든 플랫 파일 연결 관리자는 특정 플랫 파일 하나에만 연결합니다. 폴더의 각 플랫 파일에 반복하여 연결하려면 다음과 같이 Foreach 루프 컨테이너와 플랫 파일 연결 관리자를 둘 다 구성해야 합니다.  
  
-   **Foreach 루프 컨테이너:** 컨테이너의 열거된 값을 사용자 정의 패키지 변수에 매핑합니다. 그러면 컨테이너가 이 사용자 정의 변수를 사용하여 플랫 파일 연결 관리자의 **ConnectionString** 속성을 수정하고 폴더의 각 플랫 파일에 반복하여 연결합니다.  
  
-   **플랫 파일 연결 관리자:** 사용자 정의 변수를 사용해 연결 관리자의 **ConnectionString** 속성을 채워 1단원에서 만든 연결 관리자를 수정합니다.  
  
이 태스크의 절차에서는 Foreach 루프 컨테이너를 만들고 수정하여 사용자 정의 패키지 변수를 사용하고 루프에 데이터 흐름 작업을 추가하는 방법과 플랫 파일 연결 관리자를 수정하여 다음 태스크에서 사용자 정의 변수를 사용하는 방법에 대해 설명합니다.  
  
패키지를 수정한 후 패키지가 실행되면 Foreach 루프 컨테이너가 Sample Data 폴더의 파일 집합 전체에서 반복됩니다. Foreach 루프 컨테이너는 조건에 맞는 파일을 발견할 때마다 사용자 정의 변수를 파일 이름으로 채우고 Sample Currency Data 플랫 파일 연결 관리자의 **ConnectionString** 속성에 사용자 정의 변수를 매핑한 다음 해당 파일에 대해 데이터 흐름을 실행합니다. 따라서 Foreach 루프가 반복될 때마다 데이터 흐름 태스크에서 다른 플랫 파일을 사용합니다.  
  
> [!NOTE]  
> [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서는 흐름 제어를 데이터 흐름과 분리하므로 제어 흐름에 추가한 루핑에서는 데이터 흐름을 수정할 필요가 없습니다. 따라서 1단원에서 만든 데이터 흐름을 변경하지 않아도 됩니다.  
  
### <a name="to-add-a-foreach-loop-container"></a>Foreach 루프 컨테이너를 추가하려면  
  
1.  **SQL Server Data Tools**에서 **제어 흐름** 탭을 클릭합니다.  
  
2.  **SSIS 도구 상자**에서 **컨테이너**를 확장한 다음 **Foreach 루프 컨테이너** 를 **제어 흐름** 탭의 디자인 화면으로 끌어옵니다.  
  
3.  새로 추가한 **Foreach 루프 컨테이너** 를 마우스 오른쪽 단추로 클릭하고 **편집**을 선택합니다.  
  
4.  **Foreach 루프 편집기** 대화 상자의 **일반** 페이지에서 **이름**에 **Foreach File in Folder**를 입력합니다. **확인**을 클릭합니다.  
  
5.  Foreach 루프 컨테이너를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭한 다음 속성 창에서 **LocaleID** 속성이 **영어(미국)** 로 설정되었는지 확인합니다.  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a>Foreach 루프 컨테이너의 열거자를 구성하려면  
  
1.  Foreach File in Folder를 두 번 클릭하여 **Foreach 루프 편집기**를 다시 엽니다.  
  
2.  **컬렉션**을 클릭합니다.  
  
3.  **컬렉션** 페이지에서 **Foreach File 열거자**를 선택합니다.  
  
4.  **열거자 구성** 그룹에서 **찾아보기**를 클릭합니다.  
  
5.  **폴더 찾아보기** 대화 상자에서 Currency_*.txt 파일이 들어 있는 컴퓨터의 폴더를 찾습니다.  
  
    이 예제 데이터는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 단원 패키지에 포함되어 있습니다. 예제 데이터 및 단원 패키지를 다운로드하려면 다음을 수행합니다.  
  
    1.  [Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=275027)로 이동합니다. 
  
    2.  **DOWNLOADS** 탭을 클릭합니다.  
  
    3.  [SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip](https://msftisprodsamples.codeplex.com/downloads/get/596031) 파일에 대한 링크를 클릭합니다.  
  
6.  **파일** 상자에 **Currency_\*.txt**를 입력합니다.  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a>사용자 정의 변수에 열거자를 매핑하려면  
  
1.  **변수 매핑**을 클릭합니다.  
  
2.  **변수 매핑** 페이지의 **변수** 열에서 빈 셀을 클릭하고 **\<새 변수...>** 를 선택합니다.  
  
3.  **변수 추가** 대화 상자에서 **이름**에 **varFileName**을 입력합니다.  
  
    > [!IMPORTANT]  
    > 변수 이름은 대/소문자를 구분합니다.  
  
4.  **확인**을 클릭합니다.  
  
5.  **확인** 을 다시 클릭하여 **Foreach 루프 편집기** 대화 상자를 종료합니다.  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a>루프에 데이터 흐름 태스크를 추가하려면  
  
-   **Foreach File in Folder** 로 이름이 바뀐 Foreach 루프 컨테이너로 **Extract Sample Currency Data**데이터 흐름 태스크를 끌어옵니다.  
  
## <a name="next-lesson-task"></a>다음 단원 태스크  
[3단계: 플랫 파일 연결 관리자 수정](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a>참고 항목  
[Foreach 루프 컨테이너 구성](https://msdn.microsoft.com/library/519c6f96-5e1f-47d2-b96a-d49946948c25)  
[패키지에서 변수 사용](https://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  
  
