
# MT Backend Challenge

## Informa��es Gerais
Este projeto � uma API desenvolvida com .NET 8 para resolver um desafio backend. A API utiliza RabbitMQ para filas, PostgreSQL como banco de dados, e Cloudinary para armazenar imagens. O projeto � configurado para rodar em cont�ineres Docker, facilitando a implanta��o e gerenciamento dos servi�os.

## Tecnologias Utilizadas
- **.NET 8** � Desenvolvimento da API
- **RabbitMQ** � Sistema de filas para comunica��o entre processos
- **PostgreSQL** � Banco de dados relacional
- **Cloudinary** � Armazenamento de imagens na nuvem
- **Docker/Docker Compose** � Cont�ineriza��o e orquestra��o de servi�os
- **RabbitMQ Management** � Interface web de gerenciamento de filas

## Estrutura da API
- **MT.Backend.Challenge.Api**: Ponto de entrada e implementa��o dos endpoints
- **MT.Backend.Challenge.Application**: Camada de aplica��o para regras de neg�cio
- **MT.Backend.Challenge.CrossCutting**: Configura��es e depend�ncias comuns
- **MT.Backend.Challenge.Domain**: Entidades e contratos de dom�nio
- **MT.Backend.Challenge.Infrastructure**: Implementa��es de acesso a dados e integra��o com servi�os externos

## Estrutura dos Controllers
- **DeliveryDriverController.cs**: Gerenciamento de motoristas de entrega
- **MotorcycleController.cs**: Opera��es relacionadas a motocicletas
- **RentalController.cs**: Funcionalidades de aluguel de ve�culos

## Como Subir a Aplica��o
### Pr�-requisitos:
- Docker instalado na m�quina


### Passos:
1. Clone o reposit�rio em sua m�quina:
   ```
   git clone https://github.com/bisslee/desafio-backend-mt
   cd MT.Backend.Challenge
   ```

2. Execute o Docker Compose para subir os servi�os:
   ```
   docker-compose up -d
   ```

3. Acesse os servi�os:
   - PostgreSQL: **localhost:5432**
   - RabbitMQ Management: **localhost:15672** (usu�rio: `guest`, senha: `guest`)

5. A API estar� dispon�vel em: **http://localhost:5000**

## Informa��es de Contato
Autor: Ivana Santos
Email: biss.lee@gmail.com  
