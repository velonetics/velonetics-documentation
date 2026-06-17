---
lastmod: 2016-10-28
old_version: true
date: 2016-10-28
linktitle: Running Velonetics
title: Running Velonetics server
description: Using Velonetics command
weight: 30
notoc: true
menu:
  community_v2.0:
    parent: "000 Getting Started"
---

After installing Velonetics, you can start using Velonetics by typing `velonetics`. To see all the options of `velonetics`, type `velonetics -h` or `velonetics <COMMAND> -h`. For instance, the `velonetics run` help is:

{{< terminal title="Run command help" >}}
velonetics run -h

{{< ascii-logo >}}

Version: v2.0

The API Gateway builder

Usage:
  velonetics [command]

Available Commands:
  check         Validates that the configuration file is valid.
  check-plugin  Check the compatibility with the plugin deps.
  help          Help about any command
  run           Run the Velonetics server.

Flags:
  -c, --config string   Path to the configuration filename
  -d, --debug           Enable the debug
  -h, --help            help for velonetics

Use "velonetics [command] --help" for more information about a command.
{{< /terminal >}}


To start the server, invoke the `velonetics run` command. The command will require a configuration file with your API definition. You can create your first `velonetics.json` file using the [Veloneticsesigner](https://designer.velonetics.io/) if you prefer a UI.

To get started right away, you can paste the following content inside a `velonetics.json` file:

{{< highlight json >}}
{
    "$schema": "https://www.velonetics.io/schema/v3.json",
    "version": 3
}
{{< /highlight >}}

And then you can start Velonetics:

{{< terminal title="Command to start Velonetics" >}}
velonetics run -c velonetics.json
{{< /terminal >}}

Or if you use Docker:

{{< terminal title="Command to start Velonetics with Docker" >}}
docker run -p "8080:8080" -v $PWD:/etc/velonetics/ {{< product image >}}:v2.0 run -c /etc/velonetics/velonetics.json
{{< /terminal >}}

Now Velonetics is listening on `8080`, and you can see it working under `http://localhost:8080/__health`.
