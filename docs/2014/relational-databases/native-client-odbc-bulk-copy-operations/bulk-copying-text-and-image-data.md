---
title: 텍스트 및 이미지 데이터를 복사 하는 대량 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], text data
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], image data
- ODBC, bulk copy operations
ms.assetid: 87155bfa-3a73-4158-9d4d-cb7435dac201
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c674c24b4000ada4651dfb44ed2d49e9fd5bde83
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36080869"
---
# <a name="bulk-copying-text-and-image-data"></a>텍스트 및 이미지 데이터 대량 복사
  큰 **텍스트**, **ntext**, 및 **이미지** 값은 대량 복사를 사용 하는 [bcp_moretext](../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) 함수입니다. 코드 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) 에 대 한는 **텍스트**, **ntext**, 또는 **이미지** 인 열을 *pData* 포인터가으로 설정 데이터 제공 NULL 나타내는 **bcp_moretext**합니다. 각각에 대해 제공 하는 데이터의 정확한 길이 지정 해야 **텍스트**, **ntext**, 또는 **이미지** 각 대량 복사 행의 열입니다. 열에 대 한 데이터의 길이에 지정 된 열 길이와 다르면 [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)를 사용 하 여 [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) 길이 올바른 값으로 설정 하려면. A [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) 보냅니다 모든 비**텍스트**, 비-**ntext**, 및 비-**이미지** 데이터; 다음을 호출할 수 **bcp_moretext** 보내려고는 **텍스트**, **ntext**, 또는 **이미지** 데이터를 별도 단위로 합니다. 대량 복사 함수는 current에 대 한 모든 데이터가 보냈음을 확인 **텍스트**, **ntext**, 또는 **이미지** 데이터의 길이의 합 를통해전송될때열**bcp_moretext** 최신에 지정 된 길이 같으면 **bcp_collen** 또는 **bcp_bind**합니다.  
  
 **bcp_moretext** 에 열을 식별 하 매개 변수가 없습니다. 여러 **텍스트**, **ntext**, 또는 **이미지** 한 행의에서 열 **bcp_moretext** 에서 작동 하는 **텍스트**, **ntext**, 또는 **이미지** 열 서 수 번호가 가장 높은 열을 계속 가장 낮은 서 수 및 열으로 시작 합니다. **bcp_moretext** 라인이 한 열에서 다음에 전송 되는 데이터의 길이의 합과 최신에 지정 된 길이 **bcp_collen** 또는 **bcp_bind** 현재 열에 대 한 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [대량 복사 작업 수행 &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  