Installing k3s without Traefik
```
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="server" sh -s - --disable=traefik
```
This will install k3s without Traefik

Removing Traefik from the already running k3s
```
sudo  kubectl delete -f  /var/lib/rancher/k3s/server/manifests/traefik.yaml 
sudo rm -rf /var/lib/rancher/k3s/server/manifests/traefik.yaml 
sudo systemctl restart k3s
```
Traefik will be uninstalled and will not be reinstalled via HelmChartConfig when k3s is restarted.


## 測試 k3s config
```
KUBECONFIG=~/.kube/howdigital-k3s-prod-config kubectl get all
```

## 合併 config
 KUBECONFIG=~/.kube/config:~/.kube/eco.config kubectl config view --merge --flatten > config


 ## registries
 ### Google 
 1. cat json.key | docker login -u _json_key --password-stdin https://gcr.io
 2. 