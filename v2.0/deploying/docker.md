---
lastmod: 2021-12-07
old_version: true
date: 2021-12-07
linktitle: Docker artifact
title: Generating a Docker artifact
notoc: true
menu:
  community_v2.0:
    parent: "110 Deployment and Go-Live"
weight: 20
---
If you use containers, the recommended approach is to write your own `Dockerfile` and deploy an **immutable artifact** (embedding the config).

In its simplified form would be:
{{< highlight Dockerfile >}}
FROM {{< product image >}}:v2.0
COPY velonetics.json /etc/velonetics/velonetics.json
# Uncomment with Enterprise image:
# COPY LICENSE /etc/velonetics/LICENSE
{{< /highlight >}}

{{< note title="Volume or copy?" type="question" >}}
Even though you can use the official container directly and attach the configuration mounting an external volume (or ConfigMap in Kubernetes), a custom image with your configuration copied inside has benefits. It guarantees that you can do safe rollbacks and have effective testing and debugging. If you break something at any point, you only need to deploy the previous container, while if you use a volume, you are exposed to downtime or impossible scaling until you fix it.
{{< /note >}}

A more real-life example illustrates below a combination of the `check` command with a multi-stage build to compile a [flexible configuration](/docs/v2.0/configuration/flexible-config/) in a `Dockerfile`:

{{< highlight docker >}}
FROM {{< product image >}}:v2.0 as builder
ARG ENV=prod

COPY velonetics.tmpl .
COPY config .

## Save temporary file to /tmp to avoid permission errors
RUN FC_ENABLE=1 \
    FC_OUT=/tmp/velonetics.json \
    FC_PARTIALS="/etc/velonetics/partials" \
    FC_SETTINGS="/etc/velonetics/settings/$ENV" \
    FC_TEMPLATES="/etc/velonetics/templates" \
    velonetics check -d -t -c velonetics.tmpl

# The linting needs the final velonetics.json file
RUN velonetics check -c /tmp/velonetics.json --lint

FROM {{< product image >}}:v2.0
COPY --from=builder --chown=velonetics:nogroup /tmp/velonetics.json .
# Uncomment with Enterprise image:
# COPY LICENSE /etc/velonetics/LICENSE
{{< /highlight >}}

The `Dockerfile` above has two stages:
 The `check` command compiles the template `velonetics.tmpl` and any included sub-template inside and outputs (`FC_OUT`) the resulting `/tmp/velonetics.json` file.
The `velonetics.json` file is the only addition to the final Docker image.

The example above assumes you have a file structure like this:

    .
    ├── config
    │   ├── partials
    │   ├── settings
    │   │   ├── prod
    │   │   │   └── env.json
    │   │   └── test
    │   │       └── env.json
    │   └── templates
    │       └── some.tmpl
    ├── Dockerfile
    └── velonetics.tmpl

Generate the skeleton above with:
{{< highlight bash >}}
mkdir -p config/{partials,settings,templates}
mkdir -p config/settings/{prod,test}
touch Dockerfile velonetics.tmpl
{{< /highlight >}}

Now the only missing step to generate the image, is to build it, making sure that the environment argument matches our folder inside the `settings` folder:

{{< terminal title="Docker build" >}}
docker build --build-arg ENV=prod -t myvelonetics .
{{< /terminal >}}

The resulting image, including your configuration, weighs around `80MB`.