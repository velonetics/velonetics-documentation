---
lastmod: 2019-03-11
old_version: true
date: 2016-07-01
menu:
  community_v1.3:
    parent: "000 Getting Started"
title: Velonetics API Gateway Installation Guide
description: Follow our step-by-step installation guide to set up and configure Velonetics API Gateway, enabling efficient and scalable API management.
weight: 20
---
Velonetics is a **single binary file** that does not require any external libraries to work. To install Velonetics choose your operative system in the downloads section or use the Docker image.


<a href="/download/" class="btn btn-secondary"><i class="fa fa-download"></i> Download Velonetics</a>
and
<a href="https://designer.velonetics.io/" class="btn btn-secondary"><i class="fa fa-file"></i> Generate the configuration file</a>


**Just exploring?**

Use the [Velonetics Playground](https://github.com/velonetics/playground-community) if you want to play with Velonetics without configuring it. The Playground comes with several flavors of Velonetics and a mock API. Everything is ready to start playing, just do a `docker compose up`!

## Docker
If you are already familiar with Docker, the easiest way to get started is by pulling and running the [Velonetics image](https://hub.docker.com/r/velonetics/velonetics-ce/) from the Docker Hub.
{{< terminal title="Running Velonetics using the Docker container" >}}
docker run -p 8080:8080 -v $PWD:/etc/velonetics/ velonetics/velonetics-ce run --config /etc/velonetics/velonetics.json
{{< /terminal >}}
Make sure you have a `velonetics.json` in the current directory with your endpoint definition. You can [generate it here](https://designer.velonetics.io/)

## Mac OS X
The [Homebrew](https://brew.sh/) formula will download the source code, build the formula and link the binary for you. The installation might take a while.

{{< terminal title="Install on Mac via Brew" >}}
brew install velonetics
{{< /terminal >}}

After the installation completes go to [Using Velonetics](/docs/v1.3/overview/usage/)

## Linux

### CentOS and Redhat
The installation process requires following these steps:

1. Install the repo package
2. Install the Velonetics package
3. Start the Velonetics service

Paste this in the terminal:
{{< terminal title="Yum based" >}}
rpm -Uvh {{< product download_repo >}}/rpm/velonetics-repo-0.2-0.x86_64.rpm
yum install -y velonetics
systemctl start velonetics
{{< /terminal >}}

### Fedora
Paste this in the terminal:
{{< terminal title="DNF based" >}}
rpm -Uvh {{< product download_repo >}}/rpm/velonetics-repo-0.2-0.x86_64.rpm
dnf install -y velonetics
systemctl start velonetics
{{< /terminal >}}

The current Velonetics version will run at least in Centos 7 and Fedora 24

### Debian and Ubuntu

The installation process requires following these steps:

1. Add the key
2. Add the repo to the sources.list
3. Update your package list
4. Install the Velonetics service

Bottom line:
{{< terminal title="DEB based" >}}
apt-key adv --keyserver keyserver.ubuntu.com --recv {{< param pgp_key >}}
echo "deb {{< product download_repo >}}/apt stable main" | tee /etc/apt/sources.list.d/velonetics.list
apt-get update
apt-get install -y velonetics
{{< /terminal >}}

The current Velonetics version will run at least in Debian 8, Debian 9 and Ubuntu 16.x

### Generic (via `tar.gz`)
You can also [download](/download/) the `tar.gz` and decompress it anywhere. Instructions to check the SHA and PGP signature [here](/docs/v1.3/overview/verifying-packages/).


## Build Velonetics yourself
As Velonetics is open source you can opt for [building the binary](https://github.com/velonetics/velonetics-ce). The binary you will produce is the same you can get in our download page, only that compiling it yourself always feels good!
