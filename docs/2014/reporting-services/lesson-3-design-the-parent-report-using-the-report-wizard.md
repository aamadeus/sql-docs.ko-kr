---
title: '3단원: 보고서 마법사를 사용하여 부모 보고서 디자인 | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b92aba7afebc203ba8d32386eaf0dd154d97c208
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082629"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>3단원: 보고서 마법사를 사용하여 부모 보고서 디자인
  부모 보고서에 대한 데이터 테이블 및 데이터 연결을 만든 후에는 보고서 디자이너의 보고서 마법사를 사용하여 부모 보고서를 디자인합니다. 보고서 디자이너에 대한 자세한 내용은 [보고서 디자이너로 보고서 디자인&#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)을 참조하세요.  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>보고서 마법사를 사용하여 부모 보고서를 디자인하려면  
  
1.  **솔루션 탐색기**에서 최상위 웹 사이트가 선택되어 있는지 확인합니다.  
  
2.  웹 사이트를 마우스 오른쪽 단추로 클릭하고 **새 항목 추가**를 선택합니다.  
  
3.  에 **새 항목 추가** 대화 상자에서 **보고서 마법사**보고서 파일에 대 한 이름을 입력 한 다음 클릭 **추가**합니다.  
  
     그러면 보고서 마법사가 시작됩니다.  
  
4.  에 **데이터 집합 속성** 페이지는 **데이터 소스** 상자는 **DataSet1** 에서 만든 [2 단원: 데이터 연결 및 데이터 테이블에 대 한 정의 부모 보고서](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)합니다.  
    **사용 가능한 데이터 집합** 상자가 위에서 만든 **DataTable** 로 자동 업데이트됩니다.  
  
5.  **다음**을 클릭합니다.  
  
6.  **필드 정렬** 페이지에서 다음을 수행합니다.  
  
    1.  **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**및 **ReorderLevel** 을 **사용 가능한 필드** 에서 **값** 상자로 끌어옵니다.  
  
    2.  옆에 있는 화살표를 클릭 **sum (productid)**, **sum (safetystocklevel)**, **sum (reorderlevel)** 선택을 취소 하 고는 **합계** 선택 합니다.  
  
7.  **다음** 을 두 번 클릭한 다음 **마침** 을 클릭하여 **보고서 마법사**를 닫습니다.  
  
     이제 .rdlc 파일을 만드는 작업을 마쳤습니다. 보고서 디자이너에서 파일이 열립니다. 디자인한 테이블릭스가 이제 디자인 화면에 표시됩니다.  
  
8.  .rdlc 파일을 저장합니다.  
  
## <a name="next-task"></a>다음 태스크  
 보고서 마법사를 사용하여 성공적으로 부모 보고서를 디자인했습니다. 이제 자식 보고서에 대한 데이터 테이블 및 데이터 연결을 만듭니다.  
  
  