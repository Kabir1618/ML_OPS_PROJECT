# Start from Jenkins LTS image
FROM jenkins/jenkins:lts

# Switch to root
USER root

# Install Docker (CLI + Daemon)
RUN apt-get update -y && \
    apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" \
        > /etc/apt/sources.list.d/docker.list && \
    apt-get update -y && \
    apt-get install -y docker-ce docker-ce-cli containerd.io && \
    apt-get clean

# Add Jenkins to the docker group
RUN groupadd -f docker && usermod -aG docker jenkins

# Create Docker data directory
RUN mkdir -p /var/lib/docker
VOLUME /var/lib/docker

# Expose Docker socket inside the container
EXPOSE 2375

# Switch back to Jenkins user
USER jenkins
