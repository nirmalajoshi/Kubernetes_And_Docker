Steps to install Jenkins on Kubernetes using files in "Install_Jenkins_On_Kubernetes" folder
1.Create Namespace
kubectl create namespace jenkins

2.Create Deployment
kubectl create -f jenkins-deployment.yml -n jenkins

this deployment specifies single replica,the container image name is jenkins and version is 2.32.2.
Jenkins is running on port 8080

3.Create service to export the jenkins port,service type is NodePort
kubectl create -f jenkins-service.yml -n jenkins

4.Get pod details to access Jenkins
kubectl get pods -n jenkins

kubectl logs <pod name> -n jenkins

Check for password in logs.The default username is admin,to obtain password check pod logs and then you can change password later.

5.To access,get external ip with below command

minikube service jenkins -n jenkins

web browser will open jenkins webpage,put above password and create new password.

6.For interactive session in jenkins and to check file directories below command is used
kubectl exec -it <pod name>  -n jenkins
