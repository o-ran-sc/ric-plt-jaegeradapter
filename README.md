# Jaeger adapter

This repository contains jaeger configuration files, like the helm charts

## Current information

Currently only supported configuration is jaeger-all-in-one deployment.
The helm chart defines following three services.

### The jaeger agent

Jaeger agent receives trace data from jaeger client(s) with UDP to ports 5775 or 6831 or 6832.
So the jaeger pods needs to expose these ports and the jaeger agent service IP address
should be available with DNS.

With these helm charts the DNS entry will be `jaeger-all-in-one-agent`.

### the jaeger collector

Jaeger collector receives trace data from jaeger agent(s) with TCP to ports 14267 or 14268 or 9411.
Jaeger pod need to expose these ports and the collector service IP address should be available
with DNS

With these helm charts the DNS entry will be `jaeger-all-in-one-collector`.

### the jaeger query

Jaeger query implements a web service for quering trace data. It should expose a http port, for example 80.

With these helm charts the DNS entry will be `jaeger-all-in-one-query`.

## Config map

A config map for creating trace client configuration is provided. Currently it configures a disabled tracer client.
