---
title: "SQL Server 암호화 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "암호화 [SQL Server], 암호화 정보"
  - "보안 [SQL Server], 암호화"
  - "암호화 [SQL Server], 암호화 정보"
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# SQL Server 암호화
  암호화는 키 또는 암호를 사용하여 데이터를 난독 처리하는 프로세스입니다. 이 경우 해당하는 암호 해독 키 또는 암호가 없으면 데이터를 사용할 수 없게 됩니다. 암호화를 통해 액세스 제어 문제를 해결할 수는 없습니다. 그러나 암호화를 사용하면 액세스 제어가 무시되는 경우에도 데이터 손실을 제한하여 보안이 향상됩니다. 예를 들어 데이터베이스 호스트 컴퓨터가 잘못 구성되어 해커가 중요한 데이터를 얻는 경우 해당 정보가 암호화되어 있으면 해킹한 정보를 사용하지 못할 수도 있습니다.  
  
 연결, 데이터 및 저장 프로시저에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 암호화를 사용할 수 있습니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 암호화에 대한 자세한 정보를 제공합니다.  
  
> [!IMPORTANT]  
>  암호화가 보안을 유지해 주는 유용한 도구지만 모든 데이터나 연결에 대해 고려해야 하는 것은 아닙니다. 암호화 구현 여부를 결정할 때는 사용자가 데이터에 액세스하는 방법을 고려해야 합니다. 사용자가 공용 네트워크를 통해 데이터에 액세스할 경우 보안을 높이기 위한 데이터 암호화가 필요할 수도 있습니다. 그러나 모든 액세스가 보안 인트라넷 구성과 관련된 경우 암호화가 필요하지 않을 수도 있습니다. 암호화를 사용하려면 암호, 키 및 인증서에 대한 유지 관리 전략도 고려해야 합니다.  
  
> [!NOTE]  
>  전송 수준 보안(TSL1.2)에 대한 최신 정보는 [Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/kb/3135244)에서 확인할 수 있습니다.  
  
## 섹션 내용  
 [암호화 계층](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 암호화 계층에 대한 정보입니다.  
  
 [암호화 알고리즘 선택](../../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
 효과적인 암호화 알고리즘을 선택하는 방법에 대한 정보입니다.  
  
 [투명한 데이터 암호화&#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)  
 데이터를 명시적으로 암호화하는 방법에 대한 일반적인 정보입니다.  
  
 [SQL Server 및 데이터베이스 암호화 키&#40;데이터베이스 엔진&#41;](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 암호화 키에는 중요한 데이터를 보호하는 데 사용되는 공개 키, 개인 키 및 대칭 키의 조합이 포함됩니다. 이 섹션에서는 암호화 키를 구현하고 관리하는 방법에 대해 설명합니다.  
  
 [상시 암호화&#40;데이터베이스 엔진&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
 온-프레미스 데이터베이스 관리자, 클라우드 데이터베이스 운영자 또는 기타 높은 권한을 가지고 있지만 인증되지 않은 사용자가 암호화된 데이터에 액세스할 수 없도록 합니다.  
  
 [동적 데이터 마스킹](../../../relational-databases/security/dynamic-data-masking.md)  
 권한이 없는 사용자로 마스킹하여 중요한 데이터 노출을 제한합니다.  
  
 [SQL Server 인증서 및 비대칭 키](../../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)  
 공개 키 암호화를 사용하는 방법에 대한 정보입니다.  
  
## 관련 내용  
 [SQL Server 보안 설정](../../../relational-databases/security/securing-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 플랫폼에 보안을 설정하는 방법 및 사용자 및 보안 개체 작업을 수행하는 방법에 대한 개요입니다.  
  
 [암호화 함수&#40;Transact-SQL&#41;](../../../t-sql/functions/cryptographic-functions-transact-sql.md)  
 암호화 함수 구현 방법에 대한 정보입니다.  
  
 [ENCRYPTBYPASSPHRASE&#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
 데이터를 암호화하기 위해 암호를 사용하는 방법에 대한 정보입니다.  
  
 [ENCRYPTBYKEY&#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbykey-transact-sql.md)  
 데이터를 암호화하기 위해 대칭 키를 사용하는 방법에 대한 정보입니다.  
  
 [ENCRYPTBYASYMKEY&#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbyasymkey-transact-sql.md)  
 데이터를 암호화하기 위해 비대칭 키를 사용하는 방법에 대한 정보입니다.  
  
 [ENCRYPTBYCERT&#40;Transact-SQL&#41;](../../../t-sql/functions/encryptbycert-transact-sql.md)  
 데이터를 암호화하기 위해 인증서를 사용하는 방법에 대한 정보입니다.  
  
## 외부 리소스  
 [Microsoft TechNet: SQL Server TechCenter: SQL Server 2005  보안 및 보호](https://msdn.microsoft.com/sqlserver/bb895847.aspx)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 보안에 대한 현재 정보입니다.  
  
## 참고 항목  
 [sys.key_encryptions&#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)   
 [SQL Server 및 데이터베이스 암호화 키&#40;데이터베이스 엔진&#41;](../../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)   
 [Reporting Services 암호화 키 백업 및 복원](../../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md)  
  
  