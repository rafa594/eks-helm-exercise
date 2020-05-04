# EKS, Helm deployment
This repository contains the configuration files to deploy an containerized application using Kubernetes, on a AWS EKS Cluster. Helm and eksctl tools are used to enhance the performance of application.

The application consist in two webpages. First one is a Static Webpage, that shows a simple informative page. The second one is a Flask webpage consuming a Redis database. Both are running through Kubernetes deployments and services managed by a Helm release.

## Project diagram:
![EKS Helm Deployment](/images/initial.png)

## Process

First of all, create an AWS EKS cluster using eksctl tool.
Go to `eksctl` folder and run the next command:

`   
eksctl create cluster --config-file=eksctl/cluster.yaml
`

Wait for 5-10 minutes to configure the cluster. Check the configuration with the next command:

`
kubectl get sc
`

This commands show the storage classes and the provisioner of each one.
Must appear an AWS related provisioner.


Next, install the Helm custom chart. 
Go to `helm` folder and run the next command:

`
helm install eks-helm proxyapp/
`

To check the correct installation, look for the ingress objects in the cluster:

`
kubectl get ingress
`

This command must show the DNS of the Load Balancer configured in the Ingress file to reach the application.

To view the containers in the project, take the previous DNS and add the `static/` or `web/` subdirectory:

`
http://your.aws.loadbalancer.dns/web/

http://your.aws.loadbalancer.dns/static/
`