## Istio Service Mesh Demo in Minikube

Istio is an open-source service mesh platform that provides advanced routing, network visibility, and security features for microservices applications. In this demo, we will walk through the process of deploying Istio in a Minikube cluster and exploring its features.

The demo app used in this project is forked from Google Cloud Platform repository. More details are attached in the original repo link.

Forked link: https://github.com/shakayhere/kubernetes-microservices-demo
Original link: https://github.com/GoogleCloudPlatform/microservices-demo

## Dependencies to Install

To follow this demo, you need the following software installed on your system:

- Minikube
- kubectl
- Istio CLI

## Steps

1. We need a Kubernetes cluster first. For that, we are using minikube. To deploy a Minikube cluster, run the following command in your terminal:
    ```
    minikube start
    ```


2. Run command to install isio in your cluster:
    ```
    istioctl install
    ```

3. Before deploying our demo application, we need to add label in our default namespace so that istio can inject proxies into our pods. We can do that by using the followng command:
    ```
    kubectl label namespace defualt istio-injection=enabled
    ```

4. Apply kubernetes manifest file to deploy demo application inside kubernetes cluster:
    ```
    kubectl apply -f kubernetes-manifests.yaml
    ```
 
## Visualize Your Mesh

Kiali is an observability console for Istio with service mesh configuration and validation capabilities. It helps you understand the structure and health of your service mesh by monitoring traffic flow to infer the topology and report errors. We will deploy this into our cluster to view our mesh.


### View Dashboard of Our Deployed Application

1. We have kiali in our respoitory so we will apply it as kubernetes yaml file like:
    ```
    kubectl apply -f kiali.yaml
    ```

2. Port-forward kiali's service or run the following:
    ```
    istioctl dashboard kiali
    ```