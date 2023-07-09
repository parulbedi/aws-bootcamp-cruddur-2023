# Week 2 — Distributed Tracing


## Learned about Observability and Monitoring using Honeycomb, and use of Open telemetry with honeycomb for logging snd tracing the events within application

### add the following in backend-flask --> requirements.txt file to install required libraries to work with Open telemetry
```dockerfile
opentelemetry-api 
opentelemetry-sdk 
opentelemetry-exporter-otlp-proto-http 
opentelemetry-instrumentation-flask 
opentelemetry-instrumentation-requests
```

### adding keys to gitpod env
```dockerfile
export HONEYCOMB_API_KEY="Asw-XXXXXX-XXXXXXXXX-DXefG"
gp env HONEYCOMB_API_KEY="Asw-XXXXXX-XXXXXXXXX-DXefG"
```
### add the following in docker-compose.yml under backend-flask
```dockercompose
OTEL_SERVICE_NAME: "backend-flask"
OTEL_EXPORTER_OTLP_ENDPOINT: "https://api.honeycomb.io"
OTEL_EXPORTER_OTLP_HEADERS: "x-honeycomb-team=${HONEYCOMB_API_KEY}"
```

### Add the following snippet of code in app.py under backend-flask
```python
from opentelemetry import trace
from opentelemetry.instrumentation.flask import FlaskInstrumentor
from opentelemetry.instrumentation.requests import RequestsInstrumentor
from opentelemetry.exporter.otlp.proto.http.trace_exporter import OTLPSpanExporter
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import BatchSpanProcessor
```

### Itialize the tracing , then this will send the data to Honeycomb
```python
provider = TracerProvider()
processor = BatchSpanProcessor(OTLPSpanExporter())
provider.add_span_processor(processor)
trace.set_tracer_provider(provider)
tracer = trace.get_tracer(__name__)
```
