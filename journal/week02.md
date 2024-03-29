# Week 2 — Distributed Tracing


## Learned about Observability and Monitoring using Honeycomb, and use of Open telemetry with honeycomb for logging snd tracing the events within application

### 1. Honeycomb
### I added the following in backend-flask --> requirements.txt file to install required libraries to work with Open telemetry
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

### 2. Rollbar
### I added the following in backend-flask --> requirements.txt file to install required libraries to work with Rollbar
```python
blinker
rollbar
```

### Importing rollbar in app
```python
import os
import rollbar
import rollbar.contrib.flask
from flask import got_request_exception 
```
### adding keys to gitpod env
```python
export ROLLBAR_ACCESS_TOKEN="765bb-XXXXXXX-XXXXXXXXXX-34a340a75"
gp env ROLLBAR_ACCESS_TOKEN="765bb-XXXXXXX-XXXXXXXXXX-34a340a75"
```
### Added rollbar token to docker compose
```dockerfile
  backend-flask:
    environment:
      FRONTEND_URL: "https://3000-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
      BACKEND_URL: "https://4567-${GITPOD_WORKSPACE_ID}.${GITPOD_WORKSPACE_CLUSTER_HOST}"
      OTEL_SERVICE_NAME: "backend-flask"
      OTEL_EXPORTER_OTLP_ENDPOINT: "https://api.honeycomb.io"
      OTEL_EXPORTER_OTLP_HEADERS: "x-honeycomb-team=${HONEYCOMB_API_KEY}"
      ROLLBAR_ACCESS_TOKEN: "${ROLLBAR_ACCESS_TOKEN}"
```

### Initializing rollbar to collect logs
```python
rollbar_access_token = os.getenv('ROLLBAR_ACCESS_TOKEN')
@app.before_first_request
def init_rollbar():
    """init rollbar module"""
    rollbar.init(
        # access token
        rollbar_access_token,
        # environment name
        'production',
        # server root directory, makes tracebacks prettier
        root=os.path.dirname(os.path.realpath(__file__)),
        # flask already sets up logging
        allow_logging_basic_config=False)

    # send exceptions from `app` to rollbar, using flask's signal system.
    got_request_exception.connect(rollbar.contrib.flask.report_exception, app)
```

### Adding a mock endpoint for testing just after initializing rollbar in app.py file
```python
@app.route('/rollbar/test')
def rollbar_test():
    rollbar.report_message('Hello World!', 'warning')
    return "Hello World!"
```
