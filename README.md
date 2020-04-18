# helm-generator
Generates the helm chart using ansible 


# Generate the helm chart 
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

```
ansible-playbook helm-generator
```

# Prerequisites.
1. Ansible
2. Helm 
3. kubectl (after genertion)


# Example configuration (partial)
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