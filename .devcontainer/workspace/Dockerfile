FROM node:14.18.2-alpine3.14

# install Docker CLI
RUN apk update && \
apk add docker-cli && \
apk add docker-compose && \
apk add less && \
apk add unzip && \
apk add curl && \
apk add sudo && \
apk add musl-dev && \
apk add gcc  && \
apk add python3 && \
apk add python3-dev && \
apk add bash

# install glibc
ENV GLIBC_VER=2.34-r0
RUN apk --no-cache add binutils curl && \
curl -sL https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub -o /etc/apk/keys/sgerrand.rsa.pub && \
curl -sLO https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_VER}/glibc-${GLIBC_VER}.apk && \
curl -sLO https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${GLIBC_VER}/glibc-bin-${GLIBC_VER}.apk && \
apk add --no-cache glibc-${GLIBC_VER}.apk glibc-bin-${GLIBC_VER}.apk

# install aws cliv2
RUN curl -sL https://awscli.amazonaws.com/awscli-exe-linux-x86_64-2.4.6.zip -o awscliv2.zip
RUN unzip awscliv2.zip
RUN aws/install

# install aws sam
RUN python3 -m ensurepip --upgrade && pip3 install --upgrade pip
RUN pip3 install --upgrade aws-sam-cli==1.36.0
RUN pip3 uninstall --yes pip && apk del python3-dev gcc musl-dev

# install cdk and ts
RUN yarn global add 'typescript@4.5.4' 'aws-cdk@2.2.0'