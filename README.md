#1. Create a virtual environment
#python3 -m venv ~/ollama-env

#2. Activate it
#source ~/ollama-env/bin/activate
#You’ll now see something like:
#(ollama-env) MacBook:~ user$

#3. Install packages inside the requirement.txt
#pip install ollama
#And run your script:
#python app.py

Test using the link below and change the localhost according to your own localhost
curl -X POST http://localhost:8000/chat \
  -H "Content-Type: application/json" \
  -d '{"question": "What does Hugging Face provide?", "context": "Hugging Face is a technology company that provides open-source NLP libraries and tools for machine learning."}'

4. dockerize
docker build -t fastapi-app .
docker run -p 8000:8000 fastapi-app

5. install trivy 
brew install aquasecurity/trivy/trivy

6. scan docker image for vulnerability 
trivy image --severity HIGH,CRITICAL <image_name> --output output/trivy_report.txt

7. tag and push docker image to ecr
docker tag <image-name>:<tag> <your-ecr-registry-uri>/<repository-name>:<tag>
docker push <your-ecr-registry-uri>/<repository-name>:<tag>

8.Deploy and verify deployments to Kubernetes
• kubectl apply –f deployment.yaml
• kubectl apply –f service.yaml
• kubectl get deploy
• kubectl get services

9.Install kube-score
brew install kube-score/tap/kube-score

10.Validate Kubernetes Manifests with kube-score
kube-score score --output-format ci deployment.yaml

*SignUp Digital Ocean & Install doctl*
*Install helm*

11.Create Kubernetes cluster
doctl kubernetes cluster create my-cluster --region nyc1 --node-
pool "name=default;size=s-2vcpu-4gb;count=2" --version 1.33.1-do.2

// To change the version
*doctl kubernetes options sizes*

12.Get Kubeconfig for Cluster
doctl kubernetes cluster kubeconfig save my-cluster

13.Verify Cluster
kubectl get nodes

14.Tag & Push Docker Image
docker tag <image-name>:<tag> <username>/<repository-name>:<tag>
docker push <username>/<repository-name>:<tag>

15.Deploy Image on DOKS
kubectl apply –f deployment.yaml –f service.yaml

16.Install ingress-nginx repo
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install ingress-nginx ingress-nginx/ingress-nginx --create-namespace --namespace ningress-nginx

17.Monitor Until All Resources Deployed
kubectl get all –ningress-nginx

18.Test service without Ingress
kubectl port-forward svc/gpt-hf-service 8000:8000

Remove kubernetes port forwarding
• ps aux | grep "kubectl port-forward”
• kill <PID>

Test
curl -X POST http://localhost:8000/chat -H "Content-Type: application/json" -d '{"question": "What does Hugging Face provides?", "answer": "Hugging Face is a technology company that provides pen-source NLP libraries ..."}'

19.Get Ingress External IP Address
kubectl get svc -ningress-nginx

20. Update the service.yaml

21. Deploy the service.yaml
kubectl apply –f service.yaml

22.Test the application
curl -X POST http://gpt.<YOUR_OWN_EXTERNAL_IP>.sslip.io/chat -H "Content-Type: application/json" -d '{"question": "What does Hugging Face provides?", "answer": "Hugging Face is a technology company that provides pen-source NLP libraries ..."}'

#To exit later:
#deactivate
