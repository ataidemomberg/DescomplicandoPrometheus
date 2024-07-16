Temos a nossa aplicação Giropops-Senhas em execução em nosso cluster, porém ela não está monitorada pelo nosso cluster!

Você precisa monitorar essa app, coletando as métricas que ela está expondo.

A noticia ruim é que não sabemos maiores detalhes sobre a app e como monitorar, portanto, você terá 10 minutos de trabalho intenso!

Instruções
Investigue a aplicação Giropops-Senhas em execução no cluster para descobrir informações sobre como coletar métricas.


Atualize a configuração do Prometheus no Kube-Prometheus para incluir o coletor de métricas (scrape) da aplicação Giropops-Senhas. Certifique-se de que o Prometheus esteja coletando métricas do aplicativo corretamente.

cp app-servicemonitor.yaml giropops-servicemonitor
kubectl apply -f giropops-servicemonitor

kubectl port-forward svc/giropops-senhas  --address 0.0.0.0 5000:5000

Verifique se o monitoramento está funcionando corretamente e se as métricas estão sendo coletadas e exibidas no Grafana.
O nome do ServiceMonitor deverá ser: giropops-servicemonitor

IMPORTANTE: - Não deixe nenhum port-forward em execução no final do seu teste! - Para acessar a os serviços na aba Navegador, execute o comando abaixo e depois vá para a aba do Navegador: kubectl port-forward svc/SERVICE -n NAMESPACE --address 0.0.0.0 PORTA:PORTA_SERVICE

Quando concluir todas as etapas, clique no botão Check para verificar se tudo está configurado corretamente.