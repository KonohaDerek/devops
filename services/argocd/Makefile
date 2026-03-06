argo:
        kubectl port-forward svc/argocd-server -n argocd 8888:80

add-cluster:
        argocd cluster add $(c)

login:
        argocd login 127.0.0.1:8888 --username admin --password admin --insecure