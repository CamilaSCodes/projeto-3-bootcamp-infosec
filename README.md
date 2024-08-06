
---
# Explorando vulnerabilidades em um servidor de aplicações web
## 3º Projeto Prático do bootcamp em Segurança da Informação do Programa Desenvolve Boticário

Este repositório contém o relatório do teste de penetração realizado na aplicação de treinamento do OWASP: **Juice Shop**, com o objetivo de aplicar na prática os conhecimentos adquiridos na plataforma Alura durante o Bootcamp em Segurança da Informação. No relatório, são identificadas e documentadas vulnerabilidades de segurança, além de serem sugeridas correções apropriadas. Também são apresentadas descrições gerais do projeto, incluindo o escopo dos desafios, limitações e ferramentas utilizadas durante o teste.

[![repo](https://img.shields.io/badge/repo-teal?style=plastic&logo=github&logoColor=008080&labelColor=white)](https://github.com/CamilaSCodes/projeto-1-bootcamp-infosec) &ensp; Projeto 1 &emsp; | &emsp;  [![repo](https://img.shields.io/badge/repo-teal?style=plastic&logo=github&logoColor=008080&labelColor=white)](https://github.com/CamilaSCodes/projeto-2-bootcamp-infosec) &ensp; Projeto 2 &emsp; | &emsp;  [![repo](https://img.shields.io/badge/repo-teal?style=plastic&logo=github&logoColor=008080&labelColor=white)](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec) &ensp; **Projeto 3**

## Briefing do projeto

Neste projeto, será realizado um teste de penetração na aplicação web **Juice Shop** (https://owasp.org/www-project-juice-shop/), com o objetivo de resolver alguns dos desafios propostos, identificar vulnerabilidades e sugerir medidas corretivas.

### Escopo
- Desafios disponíveis na página Score Board

### Limitações
- Desafios indisponíveis no Docker devido a questões de segurança ou incompatibilidade técnica

### Configurações de ambiente

Para executar a aplicação e realizar os testes, utilize a imagem oficial do [site](https://hub.docker.com/r/bkimminich/juice-shop). No caso deste projeto, foi utilizado um container do Docker. Para reproduzir, siga os seguintes passos.

1. Instale o [Docker](https://www.docker.com).

2. Execute:
```
docker pull bkimminich/juice-shop
docker run --rm -p 3000:3000 bkimminich/juice-shop
```

3. Navegue para:
```
http://localhost:3000/#/
```

4. Acesse a página do Score Board, caso queira conhecer os desafios.

### Vulnerabilidades

Cada categoria contém uma vulnerabilidade e seus respectivos desafios, juntamente com instruções para solucioná-los e recomendações de correção. **Acesse-as através dos links abaixo**.
1. [XSS](xss)
2. [Exposição de dados sensíveis](exposição-de-dados-sensíveis)
3. [Validação imprópria de input](validação-imprópria-de-input)
4. [SQL Injection](sql-injection) 
5. [Controle de acesso](controle-de-acesso)
6. [Redirecionamento não validado](redirecionamento-não-validado) 
7. [Componentes vulneráveis](componentes-vulneráveis) 
8. [Autenticação danificada](autenticação-danificada) 
9. [Segurança por obscurantismo](segurança-por-obscurantismo) 
10. [Anti-automação danificada](anti-automação-danificada) 
11. [Configuração incorreta de segurança](configuração-incorreta-de-segurança)
12. [Problemas criptográficos](problemas-criptográficos)

### Tecnologias

![Burp Suite Badge](https://img.shields.io/badge/Burp%20Suite-F63?logo=burpsuite&logoColor=fff&style=for-the-badge) ![Docker Badge](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=fff&style=for-the-badge) ![Kali Linux Badge](https://img.shields.io/badge/Kali%20Linux-557C94?logo=kalilinux&logoColor=fff&style=for-the-badge) ![OWASP Badge](https://img.shields.io/badge/OWASP-000?logo=owasp&logoColor=fff&style=for-the-badge) ![VirtualBox Badge](https://img.shields.io/badge/VirtualBox-183A61?logo=virtualbox&logoColor=fff&style=for-the-badge)

---
