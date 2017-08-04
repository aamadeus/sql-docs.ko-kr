---
title: "전역 설정 (로깅) (OracleToSQL) | Microsoft Docs"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12dbcd77-2b90-4fa1-9cf9-239231ea5773
caps.latest.revision: 4
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: df359be112e86522d35e27d8cf49a4515d8745d6
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="global-settings-logging-oracletosql"></a>전역 설정 (로깅) (OracleToSQL)
사용 하 여 **전역 설정** SSMA에 대 한 로깅 설정을 지정 하려면 대화 상자. 일반적으로 제품 지원 팀과 작업 하는 경우에 이러한 설정을 변경할 것 있습니다.  
  
이 대화 상자에 액세스 하려면는 **도구** 메뉴 선택 **전역 설정** 클릭 하 고는 **로깅** 왼쪽 창의 맨 아래에 단추입니다.  
  
## <a name="options"></a>옵션  
**메시지 수준**  
다음 옵션에서 사용할 수 있는 **메시지 수준**:  
  
|옵션|Description|  
|----------|---------------|  
|**[모든 범주]**|다음 옵션을 모두에 대 한 로깅 수준을 설정 하는 데 사용 합니다.|  
|**수집기**|소스 스키마에 대 한 메타 데이터를 수집 하 고 프로젝트에 저장 합니다.|  
|**변환기**|해당 테이블 및 저장된 프로시저와 같은 원본 데이터베이스 개체의 구조 변환 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 구조입니다.|  
|**데이터 migrator**|원본 데이터베이스에서 데이터를 마이그레이션하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]합니다.|  
|**포맷터**|에 대 한 스크립트를 생성 하는 변환기의 하위 구성 요소는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 스키마입니다.|  
|**그래픽 사용자 인터페이스**|SSMA 도구를 사용할 때 표시 되는 메시지입니다.|  
|**링커**|SQL 식별자를 확인 하 고 다른 구성 요소에 대 한 정보를 제공 합니다.|  
|**기타**|다른 범주에 없는 모든 메시지입니다.|  
|**파서**|소스 스키마를 구문 분석합니다.|  
|**동기화**|로드 원본 데이터베이스 개체에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]합니다.|  
|**TreeConverter**|개체에 소스 메타 데이터에서 변환 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 메타 데이터입니다.|  
|**테스터**|SSMA 테스터를 사용 하는 경우 나타나는 메시지입니다.|  
  
각 옵션에 대 한 **메시지 수준**, SSMA에 대해 다음 로깅 수준 중 하나를 구성 합니다.  
  
|||  
|-|-|  
|**심각한 오류**|심각한 오류 메시지에만 로그를 기록 합니다.|  
|**오류**|로그에 오류 및 심각한 오류 메시지를 작성 합니다.|  
|**경고**|로그에 경고, 오류 및 심각한 오류 메시지를 작성 합니다.|  
|**정보**|로그에 정보, 경고, 오류 및 심각한 오류 메시지를 작성 합니다.|  
|**디버그**|디버깅 로그에 메시지를 포함 하 여 모든 메시지를 작성 합니다.|  
  
**로그 파일 경로**  
파일 경로 및 SSMA 로그 파일의 이름입니다. 다른 이름을 지정 하려면 현재 경로 클릭 하 고 클릭 한 다음 찾아보기 (**...** ) 단추입니다.  
  
**로그 파일 크기**  
Kb에서 로그 파일의 최대 크기입니다. 최소 크기는 10KB입니다. 기본값은 10240KB 합니다.  
  
**로그 파일의 총 수**  
한 로그가 꽉 차면 SSMA 로그 파일 바꾸고 새 시작 됩니다. 이 설정을 사용 하 여 보관할 로그 파일의 최대 수를 지정 합니다. 최소값은 2입니다.  
  
