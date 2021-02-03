# prometheus-demo
Demo prometheus setup with alert manager and cadvisor

Installation
  run mkdir -p var/alertmanager/data
  run mkdir -p var/grafana/data
  

Based on https://sbcode.net/prometheus/install-prometheus/

Authentication
    
    ./etc/nginx/.htpasswd

Rules: 

    /rules

Demo queries: 
    
    /graph?g0.expr=up&g0.tab=1&g0.stacked=0&g0.range_input=15m
    /graph?g0.expr=go_threads&g0.tab=1&g0.stacked=0&g0.range_input=15m&g1.expr=&g1.tab=1&g1.stacked=0&g1.range_input=1h
    /graph?g0.expr=ALERTS{alertname%3D"DiskSpaceFreeRoot10Percent"}&g0.tab=1&g0.stacked=0&g0.range_input=1h    

Grafana

Configuration: add prometheus source as http://prometheus:9090
    URLs
    
    /grafana/    
    /grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Prometheus%22,%7B%22expr%22:%22rate(http_request_total%5B5m%5D)%22,%22requestId%22:%22Q-19994a0b-4ce8-4098-926d-19dcf9a34969-0A%22%7D%5D
    /grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Prometheus%22,%7B%22expr%22:%22ALERTS%7Balertname%3D%5C%22DiskSpaceFreeRoot90Percent%5C%22%7D%22,%22requestId%22:%22Q-f2532b46-453e-4db4-b54a-be93107efec8-0A%22%7D%5D
    
    
Alertmanager 

    /alertmanager/#/alerts    