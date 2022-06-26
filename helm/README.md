# Helm

```bash
docker ps
```

```bash
helm search hub 
```

```bash
helm search hub kafka
```

Check Artifact hub at https://artifacthub.io/


```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```
```bash
helm repo list 
```
```bash
helm search repo grafana
```

Now, we're ready to install the charts. Installing a charts would deploy the application on kubernetes.

```bash
helm install grafana bitnami/grafana
```
```bash
kubectl get pods
```

It take some time to running the pods

The console would be something like this -

Application: http://127.0.0.1:8080

kubectl port-forward svc/grafana 8080:3000
User: admin
Password: kubectl get secret grafana-admin --namespace default -o jsonpath="{.data.GF_SECURITY_ADMIN_PASSWORD}" | base64 --decode

Enter password and go to port 8080

```bash
kubectl search repo 
```
```bash
kubectl search repo grafana
```
```bash
helm list
```
```bash
helm status grafana
```
```bash
helm upgrade grafana bitnami/grafana  #(Increase the revision)
```
```bash
helm rollback grafana 1 #(rollback to revision 1) -> chart name will change to the previous version
```
```bash
helm list
```
```bash
helm uninstall grafana
```
```bash
helm install grafana bitnami/grafana --version 7.9.6
```
```bash
helm list
```
```bash
helm upgrade grafan bitnami/grafana --version 7.9.8
```
```bash
helm show values bitnami/grafana
```
```bash
helm install --set replicaCount=2 grafana bitnami/grafana
```

Or 
```bash
helm install -f values.yml grafana bitnami/grafana
```
```bash
kubectl get pods #(now kubernets started 2 pods)
```

```bash
helm upgrade --reset-values grafana bitnami/grafana
```


```bash
helm dependency build 
```

## Create, package and install own helm charts

```bash
helm create hello-world
```
```bash
helm package hello-world
```
```bash
helm install hello-world ./hello-world-0.1.0.tgz
```

Now, you can access the application using the commands given in notes after installation (can edit the repository values)

```bash
helm uninstall hello-world
```

## If need to upload the chart to a repo

```bash
helm repo index . --url https://your.repo 
```
