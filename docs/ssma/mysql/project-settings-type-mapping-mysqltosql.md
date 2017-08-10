---
title: "프로젝트 설정 (형식 매핑) (MySQLToSQL) | Microsoft Docs"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
caps.latest.revision: 13
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 269c901b4242ae199f6d83fc7f678c29be39e5e5
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-type-mapping-mysqltosql"></a>프로젝트 설정 (형식 매핑) (MySQLToSQL)
프로젝트 유형 매핑 설정 SSMA 프로젝트에 대 한 기본 형식 매핑을 설정할 수 있습니다.  

프로젝트 설정 및 프로젝트 기본 설정 대화 상자에는 형식 매핑이 제공 됩니다.  
  
-   프로젝트 설정 대화 상자를 사용 하 여 현재 프로젝트에 대 한 구성 옵션을 설정 합니다. 형식 매핑을 설정 도구 메뉴에 액세스 하려면 프로젝트 설정을 선택 하 고 왼쪽된 창에서 형식 매핑 클릭 합니다.  
  
-   기본 프로젝트 설정 대화 상자를 사용 하 여 모든 프로젝트에 대 한 구성 옵션을 설정 합니다. 형식 매핑에 액세스 하려면 도구 메뉴에서 설정을 선택 기본 프로젝트 설정, 설정 된 볼 /에서 변경 하는 데 필요한 선택 마이그레이션 프로젝트 형식을 **마이그레이션 대상 버전** 드롭다운 하 고 왼쪽된 창에서 형식 매핑 클릭 합니다.  
  
## <a name="options"></a>옵션  
  
##### <a name="source-type"></a>원본 유형  
대상 데이터베이스의 데이터 형식에 매핑할 수 있는 MySQL 데이터 형식입니다.  
  
##### <a name="target-type"></a>대상 유형  
지정된 된 MySQL 데이터 형식에 대 한 대상 데이터베이스 데이터 형식입니다.  
  
##### <a name="add"></a>추가  
데이터 형식 매핑 목록에 추가 하려면 클릭 합니다.  
  
##### <a name="edit"></a>편집  
선택한 데이터 형식 매핑 목록에서 편집 하려면 클릭 합니다.  
  
##### <a name="remove"></a>제거  
매핑 목록에서 선택한 데이터 형식 매핑을 제거 하려면 클릭 합니다.  
  
##### <a name="reset-to-default"></a>기본값으로 다시 설정  
형식 매핑 목록 SSMA 기본값으로 다시 설정 하려면 클릭 합니다.  
  
## <a name="type-mappings"></a>형식 매핑  
다음 표에서 소스 및 대상 데이터 형식 간의 기본 매핑을 보여 줍니다.  
  
