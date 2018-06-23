---
title: 'Ibcpsession:: Bcpreadfmt (OLE DB) | Microsoft Docs'
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
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f47369cb66f6695ca7a235beb72536ce34495bb5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187201"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt(OLE DB)
  서식 파일에서 각 열의 서식 정보를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Remarks  
 **BCPReadFmt** 데이터 파일에 데이터의 형식을 지정 하는 서식 파일에서 데이터를 읽기 위한 메서드를 사용 합니다. 이 메서드는 서식 파일의 올바른 버전을 검색할 수 있으므로 서식 파일이 xml인지 이전 스타일의 텍스트 형식인지 자동으로 검색하여 그에 따라 동작합니다. 서식 파일 버전에서 지원 되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 BCP 버전 6.0 이상이 됩니다.  
  
 후의 **BCPReadFmt** 메서드 형식 값을 읽고, 적절 한 호출에서 [ibcpsession:: Bcpcolumns](ibcpsession-bcpcolumns-ole-db.md) 및 [ibcpsession:: Bcpcolfmt](ibcpsession-bcpcolfmt-ole-db.md) 메서드. 따라서 사용자가 서식 파일의 구문을 분석하여 메서드를 호출할 필요가 없습니다.  
  
 서식 파일을 저장 하려면 호출는 [ibcpsession:: Bcpwritefmt](ibcpsession-bcpwritefmt-ole-db.md) 메서드. 에 대 한 호출이 **BCPReadFmt** 메서드는 저장 된 서식을 참조할 수 있습니다. 대량 복사 유틸리티 또는 (**bcp**) 사용자 정의 데이터 형식에서 참조 될 수 있는 파일에 저장할 수는 **BCPReadFmt** 메서드.  
  
 `BCP_OPTION_DELAYREADFMT` 의 값은 *eOption* 의 매개 변수 [ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md) ibcpsession:: Bcpreadfmt의 동작을 수정 합니다.  
  
## <a name="arguments"></a>인수  
 *pwszFormatFile*[in]  
 데이터 파일에 대한 형식 값이 포함된 파일의 경로 및 파일 이름입니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 S_OK  
 메서드가 성공했습니다.  
  
 E_FAIL  
 사용 하 여 자세한 정보에 대 한 공급자 관련 오류가 발생 한는 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) 인터페이스입니다.  
  
 E_OUTOFMEMORY  
 메모리 부족 오류가 발생했습니다.  
  
 E_UNEXPECTED  
 예기치 않은 메서드가 호출되었습니다. 예를 들어는 [ibcpsession:: Bcpinit](ibcpsession-bcpinit-ole-db.md) 이 메서드를 호출 하기 전에 메서드를 호출 하지 않았습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [대량 복사 작업 수행](../native-client/features/performing-bulk-copy-operations.md)  
  
  