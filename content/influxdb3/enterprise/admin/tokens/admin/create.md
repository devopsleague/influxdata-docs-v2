---
title: Create an admin token
description: >
  Use the [`influxdb3 create token --admin` command](/influxdb3/enterprise/reference/cli/influxdb3/create/token/)
  or the [HTTP API](/influxdb3/enterprise/api/v3/)
  to create an [admin token](/influxdb3/enterprise/admin/tokens/admin/) for your {{< product-name omit="Clustered" >}} instance.
  An admin token grants access to all actions on the server.
menu:
  influxdb3_enterprise:
    parent: Admin tokens
weight: 201
list_code_example: |
  ##### CLI
  ```bash
  influxdb3 create token --admin 
  ```
  #### HTTP API
  ```bash
  curl -X POST "http://{{< influxdb/host >}}/api/v3/enterprise/configure/token/admin" \
    --header 'Accept: application/json' \
    --header 'Content-Type: application/json'
  ```
alt_links:
  cloud-dedicated: /influxdb3/cloud-dedicated/admin/tokens/create-token/
  cloud-serverless: /influxdb3/cloud-serverless/admin/tokens/create-token/
source: /shared/influxdb3-admin/tokens/admin/create.md
---

<!-- The content for this page is at
// SOURCE content/shared/influxdb3-admin/tokens/admin/create.md
-->