---
title: "시간, 날짜 및 간격 함수 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], time functions
- functions [ODBC], date functions
- interval functions [ODBC]
- functions [ODBC], interval functions
- time functions [ODBC]
- date functions [ODBC]
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 03980d8a45fb27f173c7caf8facef319050d0778
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="time-date-and-interval-functions"></a>시간, 날짜 및 간격 함수
다음 표에서 ODBC 스칼라 함수 집합에 포함 된 날짜 및 시간 함수를 나열 합니다. 응용 프로그램에서 호출 하 여 드라이버를 통해 지원 되는 날짜 및 시간 함수를 확인할 수 **SQLGetInfo** 와 *정보 유형* SQL_TIMEDATE_FUNCTIONS입니다.  
  
 로 표시 된 인수 *timestamp_exp* 다른 스칼라 함수의 결과 열의 이름이 될 수 있습니다 또는 *ODBC 시간 이스케이프*, *ODBC 날짜 이스케이프*, 또는 *ODBC 타임 스탬프 이스케이프*, 여기서 SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE, 또는 SQL_TYPE_TIMESTAMP로 기본 데이터 형식을 나타낼 수 있습니다.  
  
 로 표시 된 인수 *date_exp* 다른 스칼라 함수의 결과 열의 이름이 될 수 있습니다 또는 *ODBC 날짜 이스케이프* 또는 *ODBC 타임 스탬프 이스케이프*, 여기서는 내부 데이터 형식은 SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE, 또는 SQL_TYPE_TIMESTAMP로 나타낼 수 있습니다.  
  
 로 표시 된 인수 *time_exp* 다른 스칼라 함수의 결과 열의 이름이 될 수 있습니다 또는 *ODBC 시간 이스케이프* 또는 *ODBC 타임 스탬프 이스케이프*, 여기서는 내부 데이터 형식은 SQL_CHAR, SQL_VARCHAR SQL_TYPE_TIME 및 SQL_TYPE_TIMESTAMP로 나타낼 수 있습니다.  
  
 CURRENT_DATE, CURRENT_TIME, 및 CURRENT_TIMESTAMP timedate 스칼라 함수 s Q l-92에 맞게 ODBC 3.0에서 추가 되었습니다.  
  
