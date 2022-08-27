# Iniciando uma imagem base nginx com ultima versão
FROM nginx:latest
# definando autor da imagen
LABEL maintainer="Fabricio Alingeri"

# removendo nginx.conf
RUN rm /etc/nginx/nginx.conf
# Copiando nginx.conf de dentro do projeto para imagem
COPY nginx.conf /etc/nginx/nginx.conf
#atualzando sistema e instalando o wget
RUN apt-get update && apt-get install -y wget

#Dockerize é necessário para sincronizar a inicialização dos containers
ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

#expondo por 80 para nginx
EXPOSE 80

# Define um caminho onde o comando definido e executa comando para nginx
ENTRYPOINT [“nginx”, “-D”, “daemon off;”]