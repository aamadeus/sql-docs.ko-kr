---
title: Azure Blob 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.afpblobdest.f1
- sql11.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7ba7b3a14fcd6942865033772bf065c8e3215285
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36172003"
---
# <a name="azure-blob-destination"></a>Azure Blob 대상
  SSIS 패키지는 **Azure Blob 대상** 구성 요소를 통해 Azure Blob에 데이터를 쓸 수 있습니다. 지원되는 파일 형식은 CSV 및 AVRO입니다. 놓은 다음 **Azure Blob 대상을** 에 데이터 흐름 디자이너와 편집기를 표시 하려면 두 번 클릭).  
  
1.  **Azure 저장소 연결 관리자** 필드에서는 기존 Azure 저장소 연결 관리자를 지정하거나 Azure 저장소 계정을 참조하는 저장소 연결 관리자를 새로 만듭니다.  
  
2.  **Blob 컨테이너 이름** 필드에서는 원본 파일을 포함하는 Blob 컨테이너의 이름을 지정합니다.  
  
3.  **Blob 이름** 필드에서는 Blob의 경로를 지정합니다.  
  
4.  **Blob 파일 형식** 필드에서는 사용할 Blob 형식을 지정합니다.  
  
5.  파일 형식이 CSV이면 **열 구분 기호 문자** 값을 지정해야 합니다. 파일의 첫 행에 열 이름을 포함하려는 경우에는 **첫 번째 데이터 행의 열 이름** 도 선택합니다.  
  
6.  연결 정보를 지정한 다음 **열** 페이지로 전환하여 SSI 데이터 흐름에 대해 원본 열을 대상 열에 매핑합니다.  
  
  