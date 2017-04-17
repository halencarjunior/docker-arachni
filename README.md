# Arachni v.1.5.1 - WebUI v0.5.12 - DOCKER

[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)

## Criando Imagem Docker do Arachni 

## Baixando e Configurando o Postgres
```
$ docker pull postgres
```
As credenciais estao no padrão do database.yml, caso queira alterar é necessário fazer também nos arquivos de configuração
```
$ docker run --name postgres -e POSTGRES_PASSWORD=secret -e POSTGRES_USER=arachni -e POSTGRES_DB=arachni_production -d postgres
```

## Dockerfile e database.yml da Imagem

Após o banco instalado, baixar o Dockerfile e o database.yml para criar sua imagem do Arachni localmente
```
$ git clone https://github.com/halencarjunior/docker-arachni.git
```
Para construir a imagem, digite:
```
$ docker build -t arachni:latest .
```
Com a finalização, vamos dar start na nossa imagem 
```
$ docker run -t --name arachni --link postgres -p 9292:9292 arachni:latest
```
Agora em outro terminal vamos executar o bash no nosso container para configurar as tabelas do Arachni
```
$ docker exec -i -t arachni /bin/bash
```
Depois de conectado, executamos dentro do container o comando:
```
$ arachni_web_task db:setup
```
Agora podemos acessar nossa Web_ui do Arachni pelo endereço:

http://localhost:9292

As credenciais de admin são:

login: admin@admin.admin

senha: administrator
