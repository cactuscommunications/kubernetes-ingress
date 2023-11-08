# Steps to deploy

1. Create namespace and service account

    `kubectl apply -f common/ns-and-sa.yaml`

2. Create rbac

    `kubectl apply -f rbac/rbac.yaml`

3. Create default server secret

    `kubectl apply -f common/default-server-secret.yaml`

4. Create nginx config

    `kubectl apply -f common/nginx-config.yaml`

5. Create ingress class

    `kubectl apply -f common/ingress-class.yaml`


6. Install CRDs

    ```
    kubectl apply -f common/crds/k8s.nginx.org_virtualservers.yaml
    kubectl apply -f common/crds/k8s.nginx.org_virtualserverroutes.yaml
    kubectl apply -f common/crds/k8s.nginx.org_transportservers.yaml
    kubectl apply -f common/crds/k8s.nginx.org_policies.yaml
    kubectl apply -f common/crds/k8s.nginx.org_globalconfigurations.yaml
    ```
    
7. Create deployment

    `kubectl apply -f deployment/nginx-ingress.yaml`

8. Create service (NLB)

    `kubectl apply -f service/loadbalancer-aws-elb.yaml`
    (Remember to update ACM certificate)


Reference [here](https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-manifests/).