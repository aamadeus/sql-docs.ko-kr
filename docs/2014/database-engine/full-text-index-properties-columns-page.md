---
title: 전체 텍스트 인덱스 속성 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 67b7e72e0c4b248e8951667561eaf7548bfba1b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141643"
---
# <a name="full-text-index-properties-columns-page"></a>전체 텍스트 인덱스 속성(열 페이지)
  **전체 텍스트 인덱스의 속성 보기 또는 변경 하려면**  
  
-   [전체 텍스트 인덱스 관리](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>UIElement 목록  
 **고유 인덱스**  
 드롭다운 목록에서 인덱스를 선택합니다. 인덱스는 Null 값을 허용하지 않는 고유한 단일 키 열이어야 합니다.  
  
 **전체 텍스트 인덱싱할 수 있는 적합 한 열 선택**  
 표에는 이 전체 텍스트 인덱스에 사용할 수 있는 테이블 열이 표시됩니다. 현재 전체 텍스트 인덱싱된 열은 선택되어 있습니다. 경우에 따라 전체 텍스트 인덱싱할 추가 열을 선택할 수도 있습니다.  
  
> [!IMPORTANT]  
>  확인을 클릭하기 전에 최소한 하나의 열이 선택되어 있는지 확인하십시오.  
  
|||  
|-|-|  
|**사용 가능한 열**|열 이름입니다.|  
|**단어 분리기 용 언어**|단어 분리기와 형태소 분석기에서 모든 전체 텍스트 인덱싱된 데이터에 대해 언어 분석을 수행하는 데 사용되는 언어입니다.<br /><br /> 자세한 내용은 참조 하세요. [구성 및 관리 단어 분리기 및 형태소 분석기 검색용](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) 하 고 [전체 텍스트 인덱스 생성 시 언어 선택](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)합니다.|  
|**형식**|선택한 열의 문서 유형을 보관하는 테이블 열의 이름입니다. 이 속성은 읽기 전용입니다.|  
|**통계 의미 체계**|선택한 열에 대해 의미 체계 인덱싱을 사용하도록 설정할지 여부를 선택합니다. 자세한 내용은 [의미 체계 검색&#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)을 참조하세요.<br /><br /> **통계 의미 체계** 를 선택하기 전에 **언어**를 선택했으며 선택한 언어에 연결된 의미 체계 언어 모델이 없으면 **통계 의미 체계** 확인란은 사용할 수 없습니다. **언어** 를 선택하기 전에 **통계 의미 체계**를 선택한 경우 드롭다운 콤보 상자에서 사용할 수 있는 언어가 의미 체계 언어 모델에서 지원하는 언어로 제한됩니다.|  
  
## <a name="see-also"></a>관련 항목  
 [전체 텍스트 인덱스 채우기](../relational-databases/search/populate-full-text-indexes.md)  
  
  
