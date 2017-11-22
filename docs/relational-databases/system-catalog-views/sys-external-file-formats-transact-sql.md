---
title: sys.external_file_formats (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46ac5d27d81c1e8162981340115e563d1e1c3991
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2017
---
# <a name="sysexternalfileformats-transact-sql"></a>sys.external_file_formats (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  각 외부 파일 형식에 대 한 현재 데이터베이스에 대해 행을 포함 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], 및 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]합니다.  
  
 각 외부 파일 형식에 대 한 서버에 대해 행을 포함 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]합니다.  
  
|열 이름|데이터 형식|Description|범위|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|외부 파일 형식에 대 한 개체 ID입니다.||  
|name|**sysname**|파일 형식 이름입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], 데이터베이스에 대해 고유 합니다. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], 서버에 대해 고유 합니다.||  
|format_type|**tinyint**|파일 형식 유형입니다.|에서는 DELIMITEDTEXT, RCFILE, ORC, PARQUET|  
|field_terminator|**nvarchar (10)**|Format_type =에서는 DELIMITEDTEXT, 필드 종결자입니다.||  
|string_delimiter|**nvarchar (10)**|Format_type =에서는 DELIMITEDTEXT, 문자열 구분 기호입니다.||  
|date_format|**nvarchar(50)**|Format_type =에서는 DELIMITEDTEXT, 사용자 지정 날짜 및 시간 형식입니다.||  
|use_type_default|**bit**|Format_type = 분리 된 텍스트, PolyBase는 HDFS 텍스트 파일의 데이터를 가져올 때 누락 값을 처리 하는 방법을 지정 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]합니다.|0 – 문자열 'NULL'으로 누락 된 값을 저장 합니다.<br /><br /> 1-열 기본값으로 누락 된 값을 저장 합니다.|  
|serde_method|**nvarchar(255)**|Format_type = RCFILE,이 serialization/deserialization 메서드입니다.||  
|row_terminator|**nvarchar (10)**|Format_type =에서는 DELIMITEDTEXT, 외부 Hadoop 파일의 각 행을 종료 하는 문자열입니다.|항상 ' \n '입니다.|  
|인코딩|**nvarchar (10)**|Format_type =에서는 DELIMITEDTEXT, 이것이 외부 Hadoop 파일에 대 한 인코딩 방법입니다.|항상 ' UTF8'가 있습니다.|  
|data_compression|**nvarchar(255)**|외부 데이터에 대 한 데이터 압축 메서드입니다.|에서는 DELIMITEDTEXT = format_type의 경우:<br /><br /> -'org.apache.hadoop.io.compress.DefaultCodec'<br />-'org.apache.hadoop.io.compress.GzipCodec'<br /><br /> RCFILE = format_type의 경우:<br /><br /> -'org.apache.hadoop.io.compress.DefaultCodec'<br /><br /> ORC = format_type의 경우:<br /><br /> -'org.apache.hadoop.io.compress.DefaultCodec'<br />-'org.apache.hadoop.io.compress.SnappyCodec'<br /><br /> PARQUET = format_type의 경우:<br /><br /> -'org.apache.hadoop.io.compress.GzipCodec'<br />-'org.apache.hadoop.io.compress.SnappyCodec'|  
  
## <a name="permissions"></a>Permissions  
 사용자가 소유하고 있거나 사용 권한을 부여 받은 보안 개체에 대해서만 카탈로그 뷰의 메타데이터를 볼 수 있습니다. 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목:  
 [sys.external_data_sources&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys.external_tables&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT&#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  