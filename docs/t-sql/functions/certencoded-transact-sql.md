---
title: CERTENCODED (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CERTENCODED
- CERTENCODED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CERTENCODED
ms.assetid: 677a0719-7b9a-4f0b-bc61-41634563f924
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7596187fc97c0afd1df49f9de1e7ed168de5bcb
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="certencoded-transact-sql"></a>CERTENCODED(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

인증서의 공개 부분을 이진 형식으로 반환합니다. 이 함수는 인증서 ID를 가져와서 인코딩된 인증서를 반환합니다. 이진 결과에 전달 될 수 **인증서 만들기... 이진과** 새 인증서를 만듭니다.
  
## <a name="syntax"></a>구문  
  
```sql
CERTENCODED ( cert_id )  
```  
  
## <a name="arguments"></a>인수  
*cert_id*  
이 **certificate_id** 인증서의 합니다. Sys.certificates 또는 사용 하 여 사용할 수는 [CERT_ID &#40; Transact SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) 함수입니다. *cert_id* 형식이 **int**
  
## <a name="return-types"></a>반환 형식
**varbinary**
  
## <a name="remarks"></a>주의  
**CERTENCODED** 및 **CERTPRIVATEKEY** 는 이진 형식으로 인증서의 다른 부분을 반환 하는 데 함께 사용 됩니다.
  
## <a name="permissions"></a>Permissions  
**CERTENCODED** 는 누구나 사용할 수 있습니다.
  
## <a name="examples"></a>예  
  
### <a name="simple-example"></a>간단한 예  
다음 예에서는 이라는 인증서 `Shipping04` 다음 사용 하 여는 **CERTENCODED** 인증서의 이진 인코딩을 반환 하는 함수입니다.
  
```sql
CREATE DATABASE TEST1;  
GO  
USE TEST1  
CREATE CERTIFICATE Shipping04   
ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
WITH SUBJECT = 'Sammamish Shipping Records',   
EXPIRY_DATE = '20161031';  
GO  
SELECT CERTENCODED(CERT_ID('Shipping04'));  
  
```  
  
### <a name="b-copying-a-certificate-to-another-database"></a>2. 다른 데이터베이스에 인증서 복사  
조금 더 복잡한 다음 예에서는 `SOURCE_DB` 및 `TARGET_DB`라는 두 개의 데이터베이스를 만듭니다. 여기서 목표는 `SOURCE_DB`에서 인증서를 만든 다음 인증서를 `TARGET_DB`에 복사하고 `SOURCE_DB`에서 암호화된 데이터를 인증서 복사본을 사용하여 `TARGET_DB`에서 암호를 해독할 수 있는지 증명하는 것입니다.
  
예제 환경을 만들려면 `SOURCE_DB` 및 `TARGET_DB` 데이터베이스를 만들고 각 데이터베이스에 하나의 마스터 키를 만듭니다. 그런 다음 `SOURCE_DB`에서 인증서를 만듭니다.
  
```sql
USE master;  
GO  
CREATE DATABASE SOURCE_DB;  
GO  
USE SOURCE_DB;  
GO  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0URCE_DB KEY Pa$$W0rd';  
GO  
CREATE DATABASE TARGET_DB;  
GO  
USE TARGET_DB  
GO  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'Pa$$W0rd in TARGET_DB';  
GO  
  
-- Create a certificate in SOURCE_DB  
USE SOURCE_DB;  
GO  
CREATE CERTIFICATE SOURCE_CERT WITH SUBJECT = 'SOURCE_CERTIFICATE';  
GO  
```  
  
이제 인증서에 대한 이진 설명을 추출합니다.
  
```sql
DECLARE @CERTENC VARBINARY(MAX);  
DECLARE @CERTPVK VARBINARY(MAX);  
SELECT @CERTENC = CERTENCODED(CERT_ID('SOURCE_CERT'));  
SELECT @CERTPVK = CERTPRIVATEKEY(CERT_ID('SOURCE_CERT'),  
       'CertEncryptionPa$$word');  
SELECT @CERTENC AS BinaryCertificate;  
SELECT @CERTPVK AS EncryptedBinaryCertificate;  
GO  
```  
  
`TARGET_DB` 데이터베이스에서 중복 인증서를 만듭니다. 이전 단계에서 반환된 두 이진 값을 삽입하여 다음 코드를 수정해야 합니다.
  
```sql
-- Create the duplicate certificate in the TARGET_DB database  
USE TARGET_DB  
GO  
CREATE CERTIFICATE TARGET_CERT  
FROM BINARY = <insert the binary value of the @CERTENC variable>  
WITH PRIVATE KEY (  
BINARY = <insert the binary value of the @CERTPVK variable>  
, DECRYPTION BY PASSWORD = 'CertEncryptionPa$$word');  
-- Compare the certificates in the two databases  
-- The two certificates should be the same   
-- except for name and (possibly) the certificate_id  
SELECT * FROM SOURCE_DB.sys.certificates  
UNION  
SELECT * FROM TARGET_DB.sys.certificates;  
```  
  
단일의 일괄 처리로 실행되는 다음 코드는 `SOURCE_DB`에서 암호화된 데이터를 `TARGET_DB`에서 암호 해독할 수 있음을 증명합니다.
  
```sql
USE SOURCE_DB;  
  
DECLARE @CLEARTEXT nvarchar(100);  
DECLARE @CIPHERTEXT varbinary(8000);  
DECLARE @UNCIPHEREDTEXT_Source nvarchar(100);  
SET @CLEARTEXT = N'Hello World';  
SET @CIPHERTEXT = ENCRYPTBYCERT(CERT_ID('SOURCE_CERT'), @CLEARTEXT);  
SET @UNCIPHEREDTEXT_Source =   
    DECRYPTBYCERT(CERT_ID('SOURCE_CERT'), @CIPHERTEXT)  
-- Encryption and decryption result in SOURCE_DB  
SELECT @CLEARTEXT AS SourceClearText, @CIPHERTEXT AS SourceCipherText,   
       @UNCIPHEREDTEXT_Source AS SourceDecryptedText;  
  
-- SWITCH DATABASE  
USE TARGET_DB;  
  
DECLARE @UNCIPHEREDTEXT_Target nvarchar(100);  
SET @UNCIPHEREDTEXT_Target = DECRYPTBYCERT(CERT_ID('TARGET_CERT'), @CIPHERTEXT);  
-- Encryption and decryption result in TARGET_DB  
SELECT @CLEARTEXT AS ClearTextInTarget, @CIPHERTEXT AS CipherTextInTarget, @UNCIPHEREDTEXT_Target AS DecriptedTextInTarget;   
GO  
```  
  
## <a name="see-also"></a>참고 항목
[보안 함수&#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
[CREATE CERTIFICATE&#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[CERTPRIVATEKEY &#40; Transact SQL &#41;](../../t-sql/functions/certprivatekey-transact-sql.md)  
[sys.certificates&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)
  
  
