---
title: bcp_moretext | Microsoft Docs
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
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 22b9c6345b3dcdbb2a1b6bc5db735dcb2d635f5d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36172633"
---
# <a name="bcpmoretext"></a>bcp_moretext
  긴 가변 길이 데이터 형식 값의 일부를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
```  
  
## <a name="arguments"></a>인수  
 *hdbc*  
 대량 복사가 가능한 ODBC 연결 핸들입니다.  
  
 *cbData*  
 참조 데이터에서 SQL Server로 복사 되는 데이터의 바이트 수는 *pData*합니다. SQL_NULL_DATA 값은 NULL을 나타냅니다.  
  
 *pData*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 보낼 지원되는 긴 가변 길이 데이터 청크에 대한 포인터입니다.  
  
## <a name="returns"></a>반환 값  
 SUCCEED 또는 FAIL  
  
## <a name="remarks"></a>Remarks  
 와 함께에서이 함수를 사용할 수 있습니다 [bcp_bind](bcp-bind.md) 및 [bcp_sendrow](bcp-sendrow.md) long, 다양 한 더 작은 청크로 SQL Server에 가변 길이 데이터 값을 복사 합니다. **bcp_moretext** 다음 SQL Server 데이터 형식의 열을 사용할 수 있습니다: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, 사용자 정의 형식 (UDT) 및 XML입니다. **bcp_moretext** 데이터 변환을 지원 하지 않으며, 제공 된 데이터가 대상 열의 데이터 형식과 일치 해야 합니다.  
  
 경우 **bcp_bind** 으로 null이 아닌 호출 *pData* 에서 지원 되는 데이터 형식에 대 한 매개 변수 **bcp_moretext**, `bcp_sendrow` 전체 데이터 값에 관계 없이 전송 길이입니다. 그러나 If, **bcp_bind** 에 NULL *pData* 지원 되는 데이터 형식에 대 한 매개 변수 **bcp_moretext** 는 에서성공적인반환후에즉시데이터를복사하는데사용할수`bcp_sendrow` 나타내는 데이터가 있는 바인딩된 모든 열이 처리 되었습니다.  
  
 사용 하는 경우 **bcp_moretext** 한 지원 되는 데이터 형식 열을 행에 보내려면도 사용 해야 행의 다른 모든 지원 되는 데이터 형식 열을 보내려고 합니다. 열을 건너뛸 수 없습니다. 지원되는 데이터 형식은 SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT 및 SQLXML입니다. 열이 각각 varchar(max), nvarchar(max) 또는 varbinary(max)인 경우 SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY 및 SQLVARBINARY도 이 범주에 해당합니다.  
  
 호출 **bcp_bind** 또는 [bcp_collen](bcp-collen.md) SQL Server 열에 복사할 모든 데이터 부분의 총 길이 가져오거나 설정 합니다. SQL Server에 대 한 호출에 지정 된 것 보다 많은 바이트를 보내기 위해 **bcp_bind** 또는 `bcp_collen` 오류가 발생 합니다. 이 오류가 발생, 예를 들어 사용 되는 응용 프로그램에서 `bcp_collen` SQL Server에 대 한 사용 가능한 데이터의 길이 설정 하려면 `text` 를 4500으로 열 다음 호출 **bcp_moretext** 5 번 각 호출 동안 데이터 버퍼 길이가 1000 바이트 했습니다.  
  
 복사한 행 둘 이상의 long, 가변 길이 열이 있는 경우 **bcp_moretext** 가장 낮은 데이터에는 서 수 열을 다음으로 번호가 지정 하는 첫 번째 보냅니다 가장 낮은 열순으로 번호가 열 및 기타 등등. 필요한 데이터의 총 길이를 올바르게 설정하는 것이 중요합니다. 길이 설정 외에는 대량 복사에서 열의 모든 데이터가 수신되었음을 나타낼 방법이 없습니다.  
  
 때 `var(max)` 값 보내집니다 bcp_sendrow 및 bcp_moretext를 사용 하 여 서버에 필요 없는 열 길이 설정 하는 bcp_collen를 호출 하 합니다. 대신, 이러한 형식에 대 한 값은 길이가 0 인 bcp_sendrow를 호출 하 여 종료 됩니다.  
  
 응용 프로그램이 정상적으로 호출 `bcp_sendrow` 및 **bcp_moretext** 보낼 데이터의 행 수가 루프 내에서. 다음은 두 개를 포함 하는 테이블에 대 한이 작업을 수행 하는 방법의 개요 `text` 열:  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a>예제  
 사용 하는 방법을 보여 주는이 예제 **bcp_moretext** 와 **bcp_bind** 및 `bcp_sendrow`:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>관련 항목  
 [대량 복사 함수](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  