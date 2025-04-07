# vscode-dev-continers

[Dev Continer yourtube series](https://learn.microsoft.com/en-us/shows/beginners-series-to-dev-containers/?wt.mc_id=devcloud-11496-cxa)

### What Are VS Code Dev Containers?
VS Code **Dev Containers** allow you to use a **Docker container** as a full-featured development environment. This means you can work inside a containerized setup with all dependencies pre-installed, ensuring consistency across different machines. It’s particularly useful for:
- **Standardized development environments** across teams.
- **Isolated dependencies** without affecting your local system.
- **Easy onboarding** for new developers—just open the project in a container!

You define a **dev container** using a `.devcontainer/devcontainer.json` file, which tells VS Code how to configure the container.

---

### 🚀 Step-by-Step Guide to Master Dev Containers

#### **1️⃣ Install Prerequisites**
Before using Dev Containers, install:
- **VS Code** ([Download](https://code.visualstudio.com/))
- **Docker** ([Install Docker](https://www.docker.com/get-started))
- **Dev Containers Extension** ([Install](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers))

---

#### **2️⃣ Create a Dev Container Configuration**
Inside your project, create a `.devcontainer` folder and add a `devcontainer.json` file:

```json
{
  "name": "My Dev Container",
  "image": "mcr.microsoft.com/devcontainers/typescript-node:latest",
  "features": {
    "ghcr.io/devcontainers/features/docker-in-docker:latest": {}
  },
  "forwardPorts": [3000],
  "extensions": ["ms-python.python", "dbaeumer.vscode-eslint"]
}
```
This configuration:
- Uses a **pre-built Node.js container**.
- Installs **Docker-in-Docker** for running containers inside the dev container.
- **Forwards port 3000** for web development.
- **Installs VS Code extensions** inside the container.

---

#### **3️⃣ Open Your Project in a Dev Container**
1. Open VS Code.
2. Press `Ctrl + Shift + P` and select **"Dev Containers: Reopen in Container"**.
3. VS Code will **build the container** and restart inside it.

---

#### **4️⃣ Customize Your Dev Container**
You can add a **Dockerfile** for custom dependencies:

```dockerfile
FROM mcr.microsoft.com/devcontainers/python:latest
RUN pip install flask
```
Then, update `devcontainer.json`:

```json
{
  "build": {
    "dockerfile": "Dockerfile"
  }
}
```
Now, VS Code will **build the container using your custom Dockerfile**.

---

#### **5️⃣ Use Docker Compose for Multi-Container Projects**
For complex setups (e.g., **Node.js + PostgreSQL**), use `docker-compose.yml`:

```yaml
version: '3'
services:
  app:
    build: .
    volumes:
      - .:/workspace
    ports:
      - "3000:3000"
  db:
    image: postgres:latest
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```
Then, update `devcontainer.json`:

```json
{
  "dockerComposeFile": "docker-compose.yml",
  "service": "app"
}
```
Now, VS Code will **start both the app and database containers**.

---

### 🎯 Next Steps
- Explore **pre-built Dev Containers** ([List](https://containers.dev/))
- Learn advanced configurations ([Guide](https://code.visualstudio.com/docs/devcontainers/create-dev-container))
- Watch tutorials like [this one](https://www.youtube.com/watch?v=ELdZxGtqu6w) for hands-on learning.

Let me know if you need help setting up a specific environment! 🚀