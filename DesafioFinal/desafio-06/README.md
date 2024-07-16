Precisamos da sua ajuda! O Prometheus, Grafana e toda a monitoração da nossa aplicação Giropops-Senhas pararam de funcionar. E nós precisamos que tudo volte a funcionar em apenas 10 minutos!

Instruções
Verifique se todos os componentes do Kube-Prometheus estão em execução, incluindo Prometheus, Grafana, Alertmanager e outros serviços relacionados.

kubectl get svc

Use o comando kubectl port-forward para acessar os serviços Prometheus, Grafana e Alertmanager nas portas 39090, 33000 e 39093, respectivamente.

kubectl port-forward svc/prometheus-k8s -n monitoring --address 0.0.0.0 39090:9090
kubectl port-forward svc/grafana -n monitoring --address 0.0.0.0 33000:3000
kubectl port-forward svc/alertmanager-main -n monitoring --address 0.0.0.0 39093:909

Verifique se a aplicação Giropops-Senhas está em execução e coletando métricas.

Kubectl port-forward svc/giropops-senhas  --address 0.0.0.0 5000:5000


Ajuste o ServiceMonitor para a aplicação Giropops-Senhas, de modo que o Prometheus possa coletar as métricas corretamente.

kubectl apply -f giropops-servicemonitor

Verifique se o Prometheus está coletando métricas da aplicação Giropops-Senhas.
Acesse o Prometheus, Grafana e Alertmanager para garantir que todos os serviços estão funcionando corretamente.


Verifique se os exporters estão funcionando corretamente.
Ajuste a regra de alerta chamada alert-girus no PrometheusRule.
Lembre-se que você tem pouco tempo para resolver todos os problemas e deixar tudo funcionando novamente! Boa sorte!


   


   kubectl apply -f rule-app.yaml

IMPORTANTE: - Não deixe nenhum port-forward em execução no final do seu teste! - Para acessar os serviços na aba Navegador, execute o comando abaixo e depois vá para a aba do Navegador: kubectl port-forward svc/SERVICE -n NAMESPACE --address 0.0.0.0 PORTA:PORTA_SERVICE

=========
1  git clone https://github.com/prometheus-operator/kube-prometheus cd kube-prometheus kubectl create -f manifests/setup kubectl apply -f manifests/
    2  git clone https://github.com/prometheus-operator/kube-prometheus 
    3  cd kube-prometheus/
    4  kubectl create -f manifests/setup
    5  kubectl apply -f manifests/
    6  kubectl get servicemonitors -A
    7  docker ps
    8  kubectl get svc
    9  kubectl port-forward svc/prometheus-k8s -n monitoring --address 0.0.0.0 39090:9090
   10  kubectl port-forward svc/grafana -n monitoring --address 0.0.0.0 33000:3000
   11  kubectl port-forward svc/alertmanager-main -n monitoring --address 0.0.0.0 39093:9093
   12  ls
   13  cd giropops-senhas-labs/
   14  ls -l
   15  cd giropops-senhas/
   16  ls
   17  ls -l
   18  cp app-servicemonitor.yaml giropops-servicemonitor
   19  vim giropops-servicemonitor 
   20  kubectl apply -f giropops-servicemonitor 
   21  kubectl get svc
   22  kubectl port-forward svc/giropops-senhas  --address 0.0.0.0 5000:5000
   23  kubectl get svc
   24  history 