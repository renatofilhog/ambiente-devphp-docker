# Ambiente de Desenvolvimento PHP + MySql em container docker

A base de um ambiente de desenvolvimento usando containers, sendo estes bem enxutos e sem muitas extensões, caso necessário será preciso adicionar.


## Instalação

Para iniciar o ambiente execute o comando:
```bash
  docker compose up -d
```
Certifique-se de estar na pasta raiz e ter o Docker + Docker Compose instalados. 

Siga a documentação para instalção do docker: https://docs.docker.com/get-docker/

#
#### Para adicionar mais extensões, altere o Dockerfile:

```path
  /docker/php/Dockerfile
```
#### Há algumas variáveis de ambientes no docker-compose.yml:
```path
  /docker-compsoe.yml
```
## Imagens usadas

- nginx
- php:8.2-FPM
- PHP XDebuug
- MySql
