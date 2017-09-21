---
title: "설명자 전환 | Microsoft Docs"
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
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 280d35d8ce03d3d7685441c12d99c05c9ff5f451
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="descriptor-transitions"></a>설명자 전환
ODBC 설명자는 다음 세 가지 상태입니다.  
  
|State|Description|  
|-----------|-----------------|  
|D0|할당 되지 않은 설명자|  
|D1i|암시적으로 할당 된 설명자|  
|D1e|명시적으로 할당 된 설명자|  
  
 다음 표에서 각 ODBC 함수 설명자 상태에 미치는 영향을 보여 줍니다.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> 할당되지 않음|D1i<br /><br /> Implicit|D1e<br /><br /> Explicit|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1]이이 행 표시 전환 때 *HandleType* 여 되었습니다.  
  
 [2]이이 행 표시 전환 때 *HandleType* SQL_HANDLE_DESC 되었습니다.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> 할당되지 않음|D1i<br /><br /> Implicit|D1e<br /><br /> Explicit|  
|------------------------|----------------------|----------------------|  
|(면)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> 할당되지 않음|D1i<br /><br /> Implicit|D1e<br /><br /> Explicit|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(면) [2]|(HY017)|D0|  
  
 [1]이이 행 표시 전환 때 *HandleType* 여 되었습니다.  
  
 [2]이이 행 표시 전환 때 *HandleType* SQL_HANDLE_DESC 되었습니다.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField 및 SQLGetDescRec  
  
|D0<br /><br /> 할당되지 않음|D1i<br /><br /> Implicit|D1e<br /><br /> Explicit|  
|------------------------|----------------------|----------------------|  
|(면)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField 및 SQLSetDescRec  
  
|D0<br /><br /> 할당되지 않음|D1i<br /><br /> Implicit|D1e<br /><br /> Explicit|  
|------------------------|----------------------|----------------------|  
|(면) [1]|--|--|  
  
 [1]이이 행 표시 전환 때 *DescriptorHandle* 카드가, APD, 또는, IPD의 핸들을가 또는 (에 대 한 **SQLSetDescField**) 때 *DescriptorHandle* IRD의 핸들을 되었습니다 및 *FieldIdentifier* SQL_DESC_ARRAY_STATUS_PTR 되었거나 SQL_DESC_ROWS_PROCESSED_PTR 합니다.  
  
## <a name="all-other-odbc-functions"></a>다른 모든 ODBC 함수  
  
|D0<br /><br /> 할당되지 않음|D1i<br /><br /> Implicit|D1e<br /><br /> Explicit|  
|------------------------|----------------------|----------------------|  
|--|--|--|