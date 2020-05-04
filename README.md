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

Next, install the Helm custom chart. 
Go to `helm` folder and run the next command:

`
helm install eks-helm proxyapp/
`
