# README - Instru��es para instalar e rodar PostgreSQL usando Docker

### Passo 1: Instalar Docker
Certifique-se de que o Docker est� instalado e rodando em seu sistema. Se ainda n�o estiver instalado, siga as instru��es de instala��o dispon�veis em [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/).

### Passo 2: arquivo docker-compose.yml
Na pasta [raiz-projeto]/scripts/postgres, voc� encontrar� um arquivo chamado `docker-compose.yml`. Abra esse arquivo em um editor de texto e verifique as configura��es do servi�o PostgreSQL. 


### Passo 3: Rodar o Docker Compose
Abra o terminal, navegue at� o diret�rio [raiz-projeto]/scripts/postgres e execute o comando abaixo para iniciar o PostgreSQL:

```
docker-compose up -d
```

Esse comando vai baixar a imagem do PostgreSQL e iniciar um container com base nas configura��es especificadas no arquivo `docker-compose.yml`.

### Passo 4: Acessar o PostgreSQL
Ap�s iniciar o container, voc� pode acessar o banco de dados PostgreSQL utilizando qualquer ferramenta de cliente PostgreSQL, como `psql`, DBeaver ou PgAdmin. 

- **Host:** localhost
- **Porta:** 5432
- **Usu�rio:** myuser
- **Senha:** mypassword
- **Banco de Dados:** challenge_db

### Passo 5: Connection String para Entity Framework
Se voc� for utilizar o Entity Framework e o Migration para criar a base, a connection string deve ser configurada da seguinte maneira:

```
"ConnectionStrings": {
  "DefaultConnection": "Host=localhost;Port=5432;Database=challenge_db;Username=myuser;Password=mypassword"
}
```

### Passo 6: Parar o Container
Para parar o container, execute o seguinte comando:

```
docker-compose down
```

Isso encerrar� o container e liberar� os recursos utilizados.

