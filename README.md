# Projeto Symfony Docker

Este repositório contém o código e as configurações para um projeto de aplicação back-end com Symfony, utilizando Docker para facilitar o ambiente de desenvolvimento e implantação. 

## Pré-requisitos

Antes de começar, certifique-se de atender aos seguintes pré-requisitos:

- Composer instalado globalmente na sua máquina.
- Área de Trabalho do Docker configurada e funcionando corretamente.

## Configuração

1. Clone este repositório para o seu sistema local.

2. Navegue até o diretório do projeto.

## Construir e Executar os Contêineres

- Para construir e executar os contêineres, utilize o seguinte comando:

```bash
docker-compose up -d
```
## Criar app Symfony

- Para criar o app Symfony, siga os passos abaixo:

1. Execute o seguinte comando para acessar o contêiner:

```bash
docker-compose exec php /bin/bash
```
2. Crie um novo projeto Symfony no diretório atual:

```bash
symfony new .
```
## Acesso ao Aplicativo Symfony

- Após os contêineres estarem em execução e o app criado, você poderá acessar o aplicativo Symfony no seu navegador através do endereço http://localhost:8080.

## Estrutura do Projeto

- O projeto é composto por dois serviços no arquivo docker-compose.yml:

1. Serviço PHP

Container Name: php
Porta do host mapeada: 9000
Volume mapeado: ./app:/var/www/symfony_docker
Extensões PHP instaladas: intl, opcache, pdo, pdo_mysql, zip, apcu

2. Serviço Nginx

Container Name: nginx
Imagem utilizada: nginx:stable-alpine
Porta do host mapeada: 8080
Volumes mapeados: ./app:/var/www/symfony_docker, ./nginx/default.conf:/etc/nginx/conf.d/default.conf
Dependências: Dependente do serviço PHP para garantir a ordem correta de inicialização

## Contribuindo

Se você deseja contribuir com este projeto, sinta-se à vontade para abrir uma issue ou enviar um pull request.

