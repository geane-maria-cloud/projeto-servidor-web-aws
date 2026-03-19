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
Abaixo, o registro da instância Servidor-Web-Desafio (ID: 00016956059512) ativa e configurada no console AWS.

Aplicação Web Online:
Visualização da página projetos.html rodando com sucesso através do IP público da instância.
<img width="468" height="375" alt="imag" src="https://github.com/user-attachments/assets/82bc13e9-5c9c-4b26-9f82-f0918e419a2f" />
Laboratório realizado por Geane Maria como parte da transição de carreira para a área de Tecnologia da Informação.

```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
