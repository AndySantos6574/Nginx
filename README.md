# Nginx
Instalação do Nginx

Como Instalar o Nginx no Ubuntu:

Introdução

O Nginx é um dos servidores Web mais populares no mundo e é responsável por hospedar alguns dos sites de maior tráfego na Internet. Ele é uma escolha leve que pode ser usado como servidor web ou proxy reverso.

Neste guia, vamos discutir como instalar o Nginx em seu servidor Ubuntu e ajustar o firewall,


Passo 1 - Instalando o Nginx:



sudo apt update
sudo apt install nginx

Passo 2 — Vamos ajustar o Firewall

Liste as configurações do aplicativo com as quais o ufw sabe trabalhar digitando:

sudo ufw app list

Você deve obter uma lista dos perfis dos aplicativos:

Available applications:
  Nginx Full
  Nginx HTTP
  Nginx HTTPS
  OpenSSH
  
Como indicado pela saída, há três perfis disponíveis para o Nginx:

Nginx Full: Este perfil abre ambas as portas 80 (tráfego Web normal, não criptografado) e 443 (tráfego TLS/SSL criptografado)
Nginx HTTP: Este perfil abre apenas a porta 80 (tráfego Web normal, não criptografado)
Nginx HTTPS: Este perfil abre apenas a porta 443 (tráfego TLS/SSL criptografado)

É recomendável que você habilite o perfil mais restritivo que ainda assim permitirá o tráfego que você configurou. Agora, precisaremos apenas permitir o tráfego na porta 80.

Permita isso digitando:

sudo ufw allow 'Nginx HTTP'

Você pode verificar a mudança digitando:

sudo ufw status

A saída indicará qual tráfego HTTP é permitido:

Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Nginx HTTP                 ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
Nginx HTTP (v6)            ALLOW       Anywhere (v6)


Passo 3 — Verificando o Servidor Web:

Agora vamos verificar se está tudo funcionando certinho o Nginx com os seguintes comando:

systemctl status nginx

● nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2020-04-20 16:08:19 UTC; 3 days ago
     Docs: man:nginx(8)
 Main PID: 2369 (nginx)
    Tasks: 2 (limit: 1153)
   Memory: 3.5M
   CGroup: /system.slice/nginx.service
           ├─2369 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           └─2380 nginx: worker process
           
 
Como confirmado por esta saída, o serviço foi iniciado com sucesso. No entanto, a melhor maneira de realmente testar isso é solicitando uma página do Nginx


Seu nginx está active, agora é só acessar http://localhost e verá uma tela escrito > Welcome to nginx!

O seu servidor web nginx foi instalado com sucesso e está operado!



















