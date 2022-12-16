apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: recursive-tree-sample-app3
  namespace: argocd
  annotations:
    argocd.argoproj.io/sync-wave: "30"
spec: 
  project: default
  source:
    path: components/app3
    repoURL: https://github.com/6za/k1-watcher-demo.git
    targetRevision: HEAD
    directory:
      recurse: true # <--- Here
  destination:
    server: 'https://kubernetes.default.svc'
    namespace:  default
  syncPolicy:
      automated:
        prune: true
        selfHeal: true
      syncOptions:
        - CreateNamespace=true
      retry:
        limit: 5
        backoff:
          duration: 5s
          maxDuration: 5m0s
          factor: 2
