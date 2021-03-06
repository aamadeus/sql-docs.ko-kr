---
title: 데이터 이해 형식 차이 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab8fa00f-cb16-47e2-94b8-3a76f56c2b84
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 546dc71fad06fc69d816d16c1d6c2d67f59f968b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773211"
---
# <a name="understanding-data-type-differences"></a>데이터 형식 차이 이해

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Java 프로그래밍 언어 데이터 형식과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 간에는 많은 차이가 있습니다. 그러나 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]는 다양한 형식 변환 기능을 통해 이러한 차이를 손쉽게 극복합니다.  

## <a name="character-types"></a>문자 형식

JDBC 문자열 데이터 형식이 됩니다 **CHAR**하십시오 **VARCHAR**, 및 **LONGVARCHAR**합니다. JDBC 드라이버는 JDBC 4.0 API를 지원합니다. JDBC 4.0에서는 JDBC 문자열 데이터 형식이 될 수도 있습니다 **NCHAR**하십시오 **NVARCHAR**, 및 **LONGNVARCHAR**합니다. 이러한 새 문자열 형식은 유니코드 형식으로 Java 네이티브 문자 형식을 유지하므로 ANSI와 Unicode 간 변환을 수행할 필요가 없습니다.  
  
| 형식            | 설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 고정 길이    | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char** 하 고 **nchar** 데이터 형식은 JDBC에 직접 매핑됩니다 **CHAR** 하 고 **NCHAR** 형식입니다. 이는 해당 열에 `SET ANSI_PADDING ON`이 설정된 경우 서버에서 패딩을 제공하는 고정 길이 형식입니다. **nchar**에 대해서는 패딩이 항상 설정되어 있지만 **char**에 대해서는 그렇지 않습니다. 서버 char 열이 패딩되지 않은 경우 JDBC 드라이버에서 패딩을 추가합니다.                                                                                                                                                                                                                                                                                                                                                                                      |
| 가변 길이 | 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varchar** 및 **nvarchar** 형식은 JDBC에 직접 매핑됩니다 **VARCHAR** 하 고 **NVARCHAR** 각각.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Long            | [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **텍스트** 및 **ntext** 형식은 JDBC에 매핑됩니다 **LONGVARCHAR** 하 고 **LONGNVARCHAR** 각각 입력 합니다. 이러한 형식은 사용 되지 않는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]큰 값 형식을 사용 해야 하므로 **varchar (max)** 또는 **nvarchar (max)**, 대신 합니다.<br /><br /> 업데이트를 사용 하 여\<숫자 유형 > 및 [updateObject (int, java.lang.Object)](../../connect/jdbc/reference/updateobject-method-int-java-lang-object.md) 방법에 대해 실패 **텍스트** 하 고 **ntext** 서버 열입니다. 그러나 **text** 및 **ntext** 서버 열에 대해 [setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md) 메서드를 지정된 문자 변환 형식과 함께 사용할 수 있습니다. |
  
## <a name="binary-string-types"></a>이진 문자열 형식

JDBC 이진 문자열 형식은 **이진**하십시오 **VARBINARY**, 및 **LONGVARBINARY**합니다.  
  
| 형식            | 설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 고정 길이    | 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **이진** JDBC에 직접 매핑됩니다 **이진** 형식입니다. 이는 해당 열에 SET ANSI_PADDING ON이 설정된 경우 서버에서 패딩을 제공하는 고정 길이 형식입니다. 서버 char 열이 패딩되지 않으면 JDBC 드라이버가 패딩을 추가합니다.<br /><br /> 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **타임 스탬프** 형식은 JDBC **이진** 8 바이트의 고정된 길이 형식입니다. |
| 가변 길이 | 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varbinary** 형식이 매핑되는 jdbc **VARBINARY** 형식입니다.<br /><br /> 합니다 **udt** 입력 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC로 매핑되는 **VARBINARY** 형식입니다.                                                                                                                                                                                                                                 |
| Long            | 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **이미지** 형식이 매핑되는 jdbc **LONGVARBINARY** 형식입니다. 이 형식은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 사용되지 않으므로 대신 큰 값 형식인 **varbinary(max)** 를 사용해야 합니다.                                                                                                                                                                                           |
  
