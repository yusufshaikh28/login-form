
# Login App — Jenkins CI/CD Pipeline

A simple login page deployed via a fully automated Jenkins CI/CD pipeline with Docker.

## Pipeline Stages

1. **Clone Repo** — pulls latest code from GitHub
2. **Build Docker Image** — builds the login app Docker image
3. **Run Container** — stops any existing container and deploys fresh on port 8081
4. **Deployment Link** — confirms deployment at `localhost:8081`

## Tech Stack

- **Frontend:** HTML, CSS
- **Containerization:** Docker, Nginx
- **CI/CD:** Jenkins
- **Pipeline:** Jenkinsfile (declarative pipeline)

## Running Locally

```bash
docker build -t login-app .
docker run -d -p 8081:80 --name login-container login-app
```

Then open `localhost:8081`

## Jenkins Setup

1. Create a new Pipeline job in Jenkins
2. Point it to this repo
3. Jenkins will automatically run all pipeline stages on each push

