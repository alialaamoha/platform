# Use python base for better compatibility with Python/Ansible
FROM python:3.10.12-slim-bullseye

ENV SEMAPHORE_DB_USER=semaphore
ENV SEMAPHORE_DB_PASS=semaphore
ENV SEMAPHORE_DB_HOST=postgres
ENV SEMAPHORE_DB_PORT=5432
ENV SEMAPHORE_DB_DIALECT=postgres
ENV SEMAPHORE_DB=semaphore
ENV SEMAPHORE_PLAYBOOK_PATH=/tmp/semaphore/
ENV SEMAPHORE_ADMIN_PASSWORD=changeme
ENV SEMAPHORE_ADMIN_NAME=admin
ENV SEMAPHORE_ADMIN_EMAIL=admin@localhost
ENV SEMAPHORE_ADMIN=admin
ENV SEMAPHORE_ACCESS_KEY_ENCRYPTION=gs72mPntFATGJs9qK0pQ0rKtfidlexiMjYCH9gWKhTU=


RUN apt-get -y update && apt-get -y install git wget gettext curl tar


# Install kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" && \
    chmod +x kubectl && \
    mv kubectl /usr/local/bin/

# Install Ansible
RUN git clone https://github.com/kubernetes-sigs/kubespray /tmp/kubespray
RUN cd /tmp/kubespray && pip install -U -r requirements.txt

ARG SEMAPHORE_VERSION=2.13.12
RUN cd /tmp && wget https://github.com/ansible-semaphore/semaphore/releases/\
download/v${SEMAPHORE_VERSION}/semaphore_${SEMAPHORE_VERSION}_linux_amd64.deb 
RUN dpkg -i /tmp/semaphore_${SEMAPHORE_VERSION}_linux_amd64.deb

# Copy semaphore config
COPY config_template.json /semaphore/config_template.json
COPY entrypoint.sh /semaphore/entrypoint.sh
RUN chmod +x /semaphore/entrypoint.sh

# Clean up
RUN rm -rf /tmp/kubespray && rm -rf /tmp/semaphore_${SEMAPHORE_VERSION}_linux_amd64.deb 
# Startup process
ENTRYPOINT ["/semaphore/entrypoint.sh"]