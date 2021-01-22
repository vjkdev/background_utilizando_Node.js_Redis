  # Tarefas em Background utilizando Node.js e Redis

Este projeto faz parte do Bootcamp Node.js Web Developer do site Digital Innovation One.
Objetivo do projeto é desenvolver um cadastro de usuário e envio de e-mail de confirmação do cadastro como tarefa em background utilizando Node.js e Redis.

## Pré requisitos

-   [Node.js](https://nodejs.org/en/)
-   [NPM](https://www.npmjs.com/) or [Yarn](https://yarnpkg.com/pt-BR/docs/install)
-   [Redis](https://redis.io/)

## Tecnologias, Dependencias e Bibliotecas

* Node.js
* Framework Express.js
* Docker
* Redis via Docker
* Dependências: nodemailer, dotenv, nodemon, sucrase
* Bibliotecas: Bull , Bull-Board, Password-generator
* Site mailtrap.io
* Insomnia

## Instalação

* Instalar o Docker for Windows
* Verificar se o Docker foi instalado: digite no terminal o comando: **docker -v**
* Baixar no Docker a imagem do Redis: 
* Ir até Docker Hub e selecionar a imagem do Redis  
[Docker Hub]: https://hub.docker.com/_/redis
* Inserir no Terminal o comando: docker pull redis 
* Verificar as imagens instaladas no Docker: digite no terminal o comando: **docker images**

Para iniciar a imagem do Redis no Docker digite o seguinte comando no terminal: **docker run -d -p 6379:6379 -i -t redis: (digite a versão da imagem que baixou).**

Exemplo: docker run --name redis -p 6379:6379 -d -t redis:alpine**

Para verificar os containers em execução digite o comando: **docker ps**

Para encerrar a execução do container digite o comando: **docker stop [container Id],** 

o id do Container pode ser visto com o comando docker ps

## Para inicializar um projeto

1. Clone o repositório `git clone git@github.com:https://github.com/vjkdev/background_utilizando_Node.js_Redis.git`
2. Entre no diretório e instale as dependências: 
   * utilize os comandos yarn ou npm
     yarn install -y (linux)`yarn install`
     npm install -y (windows)`npm install`.

3. Instale o [Docker](https://www.docker.com/get-started) para rodar o Redis, e depois execute o comando `$ docker run --name lab01redis -p 6379:6379 --detach redis`. 

Ir ao site [**https://mailtrap.io/**](https://mailtrap.io/) criar uma conta gratuita ou acessar caso já tenha.

Em inboxes na aba SMTP/POP3 em integrations selecionar Nodemailer e copiar o código.

Configure o arquivo **.env** com os dados copiados no site do mailtrap.io

```
PORT=8080

MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USER="digite/ou cole aqui o seu código de user copiado do mailtrap "
MAIL_PASS="digite/ou cole aqui o seu password copiado do mailtrap "
```

Abra dois terminais no VSCode:
* No primeiro terminal digite: **`npm start`** para rodar a aplicação no localhost: `http://localhost:8080/`. 
* No segundo terminal digite: **`npm run queue`** para iniciar o serviço de fila em background.
* Abra um navegador de internet e digite o endereço: http://localhost:8080/admin/queues 
* Abra o Postman ou Insomnia e execute um comando Post com o seguinte JSON: 

```
{
	"name": "Junior Souza",
	"email": "juniorsz@email.com"
}
```

Assim que o comando POST é executado é possível visualizar no site http://localhost:8080/admin/queues a execução no dashboard RegistrationMail do arquivo enviado.

Ele passa pelas etapas de delayed, active e quando aparecer em completed abra o site [**https://mailtrap.io/**](https://mailtrap.io/) e vá na caixa inboxes, lá você irá receber um novo e-mail .



## Licença

This project is under the MIT license. See the [LICENSE](https://github.com/vjkdev/background_utilizando_Node.js_Redis/main/license) for more information.