---
title: CREATE SEQUENCE(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SEQUENCE
- CREATE SEQUENCE
- SEQUENCE_TSQL
- CREATE_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE SEQUENCE statement
- sequence number object, creating
- sequence object
- number, sequence
ms.assetid: 419f907b-8a72-4d6c-80cb-301df44c24c1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d26d4d303ffb312a2dc289e9f7426fbc6d191de8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629043"
---
# <a name="create-sequence-transact-sql"></a>CREATE SEQUENCE(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  시퀀스 개체를 만들고 해당 속성을 지정합니다. 시퀀스는 시퀀스를 만들 때 사용된 사양에 따라 숫자 값의 시퀀스를 생성하는 사용자 정의 스키마 바운드 개체입니다. 숫자 값의 시퀀스는 정의된 간격에 따라 오름차순이나 내림차순으로 생성되며, 시퀀스가 모두 사용되면 다시 시작(순환)되도록 구성할 수 있습니다. ID 열과 달리 시퀀스는 특정 테이블과 연결되지 않습니다. 응용 프로그램에서는 시퀀스 개체를 참조하여 다음 값을 검색합니다. 시퀀스와 테이블 간의 관계는 응용 프로그램에서 제어합니다. 사용자 응용 프로그램에서는 시퀀스 개체를 참조하고 여러 행 및 테이블에서 값을 조정합니다.  
  
 행을 삽입할 때 생성되는 ID 열 값과는 달리 응용 프로그램에서는 [NEXT VALUE FOR function](../../t-sql/functions/next-value-for-transact-sql.md)을 호출하여 행을 삽입하지 않고도 다음 시퀀스 번호를 가져올 수 있습니다. 여러 시퀀스 번호를 한 번에 가져오려면 [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md) 를 사용합니다.  
  
 **CREATE SEQUENCE** 및 **NEXT VALUE FOR** 함수를 함께 사용하는 시나리오에 대한 자세한 내용은 [시퀀스 번호](../../relational-databases/sequence-numbers/sequence-numbers.md)를 참조하세요.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
CREATE SEQUENCE [schema_name . ] sequence_name  
    [ AS [ built_in_integer_type | user-defined_integer_type ] ]  
    [ START WITH <constant> ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE [ <constant> ] } | { NO MINVALUE } ]  
    [ { MAXVALUE [ <constant> ] } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>인수  
 *sequence_name*  
 데이터베이스에서 시퀀스를 식별하는 고유 이름을 지정합니다. 형식은 **sysname**입니다.  
  
 [ built_in_integer_type | user-defined_integer_type  
 시퀀스는 모든 정수 유형으로 정의할 수 있습니다. 다음 형식이 허용됩니다.  
  
-   **tinyint** - 0에서 255 사이의 범위  
  
-   **smallint** - -32,767에서 32,768 사이의 범위  
  
-   **int** - -2,147,483,648에서 2,147,483,647 사이의 범위  
  
-   **bigint** - -9,223,372,036,854,775,808에서 9,223,372,036,854,775,807 사이의 범위  
  
-   소수 자릿수가 0인 **decimal** 또는 **numeric**.  
  
-   허용되는 형식 중 하나에 기반을 둔 사용자 정의 데이터 형식(별칭 유형)  
  
 데이터 형식을 제공하지 않은 경우 **bigint** 데이터 형식이 기본값으로 사용됩니다.  
  
 START WITH \<constant>  
 시퀀스 개체가 반환하는 첫 번째 값입니다. **START** 값은 시퀀스 개체의 최대값보다 작거나 같고 최소값보다 크거나 같은 값이어야 합니다. 새 시퀀스 개체의 기본 시작 값은 오름차순 시퀀스 개체에 대해서는 최소값이고, 내림차순 시퀀스 개체에 대해서는 최대값입니다.  
  
 INCREMENT BY \<constant>  
 각각의 **NEXT VALUE FOR** 함수 호출에 대해 시퀀스 개체의 값을 증가시키거나 감소시키는(음수인 경우) 데 사용되는 값입니다. 증가값이 음수이면 시퀀스 개체가 내림차순이고, 그렇지 않으면 오름차순입니다. 증가값은 0일 수 없습니다. 새 시퀀스 개체의 기본 증가분은 1입니다.  
  
 [ MINVALUE \<constant> | **NO MINVALUE** ]  
 시퀀스 개체의 경계를 지정합니다. 새 시퀀스 개체의 기본 최소값은 해당 시퀀스 개체의 데이터 형식에 대한 최소값입니다. **tinyint** 형식에 대해서는 0이고 다른 모든 데이터 형식에 대해서는 음수입니다.  
  
 [ MAXVALUE \<constant> | **NO MAXVALUE**  
 시퀀스 개체의 경계를 지정합니다. 새 시퀀스 개체의 기본 최대값은 해당 시퀀스 개체의 데이터 형식에 대한 최대값입니다.  
  
 [ CYCLE | **NO CYCLE** ]  
 시퀀스 개체를 최소값 또는 최대값(내림차순 시퀀스 개체의 경우)에서 다시 시작해야 하는지, 아니면 최소값 또는 최대값을 초과하는 경우 예외를 발생시켜야 하는지를 지정하는 속성입니다. 새 시퀀스 개체의 기본 순환 옵션은 NO CYCLE입니다.  
  
 시작 값이 아니라 최소값 또는 최대값에서 순환이 다시 시작됩니다.  
  
 [ **CACHE** [\<constant> ] | NO CACHE ]  
 시스템 번호를 생성하는 데 필요한 디스크 IO 수를 최소화하여 시퀀스 개체를 사용하는 응용 프로그램의 성능을 향상시킵니다. 기본값으로 CACHE가 됩니다.  
  
 예를 들어 캐시 크기 50을 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 50개의 개별 값을 캐시된 상태로 유지하지 않습니다. 현재 값 및 캐시에 남아 있는 값의 개수만 캐시합니다. 따라서 캐시 저장에 필요한 메모리 양은 항상 시퀀스 개체 데이터 형식의 인스턴스 두 개입니다.  
  
> [!NOTE]  
>  캐시 크기를 지정하지 않고 캐시 옵션을 설정하면 데이터베이스 엔진에서 크기를 선택합니다. 그러나 선택의 일관성이 보장되지 않습니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] 는 캐시 크기 계산 방법을 예고 없이 변경할 수 있습니다.  
  
 **CACHE** 옵션을 사용하여 만들 경우 전원 오류와 같은 예기치 않은 종료로 인해 캐시에 남아 있는 시퀀스 번호가 손실될 수 있습니다.  
  
## <a name="general-remarks"></a>일반적인 주의 사항  
 시퀀스 번호는 현재 트랜잭션 범위 외부에서 생성되며, 시퀀스 번호를 사용하는 트랜잭션이 커밋되는지 또는 롤백되는지 여부에 관계없이 사용됩니다.  
  
### <a name="cache-management"></a>캐시 관리  
 성능 향상을 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 **CACHE** 인수로 지정된 수의 시퀀스 번호를 미리 할당합니다.  
  
 예를 들어 시작 값이 1이고 캐시 크기가 15인 새 시퀀스가 만들어집니다. 첫 번째 값이 필요한 경우 1에서 15 사이의 값을 메모리에서 사용할 수 있습니다. 마지막으로 캐시된 값(15)은 디스크의 시스템 테이블에 기록됩니다. 15개 번호를 모두 사용한 경우 다음 요청(16번) 시 캐시가 다시 할당됩니다. 마지막으로 캐시된 새 값(30)은 시스템 테이블에 기록됩니다.  
  
 22개 번호를 사용한 후에 [!INCLUDE[ssDE](../../includes/ssde-md.md)]이 중지된 경우 이전에 저장된 번호 대신 메모리에서 다음에 예정된 시퀀스 번호(23)가 시스템 테이블에 기록됩니다.  
  
 SQL Server를 다시 시작한 후 시퀀스 번호가 필요하면 시스템 테이블에서 시작 번호(23)를 읽습니다. 15개 번호(23-38)의 캐시 양이 메모리에 할당되고 캐시되지 않은 다음 번호(39)가 시스템 테이블에 기록됩니다.  
  
 전원 오류와 같은 상황에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]이 비정상적으로 중지된 경우에는 시스템 테이블에서 읽은 번호(39)로 시퀀스가 다시 시작됩니다. 메모리에 할당되었지만 사용자 또는 응용 프로그램에서 요청한 적이 없는 시퀀스 번호는 모두 손실됩니다. 이 기능은 간격이 생길 수는 있지만 단일 시퀀스 개체가 **CYCLE**로 정의되거나 수동으로 다시 시작되지 않은 경우 해당 개체에 대해 같은 값이 두 번 발생하지 않도록 합니다.  
  
 캐시는 현재 값(마지막으로 발생한 값) 및 캐시에 남아 있는 값의 개수에 대한 추적을 통해 메모리에서 유지 관리됩니다. 따라서 캐시에서 사용하는 메모리 양은 항상 시퀀스 개체 데이터 형식의 인스턴스 두 개입니다.  
  
 캐시 인수를 **NO CACHE**로 설정하면 시퀀스가 사용될 때마다 현재 시퀀스 값이 시스템 테이블에 기록됩니다. 이로 인해 디스크 액세스가 증가하여 성능이 저하될 수는 있지만 의도하지 않은 간격이 발생할 수 있는 가능성은 줄어듭니다. **NEXT VALUE FOR** 또는 **sp_sequence_get_range** 함수를 사용하여 번호를 요청한 경우에도 간격이 발생할 수 있지만 이 경우에는 번호가 사용되지 않거나 커밋되지 않은 트랜잭션에 사용됩니다.  
  
 시퀀스 개체에서 **CACHE** 옵션을 사용하는 경우 해당 시퀀스 개체를 다시 시작하거나 **INCREMENT**, **CYCLE**, **MINVALUE**, **MAXVALUE** 또는 캐시 크기 속성을 변경하면 변경 내용이 적용되기 전에 캐시가 시스템 테이블에 기록됩니다. 그런 다음 건너뛰는 번호 없이 현재 값부터 캐시가 다시 로드됩니다. 캐시 크기 변경은 즉시 적용됩니다.  
  
 **캐시된 값을 사용할 수 있는 경우의 CACHE 옵션**  
  
 다음 프로세스는 시퀀스 개체에 대한 메모리 내 캐시에 사용하지 않은 값이 있는 경우 **CACHE** 옵션의 다음 값을 생성하도록 시퀀스 개체를 요청할 때마다 발생합니다.  
  
1.  시퀀스 개체의 다음 값이 계산됩니다.  
  
2.  시퀀스 개체의 새로운 현재 값이 메모리 내에서 업데이트됩니다.  
  
3.  문 호출 시 계산된 값이 반환됩니다.  
  
 **캐시가 모두 사용된 경우의 CACHE 옵션**  
  
 다음 프로세스는 캐시가 모두 사용된 경우 **CACHE** 옵션의 다음 값을 생성하도록 시퀀스 개체를 요청할 때마다 발생합니다.  
  
1.  시퀀스 개체의 다음 값이 계산됩니다.  
  
2.  새 캐시의 마지막 값이 계산됩니다.  
  
3.  시퀀스 개체에 대한 시스템 테이블 행이 잠기고, 2단계에서 계산된 값(마지막 값)이 시스템 테이블에 기록됩니다. 유지되는 새 값을 사용자에게 알리기 위해 캐시가 모두 사용된 xevent가 실행됩니다.  
  
 **NO CACHE 옵션**  
  
 다음 프로세스는 **NO CACHE** 옵션의 다음 값을 생성하도록 시퀀스 개체를 요청할 때마다 발생합니다.  
  
1.  시퀀스 개체의 다음 값이 계산됩니다.  
  
2.  시퀀스 개체의 새로운 현재 값이 시스템 테이블에 기록됩니다.  
  
3.  문 호출 시 계산된 값이 반환됩니다.  
  
## <a name="metadata"></a>메타데이터  
 시퀀스에 대한 자세한 내용을 보려면 [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)를 쿼리하십시오.  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>Permissions  
 SCHEMA에 대한 **CREATE SEQUENCE**, **ALTER**또는 **CONTROL** 권한이 필요합니다.  
  
-   db_owner 및 db_ddladmin 고정 데이터베이스 역할의 멤버는 시퀀스 개체를 생성, 변경 및 삭제할 수 있습니다.  
  
-   db_owner 및 db_datawriter 고정 데이터베이스 역할의 멤버는 번호를 생성하도록 하여 시퀀스 개체를 업데이트할 수 있습니다.  
  
 다음 예에서는 사용자 AdventureWorks\Larry에 대해 테스트 스키마의 시퀀스를 만들 수 있는 권한을 부여합니다.  
  
```  
GRANT CREATE SEQUENCE ON SCHEMA::Test TO [AdventureWorks\Larry]  
```  
  
 **ALTER AUTHORIZATION** 문을 사용하여 시퀀스 개체의 소유권을 이전할 수 있습니다.  
  
 시퀀스에서 사용자 정의 데이터 형식을 사용하는 경우에는 시퀀스 작성자에게 해당 형식에 대한 REFERENCES 권한이 있어야 합니다.  
  
### <a name="audit"></a>감사  
 **CREATE SEQUENCE**를 감사하려면 **SCHEMA_OBJECT_CHANGE_GROUP**을 모니터링합니다.  
  
## <a name="examples"></a>예  
 시퀀스를 만들고 **NEXT VALUE FOR**함수를 사용하여 시퀀스 번호를 생성하는 방법에 대한 예는 [시퀀스 번호](../../relational-databases/sequence-numbers/sequence-numbers.md)을 참조하세요.  
  
 다음 예에서는 대부분 테스트라는 스키마의 시퀀스 개체를 만듭니다.  
  
 테스트 스키마를 만들려면 다음 명령문을 실행합니다.  
  
```  
CREATE SCHEMA Test ;  
GO  
```  
  
### <a name="a-creating-a-sequence-that-increases-by-1"></a>1. 1씩 증가하는 시퀀스 만들기  
 다음 예에서는 Thierry라는 사용자가 사용할 때마다 1씩 증가하는 CountBy1이라는 시퀀스를 만듭니다.  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="b-creating-a-sequence-that-decreases-by-1"></a>2. 1씩 감소하는 시퀀스 만들기  
 다음 예에서는 0부터 시작하여 사용할 때마다 1씩 음수를 계산합니다.  
  
```  
CREATE SEQUENCE Test.CountByNeg1  
    START WITH 0  
    INCREMENT BY -1 ;  
GO  
```  
  
### <a name="c-creating-a-sequence-that-increases-by-5"></a>3. 5씩 증가하는 시퀀스 만들기  
 다음 예에서는 사용할 때마다 5씩 증가하는 시퀀스를 만듭니다.  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 5  
    INCREMENT BY 5 ;  
GO  
```  
  
### <a name="d-creating-a-sequence-that-starts-with-a-designated-number"></a>4. 지정된 번호에서 시작하는 시퀀스 만들기  
 Thierry는 테이블을 가져온 후 지금까지 사용된 가장 높은 ID 번호가 24,328임을 알게 됩니다. Thierry에게는 24,329부터 번호를 생성하는 시퀀스가 필요합니다. 다음 코드에서는 24,329부터 시작하여 1씩 증가하는 시퀀스를 만듭니다.  
  
```  
CREATE SEQUENCE Test.ID_Seq  
    START WITH 24329  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="e-creating-a-sequence-using-default-values"></a>5. 기본값을 사용하여 시퀀스 만들기  
 다음 예에서는 기본값을 사용하여 시퀀스를 만듭니다.  
  
```  
CREATE SEQUENCE Test.TestSequence ;  
```  
  
 시퀀스 속성을 보려면 다음 문을 실행합니다.  
  
```  
SELECT * FROM sys.sequences WHERE name = 'TestSequence' ;  
```  
  
 출력의 목록 일부는 기본값을 나타냅니다.  
  
|||  
|-|-|  
|`start_value`|`-9223372036854775808`|  
|`increment`|`1`|  
|`mimimum_value`|`-9223372036854775808`|  
|`maximum_value`|`9223372036854775807`|  
|`is_cycling`|`0`|  
|`is_cached`|`1`|  
|`current_value`|`-9223372036854775808`|  
  
### <a name="f-creating-a-sequence-with-a-specific-data-type"></a>6. 지정한 데이터 형식으로 시퀀스 만들기  
 다음 예에서는 **smallint** 데이터 형식을 사용하여 -32,768부터 32,767까지의 시퀀스를 만듭니다.  
  
```  
CREATE SEQUENCE SmallSeq  
    AS smallint ;  
```  
  
### <a name="g-creating-a-sequence-using-all-arguments"></a>7. 모든 인수를 사용하여 시퀀스 만들기  
 다음 예에서는 **decimal** 데이터 형식을 사용하여 0부터 255 사이 범위의 DecSeq라는 시퀀스를 만듭니다. 시퀀스는 125부터 시작하여 번호가 생성될 때마다 25씩 증가합니다. 시퀀스가 순환하도록 구성되었기 때문에 값이 최대값 200을 초과하는 경우 최소값 100에서 시퀀스가 다시 시작됩니다.  
  
```  
CREATE SEQUENCE Test.DecSeq  
    AS decimal(3,0)   
    START WITH 125  
    INCREMENT BY 25  
    MINVALUE 100  
    MAXVALUE 200  
    CYCLE  
    CACHE 3  
;  
```  
  
 첫 번째 값(`START WITH` 옵션 125)을 보려면 다음 문을 실행합니다.  
  
```  
SELECT NEXT VALUE FOR Test.DecSeq;  
```  
  
 150, 175 및 200을 반환하려면 문을 세 번 더 실행합니다.  
  
 시작 값이 `MINVALUE` 옵션 100으로 다시 순환되는 방식을 보려면 문을 다시 실행합니다.  
  
 캐시 크기를 확인하고 현재 값을 보려면 다음 코드를 실행합니다.  
  
```  
SELECT cache_size, current_value   
FROM sys.sequences  
WHERE name = 'DecSeq' ;  
```  
  
## <a name="see-also"></a>참고 항목  
 [ALTER SEQUENCE&#40;Transact-SQL&#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [NEXT VALUE FOR &#40;Transact-SQL&#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [시퀀스 번호](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
