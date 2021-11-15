# eks-redmine
This repo is public and create to deploy a full redmine setup using EKS on AWS

Install eksctl on you PC/Mac, and then create a cluster

$ eksctl create cluster -f linux-nodes.yaml

This will create a cluster on EKS

Then apply the Database config map, deployment and service using kubectl (This include presistent volume)

$ kubectl apply -f database-data-persistentvolumeclaim.yaml -f database-env-configmap.yaml -f database-deployment.yaml -f database-service.yaml -f redmine-deployment.yaml -f redmine-service.yaml

And then apply Redmine deployment and service (which includes exposing it on a loadbalancer)

$ kubectl apply -f redmine-deployment.yaml -f redmine-service.yaml

That's it the redmine will be working on the load balancer IP
