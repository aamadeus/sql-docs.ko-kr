---
title: Azure Data Lake Store 원본 | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
caps.latest.revision: 6
author: yualan
ms.author: yual
manager: jhubbard
ms.openlocfilehash: e7bd327dc2657123daf94390785bda11a17e2040
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080906"
---
# <a name="azure-data-lake-store-source"></a>Azure Data Lake Store 원본
  **Azure Data Lake Store 원본** 구성 요소를 사용하면 SSIS 패키지가 Azure Data Lake Store에서 데이터를 읽을 수 있습니다. 지원되는 파일 형식은 Text 및 Avro입니다.
  
## <a name="configure-the-azure-data-lake-store-source"></a>Azure Data Lake Store 원본 구성 
  
1.  Azure Data Lake Store 원본용 편집기를 표시하려면 데이터 흐름 디자이너에서 **Azure Data Lake Store 원본** 을 끌어서 놓고 두 번 클릭하여 편집기를 엽니다.  
  
2.  **Azure Data Lake Store 연결 관리자** 필드에서는 기존 Azure Data Lake Store 연결 관리자를 지정하거나 Azure Data Lake Store 서비스를 참조하는 연결 관리자를 새로 만듭니다.  
  
    1.  **파일 경로** 필드에서는 Azure Data Lake Store에 있는 원본 파일의 파일 경로를 지정합니다.   
  
    2.  **파일 형식** 필드에서는 원본 파일의 파일 형식을 지정합니다.  
  
        파일 형식이 Text이면 **열 구분 기호 문자** 값을 지정해야 합니다. 파일의 첫 행에 열 이름을 포함하려는 경우에는 **첫 번째 데이터 행의 열 이름** 도 선택합니다.  
  
3.  연결 정보를 지정한 다음 **열** 페이지로 전환하여 SSI 데이터 흐름에 대해 원본 열을 대상 열에 매핑합니다.  