---
title: "2 단계: 손상된 된 파일 만들기 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7760a481839ec7bd33aeeefd4b066f3d7750020d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-4-2---creating-a-corrupted-file"></a>단원 4-2-손상된 된 파일 만들기
변환 오류의 구성 및 처리를 보여 주기 위해 처리 시 구성 요소의 실패를 야기하는 예제 플랫 파일을 만들어야 합니다.  
  
이 태스크에서는 기존 예제 플랫 파일의 복사본을 만듭니다. 그런 다음 메모장에서 해당 파일을 열고 변환 조회를 수행하는 동안 일치 항목을 생성하지 못하도록 **CurrencyID** 열을 편집합니다. 이 새 파일을 처리하면 조회 실패로 Currency Key Lookup 변환이 실패하며 따라서 패키지의 나머지 부분도 실패합니다. 손상된 예제 파일을 만든 다음에는 패키지를 실행하여 패키지 오류를 봅니다.  
  
### <a name="to-create-a-corrupted-sample-flat-file"></a>손상된 예제 플랫 파일을 만들려면  
  
1.  메모장이나 기타 텍스트 편집기에서 Currency_VEB.txt 파일을 엽니다.  
  
    예제 데이터는 SSIS 단원 패키지에 포함되어 있습니다. 예제 데이터 및 단원 패키지를 다운로드하려면 다음을 수행합니다.  
  
    1.  [Integration Services 제품 예제](http://go.microsoft.com/fwlink/?LinkID=267527)로 이동합니다.  
  
    2.  **DOWNLOADS** 탭을 클릭합니다.  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 파일을 클릭합니다.  
  
2.  텍스트 편집기의 찾기 및 바꾸기 기능을 사용하여 모든 **VEB** 인스턴스를 찾은 다음 모두 **BAD**로 바꿉니다.  
  
3.  다른 샘플 데이터 파일과 동일한 폴더에서 수정된 파일을 **Currency_BAD.txt**로 저장합니다.  
  
    > [!IMPORTANT]  
    > **Currency_BAD.txt** 가 다른 샘플 데이터 파일과 동일한 폴더에 저장되었는지 확인합니다.  
  
4.  텍스트 편집기를 닫습니다.  
  
### <a name="to-verify-that-an-error-will-occur-during-run-time"></a>런타임 도중 오류가 발생하는지 확인하려면  
  
1.  **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.  
  
    세 번째 데이터 흐름 반복에서 Lookup Currency Key 변환은 Currency_BAD.txt 파일을 처리하려고 하며 여기서 변환이 실패합니다. 변환 실패로 인해 전체 패키지가 실패하게 됩니다.  
  
2.  **디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.  
  
3.  디자인 화면에서 **실행 결과** 탭을 클릭합니다.  
  
4.  로그를 찾아보고 다음의 처리되지 않은 오류가 발생했는지 확인합니다.  
  
    `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    > 27은 구성 요소의 ID입니다. 이 값은 데이터 흐름을 작성할 때 할당되며 패키지 값과 다를 수 있습니다.  
  
## <a name="next-steps"></a>다음 단계  
[3단계: 오류 흐름 리디렉션 추가](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
  
  
