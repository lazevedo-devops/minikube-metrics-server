# minikube-metrics-server

This repo contains the Kubernetes manifest for Metrics Server with parameter that runs perfectly at Minikube.

Basically the difference between the official manifest and this is the command section in spec.containers.args, the minikube cluster is a cluster that runs without certificate then is necessary runs the metric server without TLS Verify.

```code
command:
          - /metrics-server
          - --kubelet-insecure-tls
          - --kubelet-preferred-address-types=InternalIP
```

#### Pre-Requisites

* Kubectl Installed
* Minikube Cluster

#### Usage

```Install Locally```
```code
kubectl apply -f ./components.yaml
```

```Install Remotely```
```code
kubectl apply -f https://raw.githubusercontent.com/lazevedo-devops/minikube-metrics-server/main/components.yaml
```

You'll see a message informing that components was installed at cluster, and around 30-40 seconds the pod of metric server will be up at kube-system namespace.

#### Verifying Installation

To verify the right installation you could use this command

```code
kubectl top nodes
```

This command should present the list of nodes and the percentage of usage of them, if this happen, then the installation was done correctly.

#### Questions and Feedback?

Find me on the Linkedin as lazevedo-devops or feel free to contact me through mail lazevedo@darkscreen.io.