# Desafio AWS: Configuração de Servidor Web em Instância EC2 ☁️

Este projeto demonstra a configuração de uma infraestrutura básica na AWS, incluindo redes virtuais e computação em nuvem, para hospedar uma aplicação web simples.

## 🚀 Objetivos do Desafio
- Configurar uma rede virtual (VPC) com sub-rede e gateway de internet.
- Lançar uma instância EC2 (Amazon Linux 2023).
- Instalar e configurar um servidor web Apache (`httpd`) via script de automação (User Data).
- Realizar o deploy de uma página HTML customizada.

## 🛠️ Tecnologias Utilizadas
- **Provedor de Nuvem:** AWS (Amazon Web Services)
- **Serviços:** EC2, VPC, Security Groups, Internet Gateway.
- **Sistema Operacional:** Amazon Linux 2023.
- **Servidor Web:** Apache HTTP Server.
- **Linguagens:** Bash (automação) e HTML5.

## 📋 Passo a Passo Realizado

### 1. Infraestrutura de Rede
Criação de uma **VPC** dedicada com bloco CIDR `10.0.0.0/16`. Configurei um **Internet Gateway** e atualizei as tabelas de rotas para permitir o tráfego público (rota `0.0.0.0/0`).

### 2. Segurança
Configuração de um **Security Group** liberando as seguintes portas:
- **Porta 80 (HTTP):** Para acesso público à página web.
- **Porta 22 (SSH):** Para administração remota via terminal.

### 3. Provisionamento da Instância
Lançamento de uma instância `t3.micro`. Utilizei o campo **User Data** para automatizar a instalação do servidor no momento do boot:
```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
