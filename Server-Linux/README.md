# Servidores com Linux

# Samba

### Servidor de Arquivos

systemctl smbd service

Quando iniciar o serviço samba, poderá ver o ip utilizando o comando

```shell
ip a
```

# Servidor Web

### 2 servidores importantes

DNS -> Retorna o ip do site

Apache -> Recebe um http e retora um site

```shell
apt install apache2 -y
```

### Na AWS

- Criar um EC2
- Criar um máquina Ubuntu 20.04
- Criar uma chave .ppk 
- Disponibilizar o firewall e SSH traffic form Anywhere (0.0.0.0/0)

### Para o acesso usando o browser

- Vá em segurança e adiciona uma nova regra
- Selecione o HTTP, não seleciona o HTTPS
- E coloque para ser anywhere (0.0.0.0/0)

# Banco de dados

```shell
apt install mysql-server-8.0 -y
```

Logar no banco de dados

```shell
mysql -u root -p
```

Pode utilizar os comandos mySQL para a criação das tabelas e etc.