|||  
|-|-|  
|**MySQL 데이터 형식**|**SQL Server 데이터 형식**|  
|bigint|bigint|  
|bigint [*...255]|bigint|  
|binary|이진 [1]|  
|이진 [0..1]|이진 [1]|  
|이진 [2..255]|이진 [*]|  
|bit|이진 [1]|  
|비트 [0..8]|이진 [1]|  
|비트 [17..24]|이진 [3]|  
|비트 [25..32]|이진 [4]|  
|비트 [33..40]|이진 [5]|  
|비트 [41..48]|이진 [6]|  
|비트 [49..56]|이진 [7]|  
|비트 [57..64]|이진 [8]|  
|비트 [9..16]|이진 파일 [2]|  
|blob|varbinary(max)|  
|blob [0..1]|varbinary [1]|  
|blob [2..8000]|varbinary [*]|  
|blob [8001..*]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char|nchar [1]|  
|char 바이트|이진 [1]|  
|char 바이트 [0..1]|이진 [1]|  
|char 바이트 [2..255]|이진 [*]|  
|char [0..1]|nchar [1]|  
|char [2..255]|nchar [*]|  
|character|nchar [1]|  
|[0..1] 다양 한 문자|nvarchar [1]|  
|다양 한 2..255 문자|nvarchar|  
|문자 [0..1]|nchar [1]|  
|문자 [2..255]|nchar [*]|  
|date|date|  
|datetime|datetime2 [0]|  
|dec|decimal|  
|dec [*...65]|decimal [*] [0]|  
|dec [*...65][\*..30]|decimal [*] [\*]|  
|decimal|decimal|  
|10 진수 [*...65]|decimal [*] [0]|  
|10 진수 [*...65][\*..30]|decimal [*] [\*]|  
|double|float [53]|  
|배정밀도|float [53]|  
|배정밀도 [*...255][\*..30]|숫자 [*] [\*]|  
|double [*...255][\*..30]|숫자 [*] [\*]|  
|고정|numeric|  
|고정 [*...65][\*..30]|숫자 [*] [\*]|  
|float|float [24]|  
|float [*...255][\*..30]|숫자 [*] [\*]|  
|float [*...53]|float [53]|  
|int|int|  
|int [*...255]|int|  
|integer|int|  
|정수 [*...255]|int|  
|longblob|varbinary(max)|  
|longtext|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|int|  
|mediumint [*...255]|int|  
|mediumtext|nvarchar(max)|  
|국가별 문자|nchar [1]|  
|national char [0..1]|nchar [1]|  
|national char [2..255]|nchar [*]|  
|국가별 문자|nchar [1]|  
|다양 한 국가별 문자|nvarchar [1]|  
|[0..1] 다양 한 국가별 문자|nvarchar [1]|  
|[2..4000] 다양 한 국가별 문자|nvarchar [*]|  
|다양 한 국가별 문자 [4001..*]|nvarchar(max)|  
|국가별 문자 [0..1]|nchar [1]|  
|국가별 문자 [2..255]|nchar [*]|  
|national varchar|nvarchar [1]|  
|national varchar [0..1]|nvarchar [1]|  
|national varchar [2..4000]|nvarchar [*]|  
|national varchar [4001..*]|nvarchar(max)|  
|nchar|nchar [1]|  
|nchar varchar|nvarchar [1]|  
|nchar varchar [0..1]|nvarchar [1]|  
|nchar varchar [2..4000]|nvarchar [*]|  
|nchar varchar [4001..*]|nvarchar(max)|  
|nchar [0..1]|nchar [1]|  
|nchar [2..255]|nchar [*]|  
|numeric|numeric|  
|숫자 [*...65]|숫자 [*] [0]|  
|숫자 [*...65][\*..30]|숫자 [*] [\*]|  
|nvarchar|nvarchar [1]|  
|nvarchar [0..1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar [4001..*]|nvarchar(max)|  
|real|float [53]|  
|실제 [*...255][\*..30]|숫자 [*] [\*]|  
|직렬|bigint|  
|smallint|smallint|  
|smallint [*...255]|smallint|  
|text|nvarchar(max)|  
|텍스트 [0..1]|nvarchar [1]|  
|텍스트 [2..4000]|nvarchar [*]|  
|텍스트 [4001..*]|nvarchar(max)|  
|time|time|  
|timestamp|datetime|  
|tinyblob|varbinary [255]|  
|tinyint|smallint|  
|tinyint [*...255]|smallint|  
|tinytext|nvarchar [255]|  
|부호 없는 bigint|bigint|  
|부호 없는 bigint [*...255]|bigint|  
|부호 없는 10 진수|decimal|  
|부호 없는 10 진수 [*...65]|decimal [*] [0]|  
|부호 없는 10 진수 [*...65][\*..30]|decimal [*] [\*]|  
|부호 없는 10 진수|decimal|  
|부호 없는 10 진수 [*...65]|decimal [*] [0]|  
|부호 없는 10 진수 [*...65][\*..30]|decimal [*] [\*]|  
|double 서명 되지 않은|float [53]|  
|배정밀도 서명 되지 않은|float [53]|  
|배정밀도 서명 되지 않은 [*...255][\*..30]|숫자 [*] [\*]|  
|double 서명 되지 않은 [*...255][\*..30]|숫자 [*] [\*]|  
|서명 되지 않은 고정|numeric|  
|서명 되지 않은 고정 [*...65][\*..30]|숫자 [*] [\*]|  
|서명 되지 않은 부동 소수점|float [24]|  
|부호 없는 float [*...255][\*..30]|숫자 [*] [\*]|  
|부호 없는 float [*...53]|float [53]|  
|부호 없는 정수|bigint|  
|부호 없는 int [*...255]|bigint|  
|부호 없는 정수|bigint|  
|부호 없는 정수 [*...255]|bigint|  
|부호 없는 mediumint|int|  
|부호 없는 mediumint [*...255]|int|  
|부호 없는 숫자|numeric|  
|부호 없는 숫자 [*...65]|숫자 [*] [0]|  
|부호 없는 숫자 [*...65][\*..30]|숫자 [*] [\*]|  
|실제 서명 되지 않은|float [53]|  
|실제 서명 되지 않은 [*...255[[\*..30]|숫자 [*] [\*]|  
|부호 없는 smallint|int|  
|부호 없는 smallint [*...255]|int|  
|부호 없는 tinyint|tinyint|  
|부호 없는 tinyint [*...255]|tinyint|  
|varbinary [0..1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001..*]|varbinary(max)|  
|varchar [0..1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar [4001..*]|nvarchar(max)|  
|year|smallint|  
|연도 [2..2]|smallint|  
|연도 [4..4]|smallint|  
  
##### <a name="add"></a>추가  
데이터 형식 매핑 목록에 추가 하려면 클릭 합니다.  
  
##### <a name="edit"></a>편집  
데이터 형식 매핑 목록에서 편집 하려면 클릭 합니다.  
  
##### <a name="remove"></a>제거  
매핑 목록에서 선택한 데이터 형식 매핑을 제거 하려면 클릭 합니다.  
  
##### <a name="reset-to-default"></a>기본값으로 다시 설정  
모든 데이터 형식 매핑을 SSMA 기본값으로 다시 설정 하려면 클릭 합니다.  
  
