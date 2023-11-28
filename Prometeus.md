## Deploy

Github repo [https://github.com/Mazurovsasha/16.Monitoring/tree/master/prometheus]

### KSM metrik install

Github repo [https://github.com/Mazurovsasha/16.Monitoring/tree/master/ksm]

## Rules

Указываются в ConfigMap

```yaml
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: prometheus-server-conf
  labels:
    name: prometheus-server-conf
  namespace: monitoring
data:
  prometheus.rules: |-
    groups:
    - name: devopscube demo alert
      rules:
      - alert: High Pod Memory
        expr: sum(container_memory_usage_bytes) > 1
        for: 1m
        labels:
          severity: slack
        annotations:
          summary: High Memory Usage
```

## test filter examples:

```
rate(container_cpu_usage_seconds_total{pod=~"jenk.*"}[1m])
container_memory_working_set_bytes{container="jenkins"}
```
