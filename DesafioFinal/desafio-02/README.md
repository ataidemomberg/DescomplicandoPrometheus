Configurando e testando o Alertmanager
🧪 Neste desafio, você vai configurar e testar o Alertmanager para enviar alertas com base em condições predefinidas nas métricas coletadas pelo Prometheus.

Instruções
Adicione a configuração de alerting para integrar o Prometheus com o Alertmanager.

Crie um arquivo de regras de alerta chamado alert.rules e adicione uma regra de exemplo. Caso queira, você pode usar esse exemplo de alerta:

yaml

copy
groups:
- name: example
  rules:
  - alert: high_load
    expr: node_load1 > 0.01
    for: 10s
    labels:
      severity: page
    annotations:
      summary: "Instance {{ $labels.instance }} under high load"
      description: "{{ $labels.instance }} of job {{ $labels.job }} is under high load."
Verifique se a regra de alerta é acionada e se o Alertmanager recebe o alerta corretamente.

💡 Use as guias "Terminal" e "Editor" para concluir este desafio.

🏁 Para verificar se você concluiu corretamente o desafio, pressione Check.
