<img width="500" height="280" alt="Image" src="https://github.com/user-attachments/assets/175cea95-edf4-4456-ae7a-2698228c0c5a" />

<header>
  <h1 align="center"> ☁️Laboratório AWS — Introdução ao Amazon EC2</h1>
</header>

<h1 align="center">📌 Sobre o laboratório</h1>

Este projeto registra meu aprendizado prático sobre **Amazon EC2 (Elastic Compute Cloud)** por meio de um laboratório da **AWS Training and Certification**.

O objetivo foi compreender, na prática, como **executar, configurar, monitorar, redimensionar, proteger e encerrar uma instância EC2** na nuvem.

---

## 🎯 Objetivos

Durante o laboratório, foram trabalhados os seguintes conceitos e atividades:

* 🚀 Inicialização de uma instância Amazon EC2
* 🖥️ Configuração de um servidor web
* 🔐 Configuração de proteção contra encerramento
* 📊 Monitoramento da instância
* 🌐 Configuração de acesso HTTP
* 🛡️ Utilização de Security Groups
* 📦 Utilização de volumes Amazon EBS
* ⚙️ Execução de comandos através de User Data
* 🔄 Redimensionamento da instância
* 💾 Redimensionamento do volume de armazenamento
* 🗑️ Encerramento controlado da instância

Essas atividades permitiram acompanhar diferentes etapas do ciclo de vida de uma instância EC2.

---

## ☁️ Amazon EC2

O **Amazon Elastic Compute Cloud (EC2)** é um serviço que fornece capacidade computacional redimensionável na nuvem.

Durante o laboratório, foi utilizada uma instância EC2 para executar um servidor web e explorar recursos de computação, rede, armazenamento, segurança e monitoramento.

---

## 🛠️ Configuração utilizada

| Recurso                | Configuração           |
| ---------------------- | ---------------------- |
| ☁️ Serviço             | Amazon EC2             |
| 🐧 Sistema operacional | Amazon Linux 2023      |
| 💻 Tipo inicial        | t3.micro               |
| 🧠 CPU virtual         | 2 vCPUs                |
| 🧮 Memória inicial     | 1 GiB                  |
| 💾 Volume inicial      | 8 GiB                  |
| 🌐 Servidor web        | Apache                 |
| 🔐 Segurança           | Security Group         |
| 🌍 Protocolo liberado  | HTTP — porta 80        |
| 🛡️ Proteção           | Termination Protection |

## A instância `t3.micro` foi utilizada inicialmente e posteriormente redimensionada para `t3.small`, enquanto o volume EBS passou de **8 GiB para 10 GiB**.

## 🚀 Criação da instância EC2

A primeira etapa consistiu em criar uma instância EC2 utilizando a **Amazon Linux 2023** como AMI e o tipo de instância `t3.micro`.

## Também foi configurada uma **VPC**, um **Security Group** específico para o servidor web e a proteção contra encerramento.

## ⚙️ Automação com User Data

Um dos pontos importantes do laboratório foi a utilização do **User Data** para automatizar a configuração inicial da instância.

O script utilizado:

```bash
#!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
```

Com esse script foi possível:

* Instalar o servidor web Apache;
* Configurar o Apache para iniciar automaticamente;
* Iniciar o serviço;
* Criar uma página HTML simples.

---

## 🔐 Security Group e acesso HTTP

Inicialmente, o servidor web não podia ser acessado pelo navegador porque o **Security Group não possuía uma regra permitindo tráfego HTTP na porta 80**.

Foi adicionada uma regra de entrada:

```text
Tipo: HTTP
Porta: 80
Origem: IPv4 em qualquer lugar
```

Após essa alteração, foi possível acessar o servidor através do endereço IPv4 público e visualizar:

```text
Hello From Your Web Server!
```

Essa etapa demonstrou, na prática, como o **Security Group atua como um firewall virtual**, controlando o tráfego permitido para a instância.

---

## 📊 Monitoramento

Também foram explorados os recursos de monitoramento do EC2.

Foram verificadas:

* **Status Checks**
* **System Reachability**
* **Instance Reachability**
* Métricas disponibilizadas pelo **Amazon CloudWatch**
* Captura de tela da instância para auxiliar na solução de problemas

O laboratório também apresentou a diferença entre o monitoramento básico, realizado em intervalos de cinco minutos, e o monitoramento detalhado, que pode utilizar intervalos de um minuto.

