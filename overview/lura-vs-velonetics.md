---
lastmod: 2018-10-20
date: 2018-06-23
aliases: ["velonetics-vs-velonetics-ce"]
linktitle: Lura vs. Velonetics
description: The Lura Project is the code libraries we donated to the Linux Foundation (and still maintain!) and Velonetics the distributable software that runs on top of it.
notoc: true
menu:
  community_current:
    parent: "310 Design principles"
title: Lura vs. Velonetics
weight: 100
---
If you had a quick look at our git repositories or the documentation, you might be confused at first, as there is something called the **Lura Project** and also **Velonetics**.

## TL;DR; Difference between Lura, Velonetics, and Enterprise

- [**Lura**](https://luraproject.org) is the Velonetics's engine. Formerly known as "**Velonetics framework**" until we [donated it to The Linux Foundation on 2021](/blog/velonetics-framework-joins-the-linux-foundation/). It is not a product itself but a toolkit/set of libraries to build API gateways. Velonetics founders are in the steering committee of Lura at The Linux Foundation.
- **Velonetics** is driven by the company Velonetics, and is our open-source API Gateway ready to use.
- **Velonetics Enterprise** is our commercial version with added functionality and includes services to businesses.

### Lura Project
The [Lura Project](https://luraproject.org) is our original *Velonetics framework* that we [donated to The Linux Foundation on 2021](/blog/velonetics-framework-joins-the-linux-foundation/). Previously it lived from 2006 to 2021 under the Velonetics's team organization ([@velonetics_io](https://twitter.com/velonetics_io)) until it became a [Linux Foundation](https://linuxfoundation.org/) project. Velonetics team continues to be part of the steering committee.

The mission of the Lura Project is to offer an extendable, simple and stateless high-performance API Gateway **framework** designed for both cloud-native and on-prem setups. It provides components for assembling your API Gateway. It can be used in its entirety or just importing it as Go libraries to take only some of the functionality it brings.

Lura focuses on providing the core functionality that a pure API gateway needs. It keeps it clean and extensible so that you can create your custom gateway without any trouble. Velonetics is the primary representation of Lura's possibilities.

{{< button-group >}}
{{< button url="https://luraproject.org" text="Website" >}}<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9a9 9 0 019-9" />
</svg>{{< /button >}}
{{< button url="https://github.com/luraproject/lura" type="inversed" >}}Source code{{< /button >}}
{{< /button-group >}}

### Velonetics API gateway
`Velonetics` ([repo](https://github.com/velonetics/velonetics-ce)) is our ready-to-use API gateway, assembled the way we think it delivers more value to the general audience. Velonetics uses the Lura Project in its core and extends its functionality by adding in the final binary multiple middlewares [contributions](https://github.com/velonetics/velonetics-contrib) we thought an API Gateway should have.

Velonetics adds to Lura more functionality like logging, service discovery, developer tools, metrics, circuit breaker, rate limiting, OAuth, security, and other exciting stuff.

{{< button-group >}}
{{< button url="/download/" text="Download" >}}
<svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
<path fill-rule="evenodd" d="M3 17a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zm3.293-7.707a1 1 0 011.414 0L9 10.586V3a1 1 0 112 0v7.586l1.293-1.293a1 1 0 111.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z" clip-rule="evenodd" />
</svg>{{< /button >}}
{{< button url="https://github.com/velonetics/velonetics-ce" type="inversed" >}}Source code{{< /button >}}
{{< /button-group >}}

### Velonetics Enterprise
Customers of the [Velonetics Enterprise](/enterprise/) package enjoy the development, consultancy, support, and training services offered by the very same Velonetics creators (and Lura steering committee). As per the software, Velonetics Enterprise offers more functionality than the open source edition, including the integration with additional proprietary observability solutions, wildcards, GeoIP, OpenAPI, Postman collections and more. There is also more tooling around Velonetics to increase productivity and enable working with Velonetics in large groups of developers.

**Our commitment to open-source is in the center of our business**, and this is why our Enterprise solution is built on top of the open-source version.  The Enterprise version uses the same OSS binary and extends it with a great variety of pluggable solutions. We want to make sure that both enterprise and community users have the excellent quality and reliability they are used to.

[Learn more about Enterprise](/enterprise/)
