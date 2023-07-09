# Week 2 — Distributed Tracing


## Learned about Observability and Monitoring using Honeycomb, and use of Open telemetry with honeycomb for logging snd tracing the events within application

### adding keys to gitpod env
```dockerfile
export HONEYCOMB_API_KEY="Asw-XXXXXX-XXXXXXXXX-DXefG"
gp env HONEYCOMB_API_KEY="Asw-XXXXXX-XXXXXXXXX-DXefG"
```
### adding keys to gitpod env
```dockerfile
OTEL_SERVICE_NAME: "backend-flask"
OTEL_EXPORTER_OTLP_ENDPOINT: "https://api.honeycomb.io"
OTEL_EXPORTER_OTLP_HEADERS: "x-honeycomb-team=${HONEYCOMB_API_KEY}"
```
