FROM alpine:latest
LABEL maintener: YukiMiyatake<YukiMariaMiyatake@gmail.com>

WORKDIR /root
ENV HOME /root

#apk
RUN apk update && apk add curl unzip wget py3-pip
RUN pip install --upgrade pip

#ngrok
RUN curl -O https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip \
    && unzip ngrok-stable-linux-amd64.zip
ENV PATH=$HOME/ngrok/bin:$PATH

#dotnet core
ENV DOTNET_VERSION 2.2.1
RUN wget -O dotnet.tar.gz https://dotnetcli.blob.core.windows.net/dotnet/Runtime/$DOTNET_VERSION/dotnet-runtime-$DOTNET_VERSION-linux-musl-x64.tar.gz \
    && dotnet_sha512='f76f8650aae126b2cdf55cce200d6400137288f5c0688e314575273ab9f87f364d06dcf0992524d8d6a127485ec11f8f6e9586a5b47604bf1f6396748b3e7fca' \
    && echo "$dotnet_sha512  dotnet.tar.gz" | sha512sum -c - \
    && mkdir -p /usr/share/dotnet \
    && tar -C /usr/share/dotnet -xzf dotnet.tar.gz \
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet \
    && rm dotnet.tar.gz

#node
RUN apk add perl \
    && curl -L git.io/nodebrew | perl - setup
ENV PATH=$HOME/.nodebrew/current/bin:$PATH 




RUN nodebrew install v8.10 \
    && nodebrew install v10.15 \
    && nodebrew use v10.15 
RUN npm config set user 0 \
    && npm config set unsafe-perm true
RUN npm update -g

#AWS-cli
#RUN curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py" \
#    python get-pip.py \
#    pip install awscli
RUN pip3 install awscli

#azure-cli
RUN pip3 --no-cache-dir install azure-cli

#GCP

#Alibaba
RUN pip3 install -U aliyun-log-cli 

RUN apt-get install -y libsecret-1-dev
#serverless framework
RUN npm install -g -y serverless 
RUN npm install -g serverless-azure-functions

WORKDIR /src

#serverless create --template azure-nodejs --path my-service --name my-unique-name
#dotnet resutore  dotnet build
#CMD [ngrok http -host-header="0.0.0.0:7071" 7071]


