# docker-arachni
Criando Imagem Docker do Arachni

Baixando e Configurando o Postgres

$ docker pull postgres

As credenciais estao no padrão do database.yml, caso queira alterar é necessário fazer também nos arquivos de configuração

$ docker run --name postgres -e POSTGRES_PASSWORD=secret -e POSTGRES_USER=arachni -e POSTGRES_DB=arachni_production -d postgres



Após o banco instalado, baixar o Dockerfile e o database.yml para criar sua imagem do Arachni localmente

$ git clone https://github.com/halencarjunior/docker-arachni.git

Para construir a imagem, digite:

$ docker build -t arachni:latest .

Com a finalização, vamos dar start na nossa imagem 

$ docker run -t --name arachni --link postgres -p 9292:9292 arachni:latest

Agora em outro terminal vamos executar o bash no nosso container para configurar as tabelas do Arachni

$ docker exec -i -t arachni /bin/bash

Depois de conectado, executamos dentro do container o comando:

$ arachni_web_task db:setup

Pronto, agora podemos acessar nossa Web_ui do Arachni pelo endereço:

http://localhost:9292

As credenciais de admin são:

login: admin@admin.admin
senha: administrator
