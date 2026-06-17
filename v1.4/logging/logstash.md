---
lastmod: 2019-09-15
old_version: true
date: 2019-09-15
notoc: true
linktitle: Logstash
title: Logstash
weight: 50
source: https://github.com/velonetics/velonetics-logstash
menu:
  community_v1.4:
    parent: "090 Logging"
---
If you want to log using the Logstash standard via stdout, you have to add the `velonetics-logstash` integration in the
root level of your `velonetics.json`, inside the `extra_config` section. **The `gologging` needs to be enabled too**.

For instance:

    "extra_config": {
      "github_com/velonetics/velonetics-ce-logstash": {
        "enabled": true
      }
      "github_com/velonetics/velonetics-ce-gologging": {
          "level": "INFO",
          "prefix": "[VELONETICS]",
          "syslog": false,
          "stdout": true,
          "format": "logstash"
      }
    }
