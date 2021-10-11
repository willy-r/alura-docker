# Curso de Docker - Alura

Algumas anotações do [curso de Docker da Alura](https://cursos.alura.com.br/course/docker-e-docker-compose/).


## Comandos

Alguns comandos vistos nas aulas.

| Comando | Descrição |
| --- | --- |
| `docker version` | Exibe a versão e algumas outras informações do docker |
| `docker ps` | Exibe todos os containers em execução no momento |
| `docker ps -a` | Exibe todos os containers, independentemente de estarem em execução ou não |
| `docker run nome_da_imagem` | Cria um container com a respectiva imagem passada como parâmetro |
| `docker run -it nome_da_imagem` | Conecta o terminal atual com o do container |
| `docker run -d -P --name nome nome_da_imagem` | Ao executar, dá um nome ao container |
| `docker run -d -p 12345:80 nome_da_imagem` | Define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345 |
| `docker run -d -P -e AUTHOR='Fulano' nome_da_imagem` | Define uma variável de ambiente AUTHOR com o valor Fulano no container criado |
| `docker run -v caminho_volume_local:caminho_volume_container nome_da_imagem` | Cria um volume no respectivo caminho do container, caso seja especificado um caminho local monta o volume local no volume do container |
| `docker run --network nome_da_rede nome_da_imagem` | Roda o container com a rede especificada, o padrão é a rede default |
| `docker start id_container` | Inicia o container com id em questão |
| `docker stop id_container` | Interrompe o container com id em questão |
| `docker start -a -i id_container` | Inicia o container com id em questão e integra os terminais, além de permitir interação entre ambos |
| `docker inspect id_container` | Retorna diversas informações sobre o container |
| `docker rm id_container` | Remove o container com id em questão |
| `docker rmi nome_da_imagem` | Remove a imagem passada como parâmetro |
| `docker container prune` | Remove todos os containers que estão parados |
| `docker build -f Dockerfile` | Cria uma imagem a partir de um Dockerfile |
| `docker build -f caminho_dockerfile/Dockerfile -t nome_usuario/nome_imagem` | Constrói e nomeia uma imagem não-oficial informando o caminho para o Dockerfile |
| `docker login` | Inicia o processo de login no Docker Hub |
| `docker push nome_usuario/nome_imagem` | Envia a imagem criada para o Docker Hub |
| `docker pull nome_usuario/nome_imagem` | Baixa a imagem desejada do Docker Hub |
| `docker network create --driver bridge nome_da_rede` | Cria uma rede usando o driver bridge com o nome da rede especificado |
| `docker network ls` | Lista as redes disponíveis |
| `docker network inspect nome_da_rede` | Inspeciona a rede mostrando algumas configurações e também containers que estão usando ela |
| `docker-compose build` | Realiza o build dos serviços relacionados ao arquivo docker-compose.yml, assim como verifica a sua sintaxe |
| `docker-compose up` | Sobe todos os containers relacionados ao docker-compose, desde que o build já tenha sido executado |
| `docker-compose down` | Para todos os serviços em execução que estejam relacionados ao arquivo docker-compose.yml |
| `docker-compose ps` | Mostra todos os containers rodando no momento |


## Anotações

### Sobre containers

- Um **container** contém a aplicação, ela é executada dentro do container. Um container divide o uso do SO igualmente.

- Ganhos sobre uso de containers:
  - Melhor controle sobre uso de cada recurso (CPU, Disco, Rede, etc)
  - Agilidade na hora de trabalhar com diferentes versões de linguagens e bibliotecas
  - Mais leves que as VM's pois não usam o SO embutidos
    
### Sobre volumes

- Volumes é uma forma de você salvar as alterações feitas em um container localmente, para que as alterações permaneçam mesmo após a destruição do container.

### Sobre Dockerfile

- O Dockerfile define os comandos para executar instalações complexas e com características específicas.

- Normalmente possui o nome `Dockerfile`, mas pode ser usado de outras formas como `node.dockerfile`.

- Se for usar outro nome, quando for executar o build, a flag `-f` deverá ser usada: `docker build -f node.dockerfile`.

- Principais comandos:
  - `FROM`
  - `COPY`
  - `WORKDIR`
  - `RUN`
  - `EXPOSE`
  - `ENTRYPOINT`

### Sobre relacionamento de containers

- Por padrão o Docker cria uma rede em que todos os containers estão fazendo parte dessa rede, e automaticamente eles possuem os IP's atribuídos.

- Para fazer os containers se comunicarem é preciso criar uma rede, e atribuir nomes aos containers para que eles posssam ser achados.

- `hostname -i` irá mostrar o ip atribuído ao container pelo Docker (só funciona dentro do container).

### Sobre docker-compose

- [docker-compose.yml](Aqui) você vê um exemplo de um arquivo *docker-compose*, ele é escrito no formato **YML**, nesse exemplo ele sobe uma simples aplicação e um simples banco de dados, ligando-os a mesma rede e fazendo eles se comunicarem. 

- O arquivo `docker-compose` é uma forma de criar uma "receita" que diz para o Docker como executar os comandos contidos nele, isso é bom para evitar ficar escrevendo os comandos na linha de comando.


## Referências

- https://docs.docker.com/compose/compose-file/
- https://docs.docker.com/engine/reference/builder/
