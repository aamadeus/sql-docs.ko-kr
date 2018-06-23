---
title: 데이터 집합 속성 대화 상자, 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10130"
- sql12.rtp.rptdesigner.datasetproperties.options.f1
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
caps.latest.revision: 39
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: d0f83c86076cc968d1b8896f3c857b9925fcbb81
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080163"
---
# <a name="dataset-properties-dialog-box-options"></a>데이터 집합 속성 대화 상자, 옵션
  선택 **옵션** 에 **DatasetProperties** 데이터 정렬 옵션 및 쿼리에 대 한 부분합 같은 데이터 옵션을 변경 하려면 대화 상자. 자세한 내용은 [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md)을(를) 참조하세요.  
  
## <a name="options"></a>변수  
 **데이터 정렬**  
 데이터 정렬에 사용할 데이터 정렬 시퀀스를 결정하는 로캘을 선택합니다. **Default** 로 설정하면 보고서가 실행될 때 보고서 서버가 데이터 공급자로부터 값을 가져와야 합니다. 값을 가져올 수 없는 경우 기본값이 컴퓨터의 로캘 설정에서 파생됩니다.  
  
 **대/소문자 구분**  
 대/소문자 구분을 결정하는 값을 선택합니다. 이 옵션은 데이터가 대/소문자를 구분하는지 여부를 나타냅니다. **대/소문자 구분** 은 **True**, **False**또는 **Auto**로 설정할 수 있습니다. 기본값인 **Auto**로 설정하면 보고서가 실행될 때 보고서 서버가 데이터 공급자로부터 값을 가져와야 합니다. 데이터 공급자가 대/소문자 구분 형식을 지원하지 않는 경우에는 이 값이 **False**인 것처럼 보고서가 실행됩니다. 지원되는 값을 알고 있는 경우 **True**를 선택합니다.  
  
 **악센트 구분**  
 악센트 구분을 결정하는 값을 선택합니다. **악센트 구분** 은 데이터가 악센트를 구분하는지 여부를 나타내며 **True**, **False**또는 **Auto**로 설정할 수 있습니다. 기본값인 **Auto**로 설정하면 보고서가 실행될 때 보고서 서버가 데이터 공급자로부터 값을 가져와야 합니다. 데이터 공급자가 악센트 구분 형식을 지원하지 않는 경우에는 이 값이 **False**인 것처럼 보고서가 실행됩니다. 지원되는 값을 알고 있는 경우 **True**를 선택합니다.  
  
 **일본어 가나 구분**  
 일본어 가나 구분을 결정하는 값을 선택합니다. 이 옵션은 데이터가 일본어 가나를 구분하는지 여부를 나타내며 **True**, **False**또는 **Auto**로 설정할 수 있습니다. 기본값인 **Auto**로 설정하면 보고서가 실행될 때 보고서 서버가 데이터 공급자로부터 값을 가져와야 합니다. 데이터 공급자가 일본어 가나 구분 형식을 지원하지 않는 경우에는 이 값이 **False**인 것처럼 보고서가 실행됩니다. 지원되는 값을 알고 있는 경우 **True**를 선택합니다.  
  
 **전자/반자 구분**  
 전자/반자 구분을 결정하는 값을 선택합니다. 이 옵션은 데이터가 전자/반자를 구분하는지 여부를 나타내며 **True**, **False**또는 **Auto**로 설정할 수 있습니다. 기본값인 **Auto**로 설정하면 보고서가 실행될 때 보고서 서버가 데이터 공급자로부터 값을 가져와야 합니다. 데이터 공급자가 전자/반자 구분 형식을 지원하지 않는 경우에는 이 값이 **False**인 것처럼 보고서가 실행됩니다. 지원되는 값을 알고 있는 경우 **True**를 선택합니다.  
  
 **부분합을 정보 행으로 해석**  
 부분합 행을 집계 행이 아니라 정보 행으로 해석할지 여부를 나타내는 값을 선택합니다. 기본 값, **자동**, 보고서를 사용 하지 않는 경우 부분합 행 정보 행으로 처리 해야 함을 나타냅니다는 `Aggregate`() 함수가 데이터 집합 필드에에서 액세스할 수 있습니다. 부분합 행을 집계 행으로 해석하려면 **False**를 선택합니다. 부분합 행 정보 행으로 해석 되도록 하 고 사용 하지 않도록 알고 있는 경우는 `Aggregate`() 함수를 선택 **True**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [보고서 또는 입력란에 대 한 로캘을 설정 &#40;Reporting Services&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md)   
 [보고서에 데이터 추가 &#40;보고서 작성기 및 SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Windows 데이터 정렬 이름&#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [SQL Server 데이터 정렬 이름&#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [집계 함수 &#40;보고서 작성기 및 SSRS&#41;](report-design/report-builder-functions-aggregate-function.md)  
  
  