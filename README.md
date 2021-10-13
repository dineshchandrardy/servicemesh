# Iaas-repo
Service mesh technology comparison for encrypted inter-pod communication on Kubernetes clusters.

## Minikube Cluster setup with one control plane/master node and data plane/worker node.

### minikube installation 

Step1: Created a minikube kubernetes cluster locally on windows
         	minikube start  --memory=5120  --driver=hyperv  --cpus=4

 
Step2: Enabled Ingress            
                    	minikube addons list
                        minikube addons enable ingress

Step3: Deployed Traefik and Nginx applications on minikube cluster
                kubectl apply -f service-traefik.yaml   
                kubectl apply -f service-nginx.yaml 

Step4: Installing istio through istio operator https://istio.io/latest/docs/setup/install/operator/

step 5: Downloading the istioctl CLI package release for windows from the following  https://github.com/istio/istio/releases/tag/1.11.0

step 6: istio init operator

step 7: istioctl install istiooperator.yaml

step 8: View config map after the installation to see the istio-ca-root-cert.
                kubectl get cm 
				Kubectl get cm istio-ca-root-cert -o yaml

Step 9: deploying traefik ingress controller into traefik namespace            
            kubectl create ns traefik
            kubectl apply -f traefik.yaml -n traefik

Step 10: Deploying nginx into health-endpoint namespace
            kubectl create ns health-endpoint
            kubectl apply -f nginx.yaml -n health-endpoint

step 11: Describing end-points for each instance
           kubectl get ep nginx -n health-endpoint
           kubectl get ep traefik -n traefik

High level overview of deployments





