FROM node:latest
LABEL maintainer="William Rodrigues" \
      maintainer.email=williamrodrigues2442@gmail.com

# Copia o código do site para a imagem quando um container for criado.
COPY . /var/exemplo

# Local onde estará o package.json para poder executar os comandos.
WORKDIR /var/exemplo

# Instala as dependências quando a imagem estiver sendo construída.
RUN npm install

# Comando que é executado assim que o container é criado.
ENTRYPOINT npm start

EXPOSE 3000
