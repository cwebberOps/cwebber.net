---
layout: post
title: "Configuring Envoy to Use SSL/TLS with the v2 API"
date: 2018-03-01 13:30:27 -0800
comments: true
categories: 
---

I have been doing a bit of playing with the [Envoy Proxy](https://envoyproxy.io) this week. One of the things I ran into that has been painful was configuring a listener to use SSL/TLS. Below is some sample config to make it easier for the next person to dig out the config necessary to make it happen.

```
static_resources:
  listeners:
  - address:
      socket_address:
        address: 0.0.0.0
        port_value: 443
    filter_chains:
      tls_context:
        common_tls_context:
          tls_certificates:
          - certificate_chain:
              filename: "/etc/envoy/frontend-certs/service.crt"
            private_key:
              filename: "/etc/envoy/frontend-certs/service.key"
      filters:
      - name: envoy.http_connection_manager
        config:
          tracing:
            operation_name: egress
          access_log:
          - name: envoy.file_access_log
            config:
              path: "/dev/stdout"
          codec_type: auto
          stat_prefix: ingress_http
          route_config:
			(...)
```