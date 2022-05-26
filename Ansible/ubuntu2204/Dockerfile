
FROM ubuntu:22.04

ENV ANSIBLE_VERSION=2.9.27

# Labels.
LABEL maintainer="DenAV" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.name="denav/ansible" \
    org.label-schema.description="Ansible inside Docker" \
    org.label-schema.url="https://github.com/DenAV/Docker" \
    org.label-schema.vcs-url="https://github.com/DenAV/Docker"\
    org.label-schema.build-date=$BUILD_DATE \
    org.label-schema.vcs-ref=$VCS_REF

RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    apt-get install -y python3-pip sshpass && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

RUN python3 -m pip install --upgrade pip && \
    pip install ansible==${ANSIBLE_VERSION} && \
    pip install --upgrade pywinrm && \
    pip install netaddr && \
    rm -rf /root/.cache/pip

RUN mkdir /ansible && \
    mkdir -p /etc/ansible && \
    echo 'localhost' > /etc/ansible/hosts

WORKDIR /ansible

CMD [ "ansible-playbook", "--version" ]