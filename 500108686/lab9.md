
# FastAPI Dockerization & CI using GitHub Actions

Created by **Vanshika Agarwal**  
This guide explains how to containerize a FastAPI application and automate Docker image building and pushing using GitHub Actions.

---

## Step 1: Install Podman (Docker Alternative)

**Podman** is a container engine that can serve as a replacement for Docker.

### Installation

1. Download `podman-cli` from [https://podman.io](https://podman.io/)
2. Initialize Podman machine and configure alias:
   ```bash
   podman machine init
   podman machine start
   alias docker=podman
   docker --version
   ```

---

## Step 2: FastAPI Server Code

**File:** `main.py`

```python
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/")
def root():
    return {"name": "Vanshika", "Location": "Dehradun"}

@app.get("/{data}")
def dynamic(data: str):
    return {"hi": data, "Location": "Dehradun"}

if __name__ == "__main__":
    uvicorn.run("main:app", host="0.0.0.0", port=80, reload=True)
```

---

## Step 3: Requirements

**File:** `requirements.txt`

```
fastapi
uvicorn
```

---

## Step 4: Dockerfile

**File:** `Dockerfile`

```Dockerfile
FROM ubuntu

RUN apt update -y && apt install -y python3 python3-pip pipenv

WORKDIR /app
COPY . /app/
RUN pipenv install -r requirements.txt

EXPOSE 80
CMD pipenv run python3 ./main.py
```

---

## Step 5: Build and Run

### Build Image
```bash
docker build -t fastapi-vanshika:v1 .
```

### List Images
```bash
docker images
```

### Run Container
```bash
docker run fastapi-vanshika:v1
```

---

## Step 6: GitHub Actions Workflow

**File:** `.github/workflows/DockerBuild.yml`

```yaml
name: Docker image build

on: push

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: Build & Push Image
        run: |
          echo ${{ secrets.DOCKERTOKEN }} | docker login -u "vanshikaagarwal" --password-stdin
          docker build -t vanshikaagarwal/fastapi-docker:v0.1 .
          docker push vanshikaagarwal/fastapi-docker:v0.1
```

---

## Docker Token Setup

### Docker Hub Token

1. Visit [Docker Hub](https://hub.docker.com)
2. Go to **Account Settings > Security > Access Tokens**
3. Generate a token, give it a name, set permissions
4. Copy and store it securely (you’ll use this in GitHub Secrets)

Use the token to log in:
```bash
echo "<your-token>" | docker login -u <your-username> --password-stdin
```

---



