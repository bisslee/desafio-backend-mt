# README - Instru��es para instalar e rodar SonarQube usando Docker


### Passo 1: Instalar Docker
Certifique-se de que o Docker est� instalado e rodando em seu sistema. Se ainda n�o estiver instalado, siga as instru��es de instala��o dispon�veis em [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/).

### Passo 2: arquivo docker-compose.yml
Na pasta [raiz-projeto]/scripts/sonar-local, voc� encontrar� um arquivo chamado `docker-compose.yml`.


### Passo 3: Rodar o Docker Compose
Abra o terminal, navegue at� o diret�rio onde o arquivo `docker-compose.yml` est� salvo e execute o comando abaixo para iniciar o SonarQube:

```
docker-compose up -d
```

Esse comando vai baixar a imagem do SonarQube e iniciar um container com base nas configura��es especificadas no arquivo `docker-compose.yml`.

### Passo 4: Acessar o SonarQube
Ap�s iniciar o container, voc� pode acessar a interface do SonarQube atrav�s do navegador, utilizando o seguinte endere�o:

- **URL:** [http://localhost:9000](http://localhost:9000)

- **Usu�rio padr�o:** admin
- **Senha padr�o:** admin

### Passo 5: Parar o Container
Para parar o container, execute o seguinte comando:

```
docker-compose down
```

Isso encerrar� o container e liberar� os recursos utilizados.

## Instalar o SonarScanner e dotnet-coverage
Ainda no terminal:

1. Instalar o SonarScanner

```bash

  dotnet tool install --global dotnet-sonarscanner

```

2. Instalar o dotnet-coverage

```bash

  dotnet tool install --global dotnet-coverage

```
### Configurar um projeto no SonarQube

Apos a instala��o do SonarQube, � necess�rio configurar um projeto para que o SonarQube possa validar a qualidade do seu c�digo.

A premissa nesse documento � rodar o sonar local.

1. Na p�gina inicial do SonarQube, clique em "**Create new project**"

![Sonar Qube Initial](SonarQubeInitial.png)

2. Preencha as informa��es do projeto e clique em "**Next**"

> Coloque o nome do projeto em **Project display name**.

![Sonar Qubeproject](SonarQubeproject.png)

3. Escolha a configura��o do seu projeto e clique em "**Create project**"

> geralmente escolhemos o **Use the global settings**, caso tenha d�vidas, consulte o time de Arquitetura.

4. Ap�s a cria��o do projeto, � necess�rio escolher o M�todo de an�lise. Usaremos o **Locally**.

![Sonar Qube Analysis Method](SonarQubeAnalysisMethod.png)

5. Precisamos criar um token-name e gerar um token para o projeto. Preencha um nome e clique em "**Generate**"

![Sonar Qube Token Generate](SonarQubeTokenGenerate.png)

e clique em "**Continue**"

![Sonar Qube Token Generate](SonarQubeTokenGenerateContinue.png)

 6. Escolha a linguagem do seu projeto:

 > Nesse caso, escolheremos **C#** e **.NET Core**.

 ![Sonar Qube Language](SonarQubeLanguage.png)

 > Note que ele apresenta os comando para rodar o sonar local.
 > Copie o arquivo  [raiz-projeto]/scripts/sonar.local.bat, para a raiz do projeto, e l� altere com as informa��es do seu projeto.

 Altere conforme abaixo:

```bash Bat do template
cls
Echo Iniciando o sonar 
dotnet sonarscanner begin /k:"[trocar-por-sonar-project-name]" /d:sonar.host.url="http://localhost:9000" /d:sonar.language="cs" /d:sonar.exclusions="**/*Development.json,**/bin/**/*,**/obj/**/*"  /d:sonar.token="[trocar-por-sonar-token]" /d:sonar.cs.vscoveragexml.reportsPaths=coverage.xml

dotnet restore

dotnet build --no-incremental
dotnet-coverage collect "dotnet test" -f xml -o "coverage.xml"

dotnet sonarscanner end /d:sonar.token="[trocar-por-sonar-token]"
Echo Finalizando o sonar, aperte qq tecla para continuar

pause

```

Onde **nome-projeto** � o nome do projeto criado no SonarQube e **[trocar-por-sonar-token]** � o token gerado.

Agora, execute o arquivo sonar.local.bat. e veja o resultado no SonarQube no navegador.

> para projetos em Macs ou linux, use o arquivo sonar.local.sh.
