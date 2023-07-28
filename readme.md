## Helm

[Installing Helm](https://helm.sh/docs/intro/install/)



## Kubernetes 

> Note: Docker Desktop for Windows adds its own version of kubectl to PATH 
> [Enable Kubernetes](https://docs.docker.com/desktop/kubernetes/#enable-kubernetes)

- Test version

`kubectl version --client --output=yaml`

`kubectl version --client`

- Install and Set Up kubectl on Windows

1. Download the latest kubectl 1.27.4
`curl.exe -LO "https://dl.k8s.io/release/v1.27.4/bin/windows/amd64/kubectl.exe"`

2. Validate the binary (optional)
`curl.exe -LO "https://dl.k8s.io/v1.27.4/bin/windows/amd64/kubectl.exe.sha256"`

3. Using Command Prompt to manually compare
`CertUtil -hashfile kubectl.exe SHA256`
`type kubectl.exe.sha256`

4. Verify kubectl configuration
`kubectl cluster-info`
`kubectl cluster-info dump`

[Install and Set Up kubectl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)



## Artifacthub

search package e.g. prometheus



## Prometheus

1. Add repository

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`

2. Check repository

`helm repo ls`

`helm search repo prometheus-community`

3. Install chart

`helm install my-prometheus prometheus-community/prometheus --version 23.1.0`

4. Get the Prometheus server URL by running these commands in the same shell:

- win cmd
`kubectl get pods --namespace default -l "app.kubernetes.io/name=prometheus,app.kubernetes.io/instance=my-prometheus" -o jsonpath="{.items[0].metadata.name}"`
`kubectl --namespace default port-forward %POD_NAME% 9090`

- linux
`export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=prometheus,app.kubernetes.io/instance=my-prometheus" -o jsonpath="{.items[0].metadata.name}")`
`kubectl --namespace default port-forward $POD_NAME 9090`


