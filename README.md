# gds-ephem-etl-deploy

Este repositório possui um exemplo de deploy do app de ETL do GDS Ephem (https://github.com/GleytonLima/gds-ephem-etl).

## Pré-requisitos

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Como executar

1. Clone o repositório
2. Crie um arquivo `.env` na raiz do projeto com as variáveis de ambiente necessárias para o deploy. Veja o arquivo `.env.example` para saber quais variáveis são necessárias.

O arquivo .env deve conter as seguintes variáveis:

| Variável           | Descrição                                                               | Exemplo                       |
| ------------------ | ----------------------------------------------------------------------- | ----------------------------- |
| ETL_DB_HOST        | Host do banco de dados                                                  | db                            |
| ETL_DB_PORT        | Porta do banco de dados                                                 | 5432                          |
| ETL_DB_SCHEMA_NAME | Nome do schema do banco de dados                                        | etl_ephem                     |
| ETL_DB_USERNAME    | Usuário do banco de dados                                               | user                          |
| ETL_DB_PASSWORD    | Senha do banco de dados                                                 | password                      |
| LOGZIO_TOKEN       | Token do Logz.io, um serviço gratuíto para gerenciamento básico de logs | tokenenviologs                |
| JVM_OPTIONS        | Opções de JVM para o container do app de ETL                            | -Dspring.profiles.active=prod |

3. Execute o comando `docker-compose up -d` para iniciar o deploy.

## Como parar

Para parar o deploy, execute o comando `docker-compose down`.

## Sobre o projeto

Detalhes sobre o projeto podem ser encontrados no repositório do app de ETL (https://github.com/GleytonLima/gds-ephem-etl)

O deploy é feito utilizando o Docker Compose. O arquivo `docker-compose.yml` possui a configuração dos serviços necessários para o deploy.

Veja que o arquivo docker-compose.yml possui uma seção `networks` com a configuração de uma rede. Essa rede é utilizada para que os serviços possam se comunicar entre si. O nome da rede utilizado é gds_default. Caso você já possua uma rede com esse nome, altere o nome da rede no arquivo `docker-compose.yml` para um nome que não esteja sendo utilizado.
