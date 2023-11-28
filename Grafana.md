## Grafana install

Github repo [https://github.com/Mazurovsasha/16.Monitoring/tree/master/grafana]

User/pass: admin/admin

## WebUi

1. Connections > Data Sources > Save & tast

2. Add dashboard. Dashboards > Create Dashboards. Либо New > Import (кнопка верхний правый угол ) [https://grafana.com/grafana/dashboards/11074]

Graph for cont of pods per node

Metrics: sum(kube_pod_info{node=~"$node",job="kube-state-metrics"}) by (node)
Legend: {{node}}
Containers restarts
Metrics: sum(kube_pod_container_status_restarts_total{job="kube-state-metrics"}) by (pod)
Legend: {{pod}}