# README - Instru��es para instalar e rodar RabbitMQ usando Docker

### Passo 1: Instalar Docker
Certifique-se de que o Docker est� instalado e rodando em seu sistema. Se ainda n�o estiver instalado, siga as instru��es de instala��o dispon�veis em [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/).

### Passo 2: arquivo docker-compose.yml
Na pasta [raiz-projeto]/scripts/sonar-local, voc� encontrar� um arquivo chamado `docker-compose.yml`.

### Passo 3: Rodar o Docker Compose
Abra o terminal, navegue at� o diret�rio onde o arquivo `docker-compose.yml` est� salvo e execute o comando abaixo para iniciar o RabbitMQ:

```
docker-compose up -d
```

Esse comando vai baixar a imagem do RabbitMQ e iniciar um container com base nas configura��es especificadas no arquivo `docker-compose.yml`.

### Passo 4: Acessar o RabbitMQ
Ap�s iniciar o container, voc� pode acessar a interface de gerenciamento do RabbitMQ atrav�s do navegador, utilizando o seguinte endere�o:

- **URL:** [http://localhost:15672](http://localhost:15672)

- **Usu�rio padr�o:** mtuser
- **Senha padr�o:** mt2024

### Passo 5: Parar o Container
Para parar o container, execute o seguinte comando:

```
docker-compose down
```

Isso encerrar� o container e liberar� os recursos utilizados.
