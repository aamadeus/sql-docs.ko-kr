---
title: SQLColAttributes (Excel 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 67ba6df9955a1b138ebb919d410ef7817e1fb48e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844206"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes(Excel 드라이버)
> [!NOTE]  
>  이 항목에서는 Excel 드라이버 관련 정보를 제공 합니다. 이 함수에 대 한 일반 정보에서 해당 항목을 참조 하세요 [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
|attribute|주석|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|LONGVARBINARY 데이터용 SQL_COLUMN_DISPLAY_SIZE 없습니다 2 시간 열의 최대 길이 열의 최대 길이입니다.|  
|SQL_OWNER_NAME|빈 문자열 ("") 소유자 이름입니다. 지원 되지 않으므로이 열에 반환 됩니다.|  
|SQL_QUALIFIER_NAME|디렉터리 경로가 반환 됩니다.|  
|SQL_COLUMN_SEARCHABLE|LONGVARCHAR 및 LONGVARBINARY 열 SQL_UNSEARCHABLE로 보고 됩니다.<br /><br /> 고정 길이 및 가변 길이 이진 및 문자 데이터 형식 LONGVARCHAR 및 LONGVARBINARY 하지 않더라도 검색할 수 됩니다.|  
  
> [!NOTE]  
>  위의 아닙니다 반환 하는 특성의 전체 목록은 **SQLColAttributes**합니다.
