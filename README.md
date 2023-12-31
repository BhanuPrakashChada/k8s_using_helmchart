# k8s_using_helmchart
## Setting up a 2-Node Kubernetes Cluster using Kubeadm

## Pre req's:
- 2 vm's who's swap memory is disabled and firewall is configured to allow traffic (i used 2 ec2 instances)

### Step-1: Set the host name as Controlplane and worker for each vm respectively 
### Step-2: Install Docker
### step-3: Configure cgroup driver
### step-4: isntall Kube componets i.e. - Kubeadm - Kubelet - Kubectl
### step-5: Initialize controlplane node:
-> sudo kubeadm init --apiserver-advertise-address=<CONTROLPLANE_NODE_IP> --apiserver-cert-extra-sans=<CONTROLPLANE_NODE_IP> --pod-network-cidr=192.168.0.0/16 --node-name=<CONTROLPLANE_HOSTNAME>
### step-6: generate join command by running the below command on controlplane node
-> sudo kubeadm token create --print-join-command
### step-7: Copy the join command and run it on the worker node.
### step-8: verify the cluster 
-> kubectl get nodes
### step-9: clone the repo "https://github.com/BhanuPrakashChada/k8s_using_helmchart.git"
### step-10: Navigate to the helm_app directory, generate the docker iamge and run the following command to install helm chart
-> helm install helm_app-chart ./charts --values ./values.yaml

