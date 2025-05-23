---
title: Query SQL data sources
seotitle: Query SQL data sources with InfluxDB
list_title: Query SQL data
description: >
  The Flux `sql` package provides functions for working with SQL data sources.
  Use `sql.from()` to query SQL databases like PostgreSQL, MySQL, Snowflake,
  SQLite, Microsoft SQL Server, Amazon Athena, and Google BigQuery.
influxdb/cloud/tags: [query, flux, sql]
menu:
  influxdb_cloud:
    parent: Query with Flux
    list_title: SQL data
weight: 220
related:
  - /flux/v0/stdlib/sql/
list_code_example: |
  ```js
  import "sql"

  sql.from(
      driverName: "postgres",
      dataSourceName: "postgresql://user:password@localhost",
      query: "SELECT * FROM example_table",
  )
  ```
source: /shared/influxdb-v2/query-data/flux/sql.md
---

<!-- The content of this file is at 
// SOURCE content/shared/influxdb-v2/query-data/flux/sql.md-->