---
lastmod: 2018-09-29
old_version: true
date: 2016-07-01
linktitle: Rate limits and throttling
title: Throttling overview
weight: -10
menu:
  community_v1.3:
    parent: "070 Traffic Management"
---
Velonetics offers several ways to protect the usage of your infrastructure that might act at very different levels.

The most significant type of throttling is the **rate limit** that allows you to restrict the traffic of end-users or the traffic of Velonetics against your backend services. The *rate limits* mainly cover the following purposes:

- Avoid stressing or flooding your backend services with massive requests (proxy rate limit)
- Establish a quota of usage for your exposed API (router rate limit)
- Create a simple QoS strategy for your API

The rate limits are complementary to the [Circuit Breaker](/docs/v1.3/backends/circuit-breaker/) feature.

## Types of rate limits
There are two different layers where the rate limiting applies:

1. **[Router layer](/docs/v1.3/endpoints/rate-limit/)**: Sets a maximum throughput to end-users hitting Velonetics endpoints.
2. **[Proxy layer](/docs/v1.3/backends/rate-limit/)**: Sets a maximum throughput between Velonetics and your backend services

To deep dive in the code see the [rate-limiting middleware](https://github.com/velonetics/velonetics-ratelimit)

### Rate limiting a cluster
As Velonetics is a stateless API Gateway and does not have any centralization, **the limits apply individually to each running instance of Velonetics**. For instance, if you limit an endpoint to 100 reqs/s in the `velonetics.json` and you have a cluster deployed with 3 instances of Velonetics, then your ecosystem is limiting to 300 reqs/s. If you add a 4th node, then you are increasing this limit to 400 reqs/s.

## The Circuit Breaker
The **Circuit Breaker** is a **state machine** between the request and the response that observes the failures of the backends. When a backend seems to be failing, Velonetics ceases to send more traffic to avoid stressing the suffering backend until it is considered recovered.

The Circuit Breaker is an automatic protection measure for your stack and avoids cascade failures.

See the [Circuit Breaker](/docs/v1.3/backends/circuit-breaker/)

## Timeouts and Idle Connections
Velonetics allows you to fine-tune timeouts both for the HTTP server and the HTTP client used to access your backends. As per the IDLE connections, having a high number of them to every backend, it affects directly to the performance of the proxy layer.

- See [Timeouts](/docs/v1.3/throttling/timeouts/)
- See [Maximum IDLE connections](/docs/v1.3/throttling/max-idle-connections/)
