Neste desafio, você vai corrigir a configuração do Prometheus e do Grafana. O Prometheus não está funcionando corretamente e o Grafana precisa ser configurado.

Instruções

Corrija os arquivos de configuração do Prometheus
- Ajustar o arquivo /etc/systemd/system/prometheus.service
- Colar o conteudo do prometheus.service para o arquivo acima


Verifique se o Prometheus está coletando métricas de si mesmo e do Node Exporter.
- Copiar o arquivo do prometheus.yml

Configure o Grafana para usar o Prometheus como fonte de dados.

sudo apt-get install -y apt-transport-https software-properties-common wget && \
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add - && \
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main" && \
sudo apt-get update && sudo apt-get install grafana -y && \
systemctl enable --now grafana-server


Configure os alertas no Prometheus e verifique se estão funcionando corretamente.
- Renomer o arquilo rules.alert para alert.rules

Gere alguma carga para que o alerta seja criado.
- Nao e Necessario

Quando concluir todas as etapas, clique no botão Check para verificar se tudo está configurado corretamente.