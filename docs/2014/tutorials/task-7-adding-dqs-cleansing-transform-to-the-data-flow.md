---
title: '태스크 7: 데이터 흐름에 DQS 정리 변환 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 10b0fb12ace5a113bbde03cecf803a37b49b1974
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36186437"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>태스크 7: 데이터 흐름에 DQS 정리 변환 추가
  이 작업에서는 데이터 흐름에 DQS 정리 변환을 추가하여 DQS를 사용해서 입력 공급자 데이터를 정리합니다. 참조 **[DQS 정리 변환](http://msdn.microsoft.com/library/ee677619.aspx)** 변환에 대 한 자세한 내용은 합니다.  
  
1.  마우스 오른쪽 단추로 클릭 **DQS 정리** 에 **데이터 흐름** 탭을 클릭 **이름 바꾸기**합니다. 형식 **Cleanse Supplier Data**, 누릅니다 **ENTER**합니다.  
  
2.  선택 **Excel 파일에서 공급자 데이터 읽기**; 파란색 커넥터를 끌어 **Cleanse Supplier Data**합니다. 구성 요소가 이제 연결됩니다.  
  
     ![공급자 데이터 읽기-> Cleanse Supplier Data](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "공급자 데이터 읽기-> 공급자 데이터 정리")  
  
3.  두 번 클릭 **Cleanse Supplier Data**합니다.  
  
4.  에 **DQS 정리 변환 편집기**, 클릭 **새로** 옆에 **데이터 품질 연결 관리자 드롭 다운 목록**합니다.  
  
5.  에 **DQS 정리 연결 관리자** 대화 상자에서 **(local)** 또는 **기간** (.)를 로컬 서버에 연결 합니다. 이 단원에서는 DQS가 로컬 서버에 설치되어 있다고 가정합니다.  
  
6.  클릭 **연결 테스트** DQS 서버에 대 한 연결을 테스트 합니다.  
  
7.  **확인** 을 클릭하여 대화 상자를 닫습니다.  
  
8.  선택 **Suppliers** 에 대 한는 **데이터 품질 기술 자료**합니다.  
  
     ![DQS 정리 변환 편집기-공급자 KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS 정리 변환 편집기-공급자 KB")  
  
9. 전환 하는 **매핑** 맨 위 탭 합니다.  
  
10. **사용 가능한 입력 열**선택, **Supplier Name**, **ContactEmailAddress**, **Address Line**, **도시**, **상태**, **국가**, 및 **우편 번호** 확인란을 선택 하 여 합니다.  
  
     ![DQS 정리 변환 편집기-매핑](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS 정리 변환 편집기-매핑")  
  
11. 아래쪽 창에서 드롭 다운 목록에서 사용 하 여 이러한 열을 매핑할는 **도메인** 열:  
  
    |Column|도메인|  
    |------------|------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Address Line|Address Line|  
    |City|City|  
    |State|State|  
    |Country|Country|  
    |Zip Code|Zip|  
  
12. 클릭 **확인** 를 닫으려면는 **DQS 정리 변환 편집기** 대화 상자.  
  
## <a name="next-step"></a>다음 단계  
 [태스크 8: 조건부 분할 변환을 추가하여 정리 출력 분할](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  