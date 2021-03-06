---
title: TRANSACT-SQL을 사용 하 여 SQL Server 데이터 풀에 데이터를 수집 하는 방법 | Microsoft Docs
description: 이 자습서에는 sp_data_pool_table_insert_data 저장 프로시저를 사용 하 여 SQL Server 2019 빅 데이터 클러스터 (미리 보기)의 데이터 풀에 데이터를 수집 하는 방법을 보여 줍니다.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 1f585a354175ff893869cef7f2f47b12fe244634
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221699"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>자습서: TRANSACT-SQL을 사용 하 여 SQL Server 데이터 풀에 데이터 수집

이 자습서에서는 TRANSACT-SQL을 사용 하 여 데이터를 로드 하는 방법을 설명 합니다 [데이터 풀](concept-data-pool.md) SQL Server 2019 빅 데이터 클러스터 (미리 보기)의 합니다. SQL Server 빅 데이터 클러스터를 사용 하 여에 다양 한 원본에서에서 데이터를 수집 하 고 데이터 풀 인스턴스 간에 분산 될 수 있습니다.

이 자습서에 알아봅니다 방법:

> [!div class="checklist"]
> * 데이터 풀에서 외부 테이블을 만듭니다.
> * 샘플 웹 클릭 동향 데이터 데이터 풀 테이블에 삽입 합니다.
> * 로컬 테이블을 사용 하 여 데이터 풀 테이블에서 데이터를 조인 합니다.

> [!TIP]
> 원한다 면 다운로드 하 고이 자습서의 명령에 대 한 스크립트를 실행할 수 있습니다. 지침은 합니다 [데이터 샘플 풀](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) github입니다.

## <a id="prereqs"></a> 사전 요구 사항

* [Kubernetes에서 빅 데이터 클러스터를 배포](deployment-guidance.md)합니다.
* [Azure Data Studio 및 SQL Server 2019 확장 설치](deploy-big-data-tools.md)합니다.
* [클러스터에 샘플 데이터 로드](#sampledata)합니다.

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-in-the-data-pool"></a>데이터 풀에서 외부 테이블 만들기

다음 단계에서는 명명 된 데이터 풀의 외부 테이블을 만듭니다 **web_clickstream_clicks_data_pool**합니다. 이 표에서 사용할 수 있습니다 다음 위치로 데이터를 수집 하는 방법에 대 한 빅 데이터 클러스터에.

1. Azure Data Studio, 빅 데이터 클러스터의 마스터 SQL Server 인스턴스에 연결 합니다. 자세한 내용은 [SQL Server 마스터 인스턴스에 연결할](deploy-big-data-tools.md#master)합니다.

1. 연결을 두 번 클릭 합니다 **서버** 창 마스터 SQL Server 인스턴스에 대 한 서버 대시보드를 표시 합니다. 선택 **새 쿼리**합니다.

   ![SQL Server 마스터 인스턴스 쿼리](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. 컨텍스트를 변경 하려면 다음 TRANSACT-SQL 명령을 실행 합니다 **Sales** 마스터 인스턴스에 있는 데이터베이스입니다.

   ```sql
   USE Sales
   GO
   ```

1. 명명 된 외부 테이블을 만듭니다 **web_clickstream_clicks_data_pool** 데이터 풀에 있습니다. `SqlDataPool` 데이터 원본은 모든 빅 데이터 클러스터의 마스터 인스턴스를 사용할 수 있는 특수 데이터 원본 형식입니다.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstream_clicks_data_pool')
      CREATE EXTERNAL TABLE [web_clickstream_clicks_data_pool]
      ("wcs_user_sk" BIGINT , "i_category_id" BIGINT , "clicks" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. CTP 2.1에서 데이터 풀을 만드는 비동기 되었지만 아직 완료 될 때 확인 방법이 있습니다. 계속 하기 전에 데이터 풀 생성 되도록 하려면 2 분을 기다립니다.

## <a name="load-data"></a>데이터 로드

다음 단계를 이전 단계에서 만든 외부 테이블을 사용 하 여 데이터 풀에 샘플 웹 클릭 동향 데이터를 수집 합니다.

1. 변수 데이터 풀에 데이터를 삽입 하려면 사용 하려는 쿼리를 정의 합니다. 사용 하 여는 **모델... sp_data_pool_table_insert_data** 저장 프로시저를 쿼리에서 결과 데이터 풀 삽입할 (합니다 **web_clickstream_clicks_data_pool** 외부 테이블).

   ```sql
   DECLARE @db_name SYSNAME = 'Sales'
   DECLARE @schema_name SYSNAME = 'dbo'
   DECLARE @table_name SYSNAME = 'web_clickstream_clicks_data_pool'
   DECLARE @query NVARCHAR(MAX) = '
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
   FROM sales.dbo.web_clickstreams
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
      AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;'

   EXEC model..sp_data_pool_table_insert_data @db_name, @schema_name, @table_name, @query
   ```

1. 두 개의 SELECT 쿼리를 사용 하 여 삽입된 된 데이터를 검사 합니다.

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>데이터를 쿼리 합니다.

쿼리에서 데이터 풀에서 로컬 데이터를 사용 하 여 저장 된 결과 조인 합니다 **Sales** 테이블입니다.

```sql
SELECT TOP (100)
   w.wcs_user_sk,
   SUM( CASE WHEN i.i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
   SUM( CASE WHEN w.i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
   SUM( CASE WHEN w.i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
   SUM( CASE WHEN w.i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
   SUM( CASE WHEN w.i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
   SUM( CASE WHEN w.i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
   SUM( CASE WHEN w.i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
   SUM( CASE WHEN w.i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
   SUM( CASE WHEN w.i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
   SUM( CASE WHEN w.i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
FROM [dbo].[web_clickstream_clicks_data_pool] as w
INNER JOIN (SELECT DISTINCT i_category_id, i_category FROM item) as i
   ON i.i_category_id = w.i_category_id
GROUP BY w.wcs_user_sk;
```

## <a name="clean-up"></a>정리

이 자습서에서 만든 데이터베이스 개체를 제거 하려면 다음 명령을 사용 합니다.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>다음 단계

Spark 작업을 사용 하 여 데이터 풀에 데이터를 수집 하는 방법에 알아봅니다.
> [!div class="nextstepaction"]
> [Spark 작업을 사용 하 여 데이터를 수집 합니다.](tutorial-data-pool-ingest-spark.md)
