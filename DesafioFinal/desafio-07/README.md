Adicionando o node do cluster Kubernetes ao Prometheus
Instruções
Na VM 'linuxtips-k8s-cluster', instale e configure o Node Exporter para expor métricas do node Linux. Instale n Node Exporter como um serviço no Linux, e não no Kubernetes.

curl -LO https://github.com/prometheus/node_exporter/releases/download/v1.8.2/node_exporter-1.8.2.linux-amd64.tar.gz

tar -xvzf node_exporter-1.8.2.linux-amd64.tar.gz

sudo mv node_exporter-1.3.1.linux-amd64/node_exporter /usr/local/bin/

sudo addgroup --system node_exporter
sudo adduser --shell /sbin/nologin --system --group node_exporter

sudo vim /etc/systemd/system/node_exporter.service

[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter $OPTIONS

[Install]
WantedBy=multi-user.target




Na VM 'linuxtips-server', atualize a configuração do Prometheus para incluir o Node Exporter do 'linuxtips-k8s-cluster'. Certifique-se de que o Prometheus esteja coletando métricas corretamente.

global:
  scrape_interval: 15s
  evaluation_interval: 15s
  scrape_timeout: 10s

rule_files:

scrape_configs:
  - job_name: "prometheus"
    static_configs:
      - targets: ["localhost:9090"]
  - job_name: "node_exporter"
    static_configs:
      - targets: ["localhost:9100"]

Verifique se o monitoramento está funcionando corretamente e se as métricas estão sendo coletadas e exibidas no Prometheus.

systemctl is-active nodeexporter

Importante: Quando terminar, verifique se o node_exporter está ativo com o seguinte comando: *systemctl is-active nodeexporter * Quando concluir todas as etapas, clique no botão Check para verificar se tudo está con