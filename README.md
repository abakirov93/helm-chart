# helm-wordpress

*installed with helm v2

*   Commands:

helm version 
#when you run above command it must show version-3…

sudo mv /usr/local/bin/helm /usr/local/bin/helm3 
#first move helm3 then start installing helm2

wget https://get.helm.sh/helm-v2.16.9-linux-amd64.tar.gz 
#this is the package that we going to install

tar -xf helm-v2.16.9-linux-amd64.tar.gz   

sudo mv linux-amd64/helm /usr/local/bin/helm 
#after you run tar command move helm to bin folder

helm version 
#it must show helm version-2…

kubectl create sa -n kube-system tiller 
#by running this command you will create serviceaccount

kubectl create clusterrolebinding tiller-cluster-admin --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
#it creates "kube-system" 

helm init --service-account tiller --upgrade  
#it will upgrade

cd helm-wordpress/ 
#from here continue by getting in this folder"

#Inside "value-yaml", change the namespace to yours. Default is beks-task.

helm install wordpress-mysql-helm-chart   

kubectl get service -n beks-task 
#if you don't specify namespace it may not show you the pods

#Once you successfully completed, get the load balancer IP and paste it on the Internet Browser
#Also you can check it by going to the GCP account and in Kubernetes Engine portal, click Services and Ingress.
