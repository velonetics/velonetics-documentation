---
lastmod: 2020-07-10
old_version: true
date: 2020-07-10
linktitle: Environment vars
since: 1.2
notoc: true
menu:
  community_v1.3:
    parent: "010 Configuration file(s)"
title: Overriding the configuration with environment vars
weight: 40
meta:
  since: v1.2
  source: false
  namespace: false
  scope:
  - service
---
When Velonetics [runs](/docs/v1.3/commands/run/), all the behavior is loaded from the [configuration file](/docs/v1.3/configuration/structure/). For each configuration value that isn't nested (meaning first-level properties of the configuration), you can override its value with an environment variable.

All configuration environment variables must have the prefix `VELONETICS_` and declared in uppercase. The variable name after the prefix must match the property in the configuration value.

For instance, take the following `velonetics.json` configuration as an example:

    {
        "version": 2,
        "timeout": "3s",
        "name": "Example gateway."
    }

Now run velonetics with the following command:

{{< terminal title="Example: Override configuration with env vars" >}}
VELONETICS_NAME="Build ABC0123" VELONETICS_TIMEOUT="500ms" velonetics run -c velonetics.json
{{< /terminal >}}

The resulting configuration will be:

    {
        "version": 2,
        "timeout": "500ms",
        "name": "Build ABC0123"
    }

**NOTE**: The configuration file is not changed. The values above are a representation of the final mapped values.
