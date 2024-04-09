
Крок 1. \
Встановити ArgoCD на k8s кластер

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Крок 2. \
Зконфігурувати доступ по мережі з локальної машини в кластер k8s

```
kubectl port-forward svc/argocd-server -n argocd 8899:443&
```

Крок 3. \
Відкрити URL https://127.0.0.1:8899

Крок 4. \
Встановити ArgoCD CLI
Інструкція по інсталяції - https://argo-cd.readthedocs.io/en/stable/cli_installation/

Крок 5. \
Отримати адмін пароль до GUI веб-консолі ArgoCD
```
argocd admin initial-password -n argocd
```

## АБО

Step 5.1. \
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo
```

Step 6. \

Залогінитись під користувачем адмін використовуючи пароль отриманий в кроках 5 або 5.1

