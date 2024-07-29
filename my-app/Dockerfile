FROM node:alpine

WORKDIR /app/
COPY package.json /app/

RUN npm install -g serve
    
COPY . /app/
 
# Start and enable SSH
RUN apk add openssh \
     && echo "root:Docker!" | chpasswd \
     && chmod +x /app/init_container.sh \
     && cd /etc/ssh/ \
     && ssh-keygen -A

COPY sshd_config /etc/ssh/

EXPOSE 3000

ENTRYPOINT [ "/app/init_container.sh" ]