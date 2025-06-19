# Projeto: Página HTML com NGINX na AWS EC2 🚀

Este projeto mostra como hospedar uma página HTML simples em uma instância EC2 usando o servidor NGINX.

---

## ✅ O que foi feito

- Criada instância EC2 (Amazon Linux)
- Configurado NGINX
- Copiado `index.html` para o servidor via SCP
- Servido o site acessível via IP público

---

## 🔧 Comandos utilizados
### 1) Script de inicialização (Metatado) (User Data) da EC2 para instalar o NGINX automaticamente::

#!/bin/bash  <br>
sudo update -y <br>
sudo yum install nginx -y  <br>
sudo systemctl enable nginx  <br>
sudo systemctl start nginx  <br>

### 1.2) (opcional) Permissão na chave antes de conectar via SSH:

chmod 400 <SUA_CHAVE.pem>

### 2) Copindo o index.html para pasta tmp da minha maquina EC2:

scp -i "<SUA_CHAVE.pem>" index.html  ec2-user@<SEU_IP_PUBLICO>:/tmp

### 3) Conectando via SSH:

ssh -i "<SUA_CHAVE.pem>" ec2-user@<SEU_IP_PUBLICO>

### 4) Movendo o index.html para o index.html do nginx:

sudo mv index.html /usr/share/nginx/html/index.html

