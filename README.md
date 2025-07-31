# Flask App on AWS ECS Fargate

This project showcases a basic Python Flask web application deployed to **AWS ECS Fargate** using **Amazon ECR**. The app runs inside a Docker container and returns a simple message when accessed from a browser.

---

## 🧰 Tech Stack

- Python 3.9
- Flask
- Docker
- AWS ECR (Elastic Container Registry)
- AWS ECS Fargate
- AWS VPC, Subnet, Security Group

---

## deployment

docker build -t flask-ecs-app .

aws ecr create-repository --repository-name flask-ecs-app
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <your-account-id>.dkr.ecr.us-east-1.amazonaws.com
docker tag flask-ecs-app:latest <your-account-id>.dkr.ecr.us-east-1.amazonaws.com/flask-ecs-app:latest
docker push <your-account-id>.dkr.ecr.us-east-1.amazonaws.com/flask-ecs-app:latest

<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/72387fa0-c50f-4203-8e7f-8d1a035927da" />
<img width="975" height="548" alt="image" src="https://github.com/user-attachments/assets/7405f936-f6c9-4ea5-8ab6-1c8e3f37f6ec" />


## 📄 Application Code

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello from ECS Fargate!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)




