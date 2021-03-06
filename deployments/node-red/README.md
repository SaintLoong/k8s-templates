# node-RED

![](https://i.imgur.com/XxN4KJK.png)

## installing

```shell
helm upgrade --install node-red stable/node-red --reset-values --values values.yaml --set ingress.hosts="{node-red.$DOMAIN}"
```

### installing custom nodes

```shell
export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=node-red,app.kubernetes.io/instance=node-red" -o jsonpath="{.items[0].metadata.name}")
k exec -ti $POD_NAME "bash"
cd /data
npm install node-red-contrib-home-assistant
exit
k delete pod/$POD_NAME
```

## backup (stash)

```shell
kubectl create -f stash.yaml
```
