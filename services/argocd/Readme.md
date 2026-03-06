# ArgoCD

## install
1. kubectl create namespace argocd
2. kubectl apply -n argocd -k .


#### Argocd 增加cluster
1. 在argocd 上增加cluster
2. gcloud container clusters get-credentials bupo-cluster --region asia-east1 --project reusebupo-419110
3. kubectl config  use-context   k3d-how-cluster 
4. k8s 轉發argocd-service port : kubectl port-forward svc/argocd-server -n argocd 8888:80
5. 登入argocd : argocd login 127.0.0.1:8888
6. argocd cluster add k8s-stage.howdesign.com.tw

### Argocd 變更cluster
// 修改已存在argocd 中的cluster 連線資訊
argocd cluster add k8s-stage.howdesign.com.tw --name k8s-stage.howdesign.com.tw --insecure --server https://k8s-stage.howdesign.com.tw:6443 --config-management-plugin kustomize