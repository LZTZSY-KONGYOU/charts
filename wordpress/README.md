cd /k3s/wordpress/ # 假设您的 Chart 位于此目录
### 如果您想部署到 wordpress-app 命名空间：
```
helm install my-wordpress . -n wordpress-app --create-namespace
```

### ** 检查部署状态**
```
kubectl get pods -n wordpress-app
kubectl get svc -n wordpress-app
kubectl get deployments -n wordpress-app
```

### 访问 WordPress**

**如果 `service.type` 是 `NodePort`：** WordPress 将通过 K3s 节点的 IP 地址和您在 `values.yaml` 中配置的 NodePort 访问。 例如：`http://<您的K3s节点IP>:30080`

### 部署 Redis Deployment 和 Service
```
cd /k3s/wordpress/templates/redis/

kubectl apply -f redis-deployment.yaml -n wordpress-app

kubectl apply -f redis-service.yaml -n wordpress-app

kubectl get pods -n wordpress-app | grep redis

kubectl get svc -n wordpress-app | grep redis

```
