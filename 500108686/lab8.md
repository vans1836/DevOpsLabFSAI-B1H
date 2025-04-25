# DevOps Lab 8 – Automating Docker Builds with GitHub Actions

**Repository:** [GitHub - Lab 8]

In this lab, we extended our containerized FastAPI application by automating its Docker image build and push process using **GitHub Actions**.

GitHub Actions is a CI/CD platform provided by GitHub that enables us to create custom workflows for building, testing, and deploying applications right from our GitHub repository.

---

## Objective

To automate the build process of a Dockerized FastAPI application and push the image to Docker Hub every time code is pushed to the repository.

---

## GitHub Actions Workflow Breakdown

**File Location:** `.github/workflows/DockerBuild.yml`

### Workflow Details

- **name: Docker image build**
  - This is the name assigned to the GitHub Actions workflow.

- **on: push**
  - The workflow is triggered automatically on every push to the repository.

### Jobs and Steps

- **jobs: build**
  - Defines a job called `build` that contains all the steps required to automate the process.

- **runs-on: ubuntu-latest**
  - Specifies that the job will run on the latest version of an Ubuntu virtual machine.

### Steps Explained

1. **Checkout code**
   ```yaml
   - uses: actions/checkout@v3
   ```
   - This checks out the source code from the repository into the workflow.

2. **Check for secret**
   - Ensures that the Docker token is present in GitHub secrets.

3. **Log in to Docker Hub**
   ```yaml
   - name: Docker Login
     run: echo ${{ secrets.DOCKERTOKEN }} | docker login -u "your-docker-username" --password-stdin
   ```

4. **Build Docker Image**
   ```yaml
   - name: Build Docker Image
     run: docker build -t your-docker-username/fastapi-app:v0.1 .
   ```

5. **Push Docker Image to Docker Hub**
   ```yaml
   - name: Push Docker Image
     run: docker push your-docker-username/fastapi-app:v0.1
   ```

---

## Outcome

This GitHub Actions workflow automates:
- Building the Docker image
- Logging into Docker Hub
- Pushing the image

This ensures a **faster**, **more consistent**, and **automated deployment** process for your containerized FastAPI application.

---
**Author:** Vanshika Agarwal