## <a name="exact-numeric-types"></a>정확한 숫자 형식

JDBC의 정확한 숫자 형식은 해당되는 SQL Server 형식에 바로 매핑됩니다.  
  
| 형식     | 설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BIT      | JDBC **BIT** 형식은 단일 비트(0 또는 1)를 나타냅니다. 매핑되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **비트** 형식입니다.                                                                                                                                                                                                                                                                                                                                       |
| TINYINT  | JDBC **TINYINT** 형식은 단일 바이트를 나타내며 매핑되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **tinyint** 형식입니다.                                                                                                                                                                                                                                                                                                                                                 |
| SMALLINT | JDBC **SMALLINT** 형식은 부호 있는 16비트 정수를 나타내며 매핑되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **smallint** 형식입니다.                                                                                                                                                                                                                                                                                                                                     |
| INTEGER  | JDBC **INTEGER** 형식은 부호 있는 32비트 정수를 나타내며 매핑되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **int** 형식입니다.                                                                                                                                                                                                                                                                                                                                           |
| bigint   | JDBC **BIGINT** 형식은 부호 있는 64비트 정수를 나타내며 매핑되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bigint** 형식입니다.                                                                                                                                                                                                                                                                                                                                         |
| NUMERIC  | JDBC **NUMERIC** 형식은 동일한 전체 자릿수 값을 포함하는 고정 전체 자릿수 소수 값을 나타냅니다. **숫자** 형식에 매핑되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **숫자** 형식.                                                                                                                                                                                                                                                                   |
| DECIMAL  | JDBC **DECIMAL** 형식은 최소한 지정된 전체 자릿수 값을 포함하는 고정 전체 자릿수 소수 값을 나타냅니다. **10 진수** 형식에 매핑됩니다 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **decimal** 형식입니다.<br /><br /> JDBC **DECIMAL** 형식도 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **money** 및 **smallmoney** 형식에 매핑됩니다. 이 형식은 각각 8바이트와 4바이트로 저장되는 특정 고정 전체 자릿수 소수 형식입니다. |
  
## <a name="approximate-numeric-types"></a>근사 숫자 형식

JDBC 근사 숫자 형식은 **실제**하십시오 **DOUBLE**, 및 **FLOAT**.  
  
| 형식   | 설명                                                                                                                                                                                                                                                                                                   |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| real   | JDBC **REAL** 형식의 전체 자릿수는 7(단정밀도)이며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **real** 형식에 직접 매핑됩니다.                                                                                                                                     |
| DOUBLE | JDBC **DOUBLE** 형식의 전체 자릿수는 15(배정밀도)이며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float** 형식에 매핑됩니다. JDBC **부동 소수점** 형식은의 동의어 **DOUBLE**합니다. 혼동 될 수 있으므로 **부동 소수점** 하 고 **DOUBLE**, **DOUBLE** 는 것이 좋습니다. |
  
## <a name="datetime-types"></a>날짜 및 시간 형식

JDBC **타임 스탬프** 형식에 매핑됩니다 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** 하 고 **smalldatetime** 형식입니다. **datetime** 형식은 두 개의 4바이트 정수로 저장됩니다. **smalldatetime** 형식은 2바이트 small 정수와 동일한 정보(날짜 및 시간)를 포함하지만 정확도는 떨어집니다.  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** 형식은 고정 길이 이진 문자열 형식이며 JDBC 시간 형식 중 하나에 매핑되지 않는 경우: **날짜**하십시오 **시간**, 또는 **타임 스탬프**합니다.  
  
## <a name="custom-type-mapping"></a>사용자 지정 형식 매핑

JDBC 고급 형식(UDT, Struct 등)에 대해 SQLData 인터페이스를 사용하는 JDBC의 사용자 지정 형식 매핑 기능이며 JDBC 드라이버에 구현되어 있지 않습니다.  
  
## <a name="see-also"></a>참고 항목

[JDBC 드라이버 데이터 형식 이해](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
