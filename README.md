# ☁️ Desafio AWS: Configuração de Servidor Web em Instância EC2

Este projeto demonstra a configuração de uma infraestrutura básica na AWS, incluindo redes e computação em nuvem, para hospedar uma aplicação web simples.

## 🎯 Objetivos do Desafio
* Configurar uma rede virtual (VPC) com sub-rede e Gateway de Internet.
* Lançar uma instância EC2 (Amazon Linux 2023).
* Instalar e configurar um servidor web Apache (httpd) via script de automação (User Data).
* Realizar o deploy de uma página HTML personalizada.

## 🛠️ Tecnologias Utilizadas
* **Provedor de Nuvem:** AWS (Amazon Web Services).
* **Serviços:** EC2, VPC, Grupos de Segurança, Gateway de Internet.
* **Sistema Operacional:** Amazon Linux 2023.
* **Servidor Web:** Web Server HTTP Apache.
* **Linguagens:** Bash (automação) e HTML5.

## 📑 Passo a Passo Realizado

### 1. Infraestrutura de Rede
Criação de uma VPC dedicada e configuração de um Internet Gateway com tabelas de rotas para permitir o tráfego público.

### 2. Segurança
Configuração de um **Security Group** liberando as seguintes portas:
* **Porta 80 (HTTP):** Para acesso público à página web.
* **Porta 22 (SSH):** Para administração remota via terminal.

### 3. Provisionamento da Instância
Lançamento de uma instância **t3.micro**. Utilize o campo **User Data** para automatizar a instalação do servidor no momento da inicialização:

📸 Evidências do Laboratório
Configuração da Instância EC2:
Abaixo, o registro da instância Servidor-Web-Desafio ativa e configurada no console AWS.
<img width="868" height="381" alt="aws" src="https://github.com/user-attachments/assets/db5f2ee7-a865-4b9f-ba45-46e47aabcd7c" />
Aplicação Web Online:
Visualização da página projetos.html rodando com sucesso através do IP público da instância.
<img width="1077" height="677" alt="site" src="https://github.com/user-attachments/assets/cdc53f8f-97dc-4932-bec9-2ea52fc43df9" />

```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
