FROM ubuntu:18.04
LABEL maintener: YukiMiyatake<YukiMariaMiyatake@gmail.com>

WORKDIR /root
ENV HOME /root

#apt
RUN apt-get update && apt-get install -y curl unzip wget python python3-pip software-properties-common

#ngrok
RUN curl -O https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip \
    && unzip ngrok-stable-linux-amd64.zip
ENV PATH=$HOME/ngrok/bin:$PATH

#node
RUN apt-get install -y perl \
    && curl -L git.io/nodebrew | perl - setup
ENV PATH=$HOME/.nodebrew/current/bin:$PATH 
RUN ls -al $HOME/.nodebrew/current/bin
RUN echo $PATH

RUN echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> $HOME/.bashrc
RUN nodebrew install v8.10 \
    && nodebrew install v10.15 \
    && nodebrew use v10.15 
RUN npm config set user 0 \
    && npm config set unsafe-perm true
RUN npm update -g

#AWS-cli
RUN pip3 install awscli



RUN apt-get install -y libsecret-1-dev
#serverless framework
RUN npm install -g -y serverless 
RUN npm install -g serverless-azure-functions

#serverless create --template azure-nodejs --path my-service --name my-unique-name
#dotnet resutore  dotnet build
#CMD [ngrok http -host-header="0.0.0.0:7071" 7071]


