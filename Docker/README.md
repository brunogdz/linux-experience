# Microserviços

São um tipo de arquitetura de software, que consiste em construir aplicações desmembrando-as em serviços independentes. Estes serviços se comunicam entre si usando APIs e promovem grande agilidade em times de desenvolvimento. 

Podemos escalar apenas uma parte, ao invés de ter que escalar a aplicação como um todo, como ocorre em uma arquitetura monolítica.

## Cluster x Docker Swarm

Um cluster consiste em computadores ligados que trabalham em conjunto, de modo que pode ser considerados como um único sistema. 

O swarm é um recurso do Docker que fornece funcionalidades de orquestração de containers, incluindo clustering nativo de hosts do Docker. Um grupo de hosts do Docker formam um cluster "Swarm"

## Criando um container MYSQL

```shell
docker run --name web-server -dt -p 80:80 --mount type=volue, src=app, dst=/app/
```

## Iniciando cluster Swarm

```shell
docker swarm init
```

```shell
docker swarm join --token <token-here>
```

## Serviço cluster

```shell
docker service create --name web-server --replicas 3 -dt -p 80:80 --mount type=volume,src=app, dst=/app/ 
```

## Criando um proxy com NGINX

primeiro você precisa de um nginx.conf

um exemplo:

```shell
 http {
   
    upstream all {
        server 172.31.0.37:80;
        server 172.31.0.151:80;
        server 172.31.0.149:80;
    }

    server {
         listen 4500;
         location / {
              proxy_pass http://all/;
         }
    }

}


events { }
```

Colocando o dockerfile e ao executar o build, e o nginx.conf estando na mesma raiz, será instalado na hora de fazer o build.

```shell
docker build -t proxy-app
```

