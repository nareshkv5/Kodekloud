Need to rollout to previous version

```
kubectl get deploy
kubectl get pods
kubectl rollout undo deployment nginx-deployment -- to deploy to previous version
kubectl get deploy 
kubectl get pods
kubectl rollout status deployment nginx-deployment -- to check the rollout deployment status
