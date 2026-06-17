---
lastmod: 2018-09-27
old_version: true
canonical: /docs/overview/run/
date: 2016-10-25
menu:
  community_v1.4:
    parent: "000 Getting Started"
notoc: true
title: Using Velonetics
weight: 30
---

From an operations point of view Velonetics, is very simple to use. It only requires you to pass
the path the configuration file (which defines behaviors and endpoints). Additionally, you can
enable the debug with the `-d` flag, and that's pretty much everything.

## TL;DR
1. Generate a configuration file with your endpoints definition. The easier way to generate it is using the [designer](https://designer.velonetics.io/)
2. Check the syntax of your `velonetics.json` is good
	{{< terminal title="Syntax checking" >}}
velonetics check --config velonetics.json --debug
	{{< /terminal >}}
3. Run Velonetics
	{{< terminal title="Start the server" >}}
velonetics run -c velonetics.json -d
	{{< /terminal >}}


The flag `-c` is the short version of `--config` and `-d` the short version of `--debug` which allows
you to find problems easily.


## Using Velonetics

To start Velonetics make sure to provide the path to the binary or add it to the `PATH`. You can see all
Velonetics options by running the binary with no options:

{{< terminal title="The velonetics command" >}}
velonetics

`7MMF' `YMM'                  `7MM                         `7MM"""Yb.
  MM   .M'                      MM                           MM    `Yb.
  MM .d"     `7Mb,od8 ,6"Yb.    MM  ,MP'.gP"Ya `7MMpMMMb.    MM     `Mb
  MMMMM.       MM' "'8)   MM    MM ;Y  ,M'   Yb  MM    MM    MM      MM
  MM  VMA      MM     ,pm9MM    MM;Mm  8M""""""  MM    MM    MM     ,MP
  MM   `MM.    MM    8M   MM    MM `Mb.YM.    ,  MM    MM    MM    ,dP'
.JMML.   MMb..JMML.  `Moo9^Yo..JMML. YA.`Mbmmd'.JMML  JMML..JMMmmmdP'
_______________________________________________________________________

Version: 1.4.1

The API Gateway builder

Usage:
  velonetics [command]

Available Commands:
  check       Validates that the configuration file is valid.
  help        Help about any command
  run         Run the Velonetics server.

Flags:
  -c, --config string   Path to the configuration filename
  -d, --debug           Enable the debug
  -h, --help            help for velonetics

Use "velonetics [command] --help" for more information about a command.
{{< /terminal >}}

As you can see there are 3 different supported commands:

- [`velonetics check`](/docs/v1.4/commands/check/) (syntax validation)
- [`velonetics run`](/docs/v1.4/commands/run/) (run the server)
- `velonetics help` (show usage)
