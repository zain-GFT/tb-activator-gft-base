FROM golang:alpine
MAINTAINER "GFT"

ENV TERRAFORM_VERSION=0.12.24
ENV ACTIVATOR_NAME=tb-activator-gft-base

RUN apk add --update git bash openssh python3 wget unzip

RUN wget https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip

RUN unzip ./terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    mv terraform /usr/bin/ && rm -f terraform_${TERRAFORM_VERSION}_linux_amd64.zip

RUN git clone https://github.com/tranquilitybase-io/tb-activator-gft-base.git
RUN mkdir /opt/app/ && mkdir /opt/app/data
COPY service-account.json /opt/app/data/.

