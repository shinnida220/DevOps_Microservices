# Lesson 4 Container Ochestration With Kubernetes
# Class 6 - Exercise - Exercise - Creating an EKS Cluster and Deploying an App - CLI

create-k8-cluster:
	# 1. Create a kubernetes cluster
	eksctl create cluster --name udacity-k8 --region=us-east-1 \
		--zones=us-east-1a,us-east-1b,us-east-1c,us-east-1d,us-east-1f 
		# --instance-types=t3.small 
		# --cfn-role-arn=Cloud9-EKS-Role
		# --instance-selector-vcpus=2 --instance-selector-memory=2 --instance-selector-cpu-architecture=x86_64
		# --ssh-public-key="ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAINozaHQYGcQbiB5GIUrAFXa3j2f6RnvokAcgtvX2MQ35 ibk.com@gmail.com" \
		# 

check-status-of-created-cluster:
	# 2. You can check the status with 
	eksctl utils describe-stacks --region=us-east-1 --cluster=udacity-k8 --output=yaml
	
check-details-of-created-cluster:
	# 3. Once the Cluster (CloudFormation stack) status is CREATE_COMPLETE
	eksctl get cluster --name=udacity-k8 --region=us-east-1
	
update-kube-config:
	# Create or update the kubeconfig file for your cluster:
	@cat ~/.kube/config
	aws eks --region us-east-1 update-kubeconfig --name udacity-k8-demo
	
check-k8-cluster-health:
	# Interact wiht the cluster with kubectl -> Check the health of the cluster
	kubectl get nodes
	
dockerise-sample-app:
	# Ensure Docker Desktop is running locally
	docker --version
	# Build an image using the Dockerfile in the current directory
	@cd python-helloworld; docker build -f Dockerfile -t python-helloworld .
	
run-docker-container-locally:
	docker run -it 8ad5d4e648f5 bash
	
list-available-docker-images:
	docker images
	
run-docker-container:
	# Run a container
	docker run -d -p 5000:5000 python-helloworld
	
check-running-container:
	# Check the output at http://localhost:5000/ or http://0.0.0.0:5000/ or http://127.0.0.1:5000/
	docker ps
	
stop-docker-container:
	# Now, stop the container.
	docker container stop python-helloworld -t 10
	
tag-docker-image-locally:
	# Tag locally before pushing to the Dockerhub
	# We have used a sample Dockerhub profile /sudkul
	# Replace sudkul/ with your Dockerhub profile
	docker tag python-helloworld nuelibk/python-helloworld:v2.0.0
	docker images
	
login-to-docker-hub:
	# Log into the Dockerhub from your local terminal
	docker login

push-image-to-docker-hub:
	# Replace nuelibk/ with your Dockerhub profile
	docker push nuelibk/python-helloworld:v2.0.0
	# Check the image in your Dockerhub online at https://hub.docker.com/repository/docker/nuelibk/python-helloworld

k8-deploy-docker-image:
	# Deploy an App from the Dockerhub to the Kubernetes Cluster
	kubectl create deploy python-helloworld --image=nuelibk/python-helloworld:v2.0.0
	
k8-delete-deployment:
	# Deploy an App from the Dockerhub to the Kubernetes Cluster
	kubectl delete deploy python-helloworld

k8-get-deploy-status:	
	# See the status
	kubectl get deploy,rs,svc,pods	
	
k8-port-forward:
	# Port forward 
	kubectl port-forward pod/python-helloworld-6779477f66-rwgm6 --address 0.0.0.0 5000:5000
	
destroy-cluster:
	eksctl delete cluster --region=us-east-1 --name=udacity-k8 --force