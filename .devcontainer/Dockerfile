FROM node:20.6-slim

ENV TZ Asia/Tokyo

# install golang and setting
RUN apt-get update && apt-get install -y \
    curl \
    && apt-get clean \
    && apt-get install wget \
    && apt-get install unzip \
    && apt-get install -y git
RUN wget https://dl.google.com/go/go1.21.0.linux-amd64.tar.gz
RUN tar -C /usr/local -xzf go1.21.0.linux-amd64.tar.gz
RUN rm -rf go1.21.0.linux-amd64.tar.gz
ENV PATH $PATH:/usr/local/go/bin
RUN go install github.com/ramya-rao-a/go-outline@latest
RUN go install github.com/cweill/gotests/gotests@latest
RUN go install github.com/fatih/gomodifytags@latest
RUN go install github.com/josharian/impl@latest
RUN go install github.com/haya14busa/goplay/cmd/goplay@latest
RUN go install github.com/go-delve/delve/cmd/dlv@latest
RUN go install honnef.co/go/tools/cmd/staticcheck@latest
RUN go install golang.org/x/tools/gopls@latest

# install AWS CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64-2.13.25.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip
RUN ./aws/install
RUN rm -rf awscliv2.zip
RUN rm -rf /aws

# install AWS CDK
RUN npm install -g aws-cdk@2.94.0
