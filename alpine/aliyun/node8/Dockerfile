FROM node:8-alpine
LABEL maintener: YukiMiyatake<YukiMariaMiyatake@gmail.com>

WORKDIR /root
ENV HOME /root

#apk
RUN apk update && apk add curl unzip wget
#RUN pip install --upgrade pip

#ngrok
RUN curl -O https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip \
    && unzip ngrok-stable-linux-amd64.zip
ENV PATH=$HOME/ngrok/bin:$PATH


RUN apk add  py-pip 
#Alibaba
#RUN pip3 install -U aliyun-log-cli 
#COPY --from=builder /go/src/github.com/aliyun/aliyun-cli/out/aliyun /usr/local/bin

#RUN apk add libsecret-1-dev
#serverless framework
RUN npm install -g -y serverless 
RUN npm install -g serverless-aliyun-function-compute

WORKDIR /src


RUN \
  apk add --no-cache build-base && \
  pip install aliyuncli && \
  apk del build-base && \
  rm -rf /tmp/*
#serverless create --template azure-nodejs --path my-service --name my-unique-name
#dotnet resutore  dotnet build
#CMD [ngrok http -host-header="0.0.0.0:7071" 7071]


