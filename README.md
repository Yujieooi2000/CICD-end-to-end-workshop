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

5. install trivy using docker
docker pull aquasec/trivy:latest

#To exit later:
#deactivate
