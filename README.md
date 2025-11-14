Voting app deployment
To reach the application using the hostnames vote.local and result.local you need to first run "minikube tunnle" and put the ingress service's external IP in /etc/hosts
Then deploy the applications using kubectl apply -f .
