# Use official base image with Node.js, yarn, git, etc.
FROM mcr.microsoft.com/devcontainers/javascript-node:20

# Install additional tools and languages
RUN apt-get update && \
    apt-get install -y \
    openjdk-17-jdk \
    python3-pip \
    unzip \
    wget \
    curl \
    gnupg \
    software-properties-common \
    lsb-release \
    ca-certificates && \
    pip3 install --upgrade pip && \
    rm -rf /var/lib/apt/lists/*

# Install Docker CLI
RUN curl -fsSL https://get.docker.com | sh

# Install Docker Compose
RUN curl -L "https://github.com/docker/compose/releases/download/v2.24.1/docker-compose-linux-x86_64" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose

# Install kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" && \
    install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl && \
    rm kubectl

# Install .NET SDK for C#
RUN wget https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && \
    dpkg -i packages-microsoft-prod.deb && \
    apt-get update && \
    apt-get install -y dotnet-sdk-7.0 && \
    rm packages-microsoft-prod.deb

# Set env
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
ENV PATH=$PATH:/usr/lib/jvm/java-17-openjdk-amd64/bin
