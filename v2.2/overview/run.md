---
lastmod: 2016-10-28
old_version: true
date: 2016-10-28
linktitle: Running Velonetics
title: Running Velonetics server
description: All options of the velonetics command to manage the service, write plugins, or get information about the installed version.
weight: 30
notoc: true
menu:
  community_v2.2:
    parent: "000 Getting Started"
---

After installing Velonetics, you can start using Velonetics by typing `velonetics`. To see all the options of `velonetics`, type `velonetics -h` or `velonetics <COMMAND> -h`. For instance, the `velonetics run` help is:

{{< terminal title="Run command help" >}}
velonetics run -h

{{< ascii-logo >}}

Version: 2.2

The API Gateway builder

Usage:
  velonetics [command]

Available Commands:
  audit         Checks the integrity of the config and returns security recommendations.
  check         Validates that the configuration file is valid.
  check-plugin  Check the compatibility with the plugin deps.
  help          Help about any command
  run           Run the Velonetics server.
  version       Shows Velonetics version.

Flags:
  -c, --config string   Path to the configuration filename
  -d, --debug           Enable the debug
  -h, --help            help for velonetics

Use "velonetics [command] --help" for more information about a command.
{{< /terminal >}}

You can use the following commands:

- `velonetics audit`: Use [velonetics audit](/docs/v2.2/configuration/audit/) to get security recommendations for a given configuration.
- `velonetics check`: Use [velonetics check](/docs/v2.2/configuration/structure/) to make sure the configuration file you have generated is not broken and has the required attributes to start the gateway.
- `velonetics check-plugin`: Use the [check-plugin](/docs/v2.2/extending/check-plugin/) when you are developing custom plugins and you want to check that they are compatible with the server.
- `velonetics run`: Use run to start the API gateway server.
- `velonetics version`: Use the version command to print the current Velonetics version and the Glibc and Go versions used during compilation.

## Starting the gateway server
To start the server, invoke the `velonetics run` command with a configuration file containing your API definition. You can visually create your first `velonetics.json` file using the [Veloneticsesigner](https://designer.velonetics.io/) if you prefer a UI.

Or to get started right away, you can paste the following content inside a `velonetics.json` file:

```json
{
    "$schema": "https://www.velonetics.io/schema/v2.2/velonetics.json",
    "version": 3
}
```

And then you can start Velonetics:

{{< terminal title="Command to start Velonetics" >}}
velonetics run -c velonetics.json
{{< /terminal >}}

Or if you use Docker:

{{< terminal title="Command to start Velonetics with Docker" >}}
docker run -p "8080:8080" -v $PWD:/etc/velonetics/ {{< product image >}}:2.2 run -c velonetics.json
{{< /terminal >}}

Now Velonetics is listening on `8080`, and you can see it working under `http://localhost:8080/__health`.
