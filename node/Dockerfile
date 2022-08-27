# Iniciando uma imagem base node com versão 15
FROM node:15
# definando autor da imagen
LABEL maintainer="Fabricio Alingeri"
# diretório de trabalho
WORKDIR /usr/src/app
# Copiando o app
COPY . .
#instala node
RUN npm install
#atualzando sistema e instalando o wget
RUN apt-get update && apt-get install -y wget

#Dockerize é necessário para sincronizar a inicialização dos containers
ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

#expondo por 3000 para node
EXPOSE 3000

# Define um caminho onde o comando definido e executa comando para node
ENTRYPOINT [ "node", "index.js" ]