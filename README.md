###Demo
![{AFBC7C51-B134-4279-B27E-5079281A3677}](https://github.com/user-attachments/assets/414a7777-aa6e-4b75-9fdf-f3022599e1cf)
![{FD86929B-8F8C-4372-800E-60308637677B}](https://github.com/user-attachments/assets/168735bc-a6b3-4d38-9f51-20bda976abde)

### Run toturial
To run:

Step 1: Pull *Prometheus* and *Grafana* in docker hub
```bash
docker pull prom/prometheus
docker pull grafana/grafana
```
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
