# ☁️ Desafio AWS: Configuração de Servidor Web em Instância EC2

Este projeto foi desenvolvido como parte do aprendizado em **Gestão de Tecnologia da Informação**. O objetivo foi implementar uma infraestrutura básica na AWS para hospedar uma página web simples.

## 🚀 Tecnologias Utilizadas
* **AWS EC2:** Instância Amazon Linux (Tipo T3).
* **AWS VPC:** Configuração de rede virtual, sub-redes e internet gateway.
* **Apache (httpd):** Servidor web para hospedar a aplicação.
* **HTML5:** Estrutura da página de projetos.

## 🛠️ O que foi feito:
1. Configuração de uma rede virtual segura (VPC).
2. Lançamento de uma instância EC2 com IP público.
3. Instalação automatizada do servidor Apache via User Data.
4. Configuração de Security Groups para permitir acesso via portas 80 (HTTP) e 22 (SSH).
5. Deploy do arquivo `projects.html` no diretório `/var/www/html`.

## 📂 Documentação
As evidências de funcionamento (prints do log do sistema, acesso SSH e página online) estão anexadas no arquivo `projetos.html.pdf` neste repositório.do boot:
```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
