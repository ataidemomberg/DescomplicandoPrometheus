Você precisa instalar o kube-prometheus nesse cluster Kubernetes que já está configurado, somente esperando você e o kube-prometheus! Bom trabalho!

Instruções
Instale o Kube-Prometheus no cluster Kubernetes
- Executar:

git clone https://github.com/prometheus-operator/kube-prometheus \
cd kube-prometheus \
kubectl create -f manifests/setup \
kubectl apply -f manifests/

#################################################
!!! As Demais abaixo nao e necessario !!!
##################################################

Verifique se todos os componentes do Kube-Prometheus estão em execução, incluindo Prometheus, Grafana, Alertmanager e outros serviços relacionados.
Executar: 

kubectl get servicemonitors -A


Acesse o Prometheus na porta 39090, o Grafana na porta 33000 e o Alertmanager na porta 39093 através do port-forward, para verificar se eles estão funcionando corretamente.


kubectl port-forward svc/prometheus-k8s -n monitoring --address 0.0.0.0 39090:9090
kubectl port-forward svc/grafana -n monitoring --address 0.0.0.0 33000:3000
kubectl port-forward svc/alertmanager-main -n monitoring --address 0.0.0.0 39093:9093
kubectl port-forward svc/alertmanager-main -n monitoring --address 0.0.0.0 39093:9093



IMPORTANTE: - Não deixe nenhum port-forward em execução no final do seu teste! - Para acessar a os serviços na aba Navegador, execute o comando abaixo e depois vá para a aba do Navegador: kubectl port-forward svc/SERVICE -n NAMESPACE --address 0.0.0.0 PORTA:PORTA_SERVICE

Quando concluir todas as etapas, clique no botão Check para verificar se tudo está configurado corretamente.