---

## 🔄 Redimensionamento da infraestrutura

O laboratório também demonstrou como adaptar os recursos de uma instância conforme as necessidades do workload.

Antes de realizar o redimensionamento, a instância foi interrompida.

### Alteração realizada

```text
t3.micro → t3.small
```

Além disso, o volume do Amazon EBS foi aumentado:

```text
8 GiB → 10 GiB
```

Após as alterações, a instância foi iniciada novamente com os novos recursos.

---

## 🛡️ Termination Protection

Outro conceito importante praticado foi a **proteção contra encerramento**.

Ao tentar encerrar a instância com essa proteção habilitada, a operação não foi concluída.

Foi necessário desabilitar a **Termination Protection** antes de realizar o encerramento definitivo da instância.

Essa etapa ajudou a compreender a importância de mecanismos de proteção contra exclusões acidentais de recursos.

---

## 📚 Principais aprendizados

Este laboratório permitiu consolidar conhecimentos sobre:

* ☁️ Computação em nuvem com Amazon EC2
* 🖥️ Instâncias e tipos de recursos computacionais
* 🐧 Amazon Linux
* 🛡️ Security Groups
* 🌐 Regras de tráfego HTTP
* 📦 Amazon EBS
* ⚙️ User Data e automação
* 📊 Monitoramento com CloudWatch
* 🔄 Redimensionamento de recursos
* 🛡️ Proteção contra encerramento
* 🔚 Ciclo de vida de uma instância EC2

---

## 🧠 O que ficou de aprendizado

> Este laboratório mostrou, de forma prática, que trabalhar com infraestrutura em nuvem não envolve apenas criar uma máquina virtual. É necessário compreender também **segurança, rede, armazenamento, monitoramento, automação, escalabilidade e gerenciamento do ciclo de vida dos recursos**.

A experiência ajudou a conectar conceitos teóricos de computação em nuvem com uma implementação prática dentro do ambiente AWS.

---

## 📸 Evidências do laboratório

### Instância EC2

> Adicione aqui um print da instância EC2 em execução.

```text
📷 /images/ec2-instance.png
```

### Security Group

> Adicione aqui um print da regra HTTP configurada.

```text
📷 /images/security-group.png
```

### Servidor Web

> Adicione aqui um print da página `Hello From Your Web Server!`.

```text
📷 /images/web-server.png
```

### Monitoramento

> Adicione aqui um print das métricas da instância.

```text
📷 /images/cloudwatch.png
```

### Redimensionamento

> Adicione aqui um print mostrando a alteração da instância e do volume EBS.

```text
📷 /images/resize-ec2.png
```

---

## 🧰 Tecnologias e serviços

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge\&logo=amazonaws)

![EC2](https://img.shields.io/badge/Amazon-EC2-orange?style=for-the-badge\&logo=amazonec2)

![Linux](https://img.shields.io/badge/Amazon-Linux-orange?style=for-the-badge\&logo=linux)

![Apache](https://img.shields.io/badge/Apache-Web_Server-red?style=for-the-badge\&logo=apache)

**Serviços e conceitos estudados:**

`Amazon EC2` • `Amazon EBS` • `Amazon CloudWatch` • `Security Groups` • `VPC` • `AMI` • `User Data` • `Apache` • `Amazon Linux 2023`

---

## 📖 Referência

**AWS Training and Certification — Introduction to Amazon EC2**

Laboratório prático utilizado para desenvolver conhecimentos fundamentais sobre criação, configuração, monitoramento, segurança, redimensionamento e encerramento de instâncias Amazon EC2.

---

## 🚀 Próximos passos

Este laboratório faz parte da minha jornada de aprendizado em **AWS Cloud**.

**Próximos objetivos:**

* 📚 Continuar explorando os principais serviços AWS
* ☁️ Aprofundar conhecimentos em Cloud Computing
* 🔐 Evoluir os conhecimentos de segurança na AWS
* 🏗️ Praticar arquitetura e infraestrutura em nuvem
* ⚙️ Explorar automação e gerenciamento de recursos

---

<p align="center">
  ☁️ <strong>Aprendizado contínuo em Cloud Computing</strong> ☁️
</p>

<p align="center">
  <sub>Laboratório realizado para fins educacionais.</sub>
</p>




<p align="center">
  <sub>© 2026 Alessandro Batista Prudente — Todos os direitos reservados.</sub>
</p>
