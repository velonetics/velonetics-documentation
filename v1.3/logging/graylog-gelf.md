---
lastmod: 2019-09-15
old_version: true
date: 2019-09-15
notoc: true
linktitle: Graylog - GELF
title: Graylog and the GELF format
weight: 40
source: https://github.com/velonetics/velonetics-gelf
since: 0.7
menu:
  community_v1.3:
    parent: "090 Logging"
---
Velonetics supports sending structured events in GELF format to your Graylog Cluster thanks to the [velonetics-gelf](https://github.com/velonetics/velonetics-gelf) integration.

The setup of GELF is straightforward and requires only to set two parameters:

- `address`: The address (including the port) of your Graylog cluster (or any other service that receives GELF inputs).
- `enable_tcp`: Set to `false` (recommended) to use UDP. When using TCP performance might be affected.

## Enabling GELF
Add the `velonetics-gelf` integration in the root level of your `velonetics.json`, inside the `extra_config` section. **The `gologging` needs to be enabled too**.

For instance:

    "extra_config": {
      "github_com/velonetics/velonetics-ce-gelf": {
        "address": "myGraylogInstance:12201",
        "enable_tcp": false
      }
      "github_com/velonetics/velonetics-ce-gologging": {
          "level": "INFO",
          "prefix": "[VELONETICS]",
          "syslog": false,
          "stdout": true
      }
    }
