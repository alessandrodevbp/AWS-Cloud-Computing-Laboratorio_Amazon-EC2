<p align="center">
  <img width="400" alt="Amazon EC2" src="https://github.com/user-attachments/assets/175cea95-edf4-4456-ae7a-2698228c0c5a" />
</p>


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

### Criação da Instância EC2

<img width="500" alt="Image" src="https://github.com/user-attachments/assets/ec8d2af9-18cd-4df1-87fb-107c4976121f" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/b3e2abd4-4ae2-4606-9d86-008d8bf3edbe" />
<img width="500" height="280" alt="Image" src="https://github.com/user-attachments/assets/2501d752-ff3d-4ae3-92d8-ae8a53a205cd" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/70c9199a-d562-4231-b11e-8304192ff5a5" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/60b74ce5-5261-49b6-812e-0226259cb353" />
<img width="500" height="280" alt="Image" src="https://github.com/user-attachments/assets/4853c30d-2c92-48ae-80ee-da8fa744b7c4" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/8fd58751-2a10-4514-8040-17163100adaa" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/cdc470b0-32cb-47d9-bef9-09ecb999d1e7" />

```text
📷 /images/ec2-instance.png
```

### Monitoramento

<img width="500" height="260" alt="Image" src="https://github.com/user-attachments/assets/add80d0e-40a8-4032-a567-8e0fcd40af6c" />
<img width="500" height="260" alt="Image" src="https://github.com/user-attachments/assets/d276158f-579e-47f7-b0c1-4c92d97eb2d6" />

```text
📷 /images/cloudwatch.png
```

### Security Group

<img width="500" height="260" src="https://github.com/user-attachments/assets/ad743638-21f5-41e7-8f48-a8c415728cf5" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/1ad0dedf-a1c5-460a-b204-93e5ed0d0061" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/b248eb73-8045-49cf-8590-99af7da841e0" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/88084316-fa76-4a68-9593-367eb11389f9" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/5e75a199-5b30-4d5f-b713-d64f3dd0030e" />


```text
📷 /images/security-group.png
```

### Servidor Web

<img width="500" alt="Image" src="https://github.com/user-attachments/assets/4df7df0e-601c-4894-a41e-d709dfa5e0b9" />

```text
📷 /images/web-server.png
```

### Redimensionamento (Alteração do tipo de instância e do volume EBS)

<img width="500" alt="Image" src="https://github.com/user-attachments/assets/e9cc1fe5-9b15-4f67-8e4d-397d8bf916ee" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/05877202-9ea6-4f22-88db-ccc2c658c9f3" />
<img width="500" height="260" src="https://github.com/user-attachments/assets/75458769-1b11-45af-81a5-5402dc42a60d" />
<img width="500" height="260" alt="Image" src="https://github.com/user-attachments/assets/7498f7e7-0c07-4791-b5ab-b044ad7a382f" />
<img width="500" height="260" alt="Image" src="https://github.com/user-attachments/assets/376b2ec8-d6c3-49dd-ac8c-63d47549ebd0" />
<img width="500" height="260" alt="Image" src="https://github.com/user-attachments/assets/1cd174d4-ede3-424a-ad06-9659fbc717df" />
<img width="500" height="260" alt="Image" src="https://github.com/user-attachments/assets/dc7c43a4-09bb-4672-b792-44eceb966f9a" />
<img width="500" height="260" alt="Image" src="https://github.com/user-attachments/assets/d7347a58-79b3-48d8-8e13-7c9701fc6587" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/b2f9a1d7-6eb1-4e89-9d9c-b7bf9432cd32" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/197d12a6-b88b-4fbf-b5ff-93eb3eda57fb" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/3cbd7a40-23c7-49a1-8e07-a627e89ff46e" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/f846f440-3d94-4263-b27f-fac6874f8ea0" />
<img width="500" alt="Image" src="https://github.com/user-attachments/assets/99df7f88-f195-44c2-a817-555020cb5852" />

```
⚠️ Observação
Ao realizar a criação da instância "Web Server", a "Proteção Contra Encerramento" ficou desabilitada, não sendo possível
prosseguir com o que era proposto neste laboratório: apresentar a falha ao tentar excluir a instância.
Dessa forma, realizei a criação de uma nova instância, "Web Server 2", com a "Proteção Contra Encerramento" habilitada.
Assim, foi possível apresentar a falha ao tentar excluir essa instância, conforme proposto no laboratório.
Por esse motivo, houve uma alteração nos prints finais.
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
