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
<img width="864" height="373" alt="aws" src="https://github.com/user-attachments/assets/ee157626-8cf3-4c9a-8d4a-8de21da20a92" />
<img width="854" height="342" alt="site" src="https://github.com/user-attachments/assets/d5ef501e-5590-4018-8848-45d2262d1ce4" />

---

## 🛠️ Especificações Técnicas da Instância

Para este laboratório, a infraestrutura foi provisionada com as seguintes características:

* **Nome da Instância:** Servidor-Web-Desafio
* **ID do Recurso:** 00016956059512
* **Sistema Operacional:** Amazon Linux 2023
* **Tipo de Instância:** Família T3 (t3.micro)
* **Armazenamento:** Volume raiz SSD de uso geral (gp2)
* **Servidor Web:** Apache (httpd) instalado via script de automação (User Data)

---

## 🏗️ Arquitetura do Projeto

Abaixo, a representação visual de como os componentes estão conectados dentro da nuvem AWS:

```text
+-------------------------------------------------------------+
| AWS Cloud (Region)                                          |
|  +-------------------------------------------------------+  |
|  | VPC (Virtual Private Cloud)                           |  |
|  |  +-------------------------------------------------+  |  |
|  |  | Public Subnet                                   |  |  |
|  |  |  +-------------------+      +-----------------+  |  |  |
|  |  |  |  Security Group   | <--- | Internet        |  |  |  |
|  |  |  |  (Port 80 & 22)   |      | Gateway         |  |  |  |
|  |  |  +---------+---------+      +-----------------+  |  |  |
|  |  |            |                                   |  |  |
|  |  |  +---------v---------+                         |  |  |
|  |  |  | EC2 Instance      |                         |  |  |
|  |  |  | (Apache Server)   |                         |  |  |
|  |  |  +-------------------+                         |  |  |
|  |  +-------------------------------------------------+  |  |
|  +-------------------------------------------------------+  |
+-------------------------------------------------------------+

Laboratório realizado por Geane Maria como parte da transição de carreira para a área de Tecnologia da Informação.

```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
