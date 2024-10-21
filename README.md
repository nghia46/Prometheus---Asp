### Run toturial
To run:
Step 1: Pull *Prometheus* and *Grafana* in docker hub
Step 2: Run you app with config endpoint for metric (example: localhost/metrics)
Step 3: Config the app endpoint with *Prometheus* using *Prometheus* config *.yml*
Step 4: Map *Prometheus* metric in *Grafana* 
Step 5: Setup *Grafana* chart for the metric stats
### Command
```bash
docker run -d --name=prometheus -p 9090:9090 -v your-prometheus-config directory\prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus
```
### prometheus-config-example
```yml
global:
  scrape_interval: 5s

scrape_configs:
  - job_name: 'aspnetcore_api'
    scrape_interval: 5s
    metrics_path: /metrics
    scheme: https
    tls_config:
      insecure_skip_verify: true
    static_configs:
      - targets: ['host.docker.internal:7005']

```