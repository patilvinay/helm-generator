# Helm-generator
Generates the helm chart using ansible 


## Generate the helm chart 
Features
1. Generates Service resource
2. Deployments resource
3. VirtualService resource for Istio
4. Gateway resource for Istio
5. Ingress resource in case you don't want to use Istio
6. Pull Secret (secret file should be kept in ~/.config folder, helm pulls it during helm install)
7. Application secret(secret file should be kept in ~/.config folder, helm pulls it during helm install)
8. Database string(secret file should be kept in ~/.config folder, helm pulls it during helm install)
9. Certmanager Certificate resource(both prod and staging)
config.yaml has all the configuration date. This file can be modified to customise the generated template


## How to run 
```
./helm-generator <your config file>

#Example
./helm-generator config-webapp.yaml
```

## Prerequisites.
1. Ansible
2. Helm 
3. kubectl (after genertion)

## Prerequisites to use the generated helm chart
1. kubectl
2. k8s cluster (Cloud,minikube,kind, I use kind)
3. Istio Installed in K8s

> When you run the helm install use the right context.
```
kubectl config use-config  <your context>
```


## Example configuration (partial)
```
app:
    name: todo-api
    version: latest
    host: todo.in
    kubeContext: kind-kind
    namespace: todo

config:
   deployment: 'enabled' 
   service: 'enabled'
   ingress: 'enabled'
   gateway: 'enabled'
   virtualService: 'enabled'
   dockerSecret: 'enabled'
   applicationSecret: 'enabled'
   dockersecret: 'enabled'

```