|함수|Description|  
|--------------|-----------------|  
|**CURRENT_DATE ()** (ODBC 3.0)|현재 날짜를 반환합니다.|  
|**CURRENT_TIME [(** *시간 정밀도* **)]** (ODBC 3.0)|현재 현지 시간을 반환합니다. *시간 전체 자릿수* 인수는 반환된 된 값의 초 전체 자릿수를 결정 합니다.|  
|**CURRENT_TIMESTAMP**<br /> **[(** *타임 스탬프 정밀도* **)]** (ODBC 3.0)|현재 현지 날짜와 현지 시간을 타임 스탬프 값으로 반환합니다. *타임 스탬프 정밀도* 인수는 반환 된 타임 스탬프의 초 전체 자릿수를 결정 합니다.|  
|**CURDATE ()** (ODBC 1.0)|현재 날짜를 반환합니다.|  
|**CURTIME ()** (ODBC 1.0)|현재 현지 시간을 반환합니다.|  
|**DAYNAME (** *date_exp* **)** (ODBC 2.0)|(예: 일요일부터 토요일 또는 Sun 날의 데이터 원본에 따른 특정 이름 포함 하는 문자열을 반환 합니다. Sunday에서 독일어를 사용 하는 데이터 원본에 대 한 Samstag 통해 Sonntag 하거나 영어를 사용 하는 데이터 원본)에 대 한 일 부분에 대 한 *date_exp*합니다.|  
|**DAYOFMONTH (** *date_exp* **)** (ODBC 1.0)|월 필드에 따라 해당 월의 일을 반환 *date_exp* 1-31 범위의 정수 값으로.|  
|**DAYOFWEEK (** *date_exp* **)** (ODBC 1.0)|주 필드에 따라 요일을 반환 *date_exp* 범위의 정수 값으로 1-7, 여기서 1은 일요일을 나타냅니다.|  
|**DAYOFYEAR (** *date_exp* **)** (ODBC 1.0)|year 필드에 따라 해의 날짜 반환 *date_exp* 1-366 범위의 정수 값으로.|  
|**추출 (** *필드 추출 FROM* *추출 원본***)** (ODBC 3.0)|반환 된 *필드 추출* 부분의 *추출 원본*합니다. *추출 원본* 인수는 날짜/시간 또는 간격 식입니다. *필드 추출* 인수는 다음 키워드 중 하나일 수 있습니다.<br /><br /> 년 월 일 분 초<br /><br /> 반환된 된 값의 전체 자릿수는 구현 정의 합니다. 소수 자릿수는 0 초를 지정 하지 않으면이 경우 소수 자릿수 보다 작지 않습니다 소수 자릿수 초의 전체 자릿수는 *추출 원본* 필드입니다.|  
|**시간 (** *time_exp* **)** (ODBC 1.0)|시간 필드를 기반으로 시간을 반환 *time_exp* 범위 0-23의 정수 값으로.|  
|**분 (** *time_exp* **)** (ODBC 1.0)|분 필드를 기준 반환 *time_exp* 범위 0-59는 정수 값으로.|  
|**월 (** *date_exp* **)** (ODBC 1.0)|월의 월 필드에 따라 반환 *date_exp* 범위 1-12는 정수 값으로.|  
|**MONTHNAME (** *date_exp* **)** (ODBC 2.0)|월 부분에 대 한 월 (예: January에서 december 통해 영어를 사용 하는 데이터 원본에 대 한 12 월까지 또는 독일어를 사용 하는 데이터 원본의 경우에서 dezember까지)의 데이터 원본에 따른 특정 이름이 들어 있는 문자열을 반환 합니다. *date_exp*합니다.|  
|**이제 ()** (ODBC 1.0)|현재 날짜 및 시간을 타임 스탬프 값으로 반환합니다.|  
|**분기 (** *date_exp* **)** (ODBC 1.0)|분기에 반환 *date_exp* 범위의 정수 값으로 1-4, 여기서 1 년 1 월 1 년 3 월 31 일까 지 나타냅니다.|  
|**두 번째 (** *time_exp* **)** (ODBC 1.0)|두 번째 필드에 따라 두 번째 반환 *time_exp* 범위 0-59는 정수 값으로.<br /><br /> 추가 하 여 계산 된 타임 스탬프를 반환 *integer_exp* 형식의 간격 *간격* 를 *timestamp_exp*합니다. 유효한 값은 *간격* 는 다음 키워드:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> 여기서 소수 자릿수 초는 billionths 초 단위로 표현 됩니다. 예를 들어 다음 SQL 문은 자신의 1 년 기념일 및 각 직원의 이름을 반환합니다.<br /><br /> 이름, 직원에서 {fn TIMESTAMPADD (1, HIRE_DATE SQL_TSI_YEAR)을 (를) 선택<br /><br /> 경우 *timestamp_exp* 시간 값은 고 *간격* 일, 주, 월, 분기 또는 연도 날짜 부분의 지정 *timestamp_exp* 하기 전에 현재 날짜로 설정 됩니다 결과 타임 스탬프를 계산 하는 중입니다.<br /><br /> 경우 *timestamp_exp* 날짜 값이 및 *간격* 지정 소수 자릿수 초, 초, 분 또는 시간의 시간 부분 *timestamp_exp* 하기 전에 0으로 설정 되어 결과 타임 스탬프를 계산 하는 중입니다.<br /><br /> 응용 프로그램 결정 하는 간격을 호출 하 여 데이터 원본 지원 **SQLGetInfo** SQL_TIMEDATE_ADD_INTERVALS 옵션을 사용 합니다.|  
|**TIMESTAMPDIFF (** *간격*, *timestamp_exp1*, *timestamp_exp2***)** (ODBC 2.0)|정수 형식의 간격 수를 반환 *간격* 기준인 *timestamp_exp2* 보다 크면 *timestamp_exp1*합니다. 유효한 값은 *간격* 는 다음 키워드:<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> 여기서 소수 자릿수 초는 billionths 초 단위로 표현 됩니다. 예를 들어 다음 SQL 문은 자신이 이용 되어 년 수와 각 직원의 이름을 반환 합니다.<br /><br /> 이름, 직원에서 {fn TIMESTAMPDIFF (SQL_TSI_YEAR, {fn curdate ()} HIRE_DATE)을 (를) 선택<br /><br /> 두 식 중 하나가 타임 스탬프 시간 값이 있으면 및 *간격* 타임 스탬프 간의 차이 계산 하기 전에 현재 날짜로 설정 일, 주, 월, 분기 또는 연도, 해당 타임 스탬프의 날짜 부분을 지정 합니다.<br /><br /> 두 식 중 하나가 타임 스탬프는 날짜 값 이면 및 *간격* 소수 자릿수를 지정 해당 타임 스탬프의 시간 부분 초, 초, 분 또는 시간, 타임 스탬프 간의 차이 계산 하기 전에 0으로 설정 됩니다.<br /><br /> 응용 프로그램 결정 하는 간격을 호출 하 여 데이터 원본 지원 **SQLGetInfo** SQL_TIMEDATE_DIFF_INTERVALS 옵션을 사용 합니다.|  
|**주 (** *date_exp* **)** (ODBC 1.0)|주 필드에 따라 해당 연도의 주 반환 *date_exp* 1-53 범위의 정수 값으로.|  
|**연도 (** *date_exp* **)** (ODBC 1.0)|year 필드에 따라 반환 *date_exp* 정수 값으로. 범위는 데이터 소스에 따라 다릅니다.|