kube adm can be used to help you create mvp cluster for k8s it is a tool to create a controlplane nodes and workernodes to join the cluster 

blog : https://devopscube.com/setup-kubernetes-cluster-kubeadm/
video : https://www.youtube.com/watch?v=xX52dc3u2HU&ab_channel=DevopsCube

### what will kubeadm do ?
1.  When you initialize kubeadm, first it runs all the preflight checks to validate the system state and it downloads all the required cluster container images from the **registry.k8s.io** container registry.
2.  It then generates required TLS certificates and stores them in the **/etc/kubernetes/pki** folder.
3.  Next, it generates all the kubeconfig files for the cluster components in the **/etc/kubernetes** folder.
4.  Then it starts the kubelet service and generates the static pod manifests for all the cluster components and saves it in the **/etc/kubernetes/manifests** folder.
5.  Next, it starts all the control plane components from the static pod manifests.
6.  Then it installs core DNS and Kubeproxy components
7.  Finally, it generates the node bootstrap token.
8.  Worker nodes use this token to join the control plane.

### before we begin !
1. make sure you have these ports free
![[Screenshot 2023-05-02 at 01.12.30.png]]


### there is two ways to create k8s cluster

## Declarative using yaml file
2. make sure you have [[containerd]] or whatever [[CRI]] you wana use
3. create `kubeadm-config.yaml` file and create the cluster resources as you need
4. here is an example config file for using ip(82.131.58.212) and [[containerd]] as the cri
```
apiVersion: kubeadm.k8s.io/v1beta3
kind: ClusterConfiguration
kubernetesVersion: stable
controlPlaneEndpoint: "82.131.58.212:6443"
networking:
  podSubnet: "10.244.0.0/16"
  serviceSubnet: "10.96.0.0/12"
---
apiVersion: kubeadm.k8s.io/v1beta3
kind: InitConfiguration
nodeRegistration:
  criSocket: /run/containerd/containerd.sock
```

5. apply the file using `sudo kubeadm init --config=kubeadm-config.yaml`
4. in order for kubectl to be able to interact with the cluster run the following
	1. `mkdir -p $HOME/.kube`
	2. `sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config`
	3. `sudo chown $(id -u):$(id -g) $HOME/.kube/config`

## Imperative using command line
2. install container runtime like crio steps https://www.linuxtechi.com/install-crio-container-runtime-on-ubuntu/
3. run this command to create a master node 
```
sudo kubeadm init --control-plane-endpoint="<PUBLIC-IP>" --apiserver-cert-extra-sans="<PUBLIC-IP>" --pod-network-cidr="192.168.0.0/16" --node-name "controlplane" --ignore-preflight-errors Swap --cri-socket="unix:///var/run/crio/crio.sock"
```

NOTE check every parameter carefully and update it as needed 

4. in order for kubectl to be able to interact with the cluster run the following
	1. `mkdir -p $HOME/.kube`
	2. `sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config`
	3. `sudo chown $(id -u):$(id -g) $HOME/.kube/config`
5. now you can use `kubectl` to play around with this master node and join more workernodes to the cluster

### reset or remove a node 
https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/#tear-down