# RUN :

1. Download and install minikube : https://github.com/kubernetes/minikube
2. Install hyperkit :

* Docker
`curl -LO https://storage.googleapis.com/minikube/releases/latest/docker-machine-driver-hyperkit \
&& chmod +x docker-machine-driver-hyperkit \
&& sudo mv docker-machine-driver-hyperkit /usr/local/bin/ \
&& sudo chown root:wheel /usr/local/bin/docker-machine-driver-hyperkit \
&& sudo chmod u+s /usr/local/bin/docker-machine-driver-hyperkit`

* Hyperkit
[hyperkit](https://github.com/moby/hyperkit)


3. First delete .minikube `~/.minikube and (optional) .kube directory ~/.kube`
4. `./minikube start -p CLUSTER_NAME --driver=virtualbox --host-only-cidr 192.168.56.1/24 (virtualbox) or ./minikube start --driver=hyperkit (hyperkit)`
5. Optional for multinodes : `./minikube start --nodes n (n for how many nodes wants to deploy)`
6. `./minikube -p CLUSTER_NAME kubectl -- create deployment balanced --image=nginx`
7. `./minikube -p CLUSTER_NAME kubectl -- expose deployment balanced --type=LoadBalancer --port=8080 --target-port=80 (target-port = container port and port = host port)`
8. `./minikube -p CLUSTER_NAME tunnel`
9. Check details service : `./minikube -p CLUSTER_NAME kubectl -- get svc`
10. Open browser type http://EXTERNAL_IP
11. Destroy all nodes : `./minikube delete --all`
