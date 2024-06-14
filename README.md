# Explorando vulnerabilidades em um servidor de aplicações web
## 3º Projeto Prático do bootcamp em Segurança da Informação do Programa Desenvolve Boticário

![logo da boticário](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens_projeto3/boticario_logo.JPG?raw=true)

Este repositório contém o relatório do teste de penetração realizado no site da marca O Boticário, com o objetivo de aplicar na prática os conhecimentos adquiridos na plataforma Alura durante o Bootcamp em Segurança da Informação. No relatório, são identificadas e documentadas vulnerabilidades de segurança, além de serem sugeridas correções apropriadas. Também são apresentadas descrições gerais do projeto, incluindo o escopo, limitações, técnicas e ferramentas utilizadas durante o teste.

[![repo](https://img.shields.io/badge/repo-teal?style=plastic&logo=github&logoColor=008080&labelColor=white)](https://github.com/CamilaSCodes/projeto-1-bootcamp-infosec) &ensp; Projeto 1 &emsp; | &emsp;  [![repo](https://img.shields.io/badge/repo-teal?style=plastic&logo=github&logoColor=008080&labelColor=white)](https://github.com/CamilaSCodes/projeto-2-bootcamp-infosec) &ensp; Projeto 2 &emsp; | &emsp;  [![repo](https://img.shields.io/badge/repo-teal?style=plastic&logo=github&logoColor=008080&labelColor=white)](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec) &ensp; **Projeto 3**

## Briefing do projeto

Nesse projeto, a Boticário solicitou à equipe de Red Team a execução de um teste de penetração em seu site (https://www.boticario.com.br/), com o objetivo de melhorar a segurança da aplicação web, proteger os dados dos usuários e da empresa, e receber recomendações de correção para as vulnerabilidades identificadas.

### Escopo
- Página principal
- Formulários de login
- Áreas de usuário autenticado
- Páginas de compra

### Limitações
- Não realizar ataques de negação de serviço (DoS)
- Não modificar ou excluir dados

### Técnicas aplicadas
- Testes de controle de acesso
- Testes de injeção SQL
- Testes de Local File Inclusion (LFI)
- Testes de cross-site scripting (XSS)
- Ataques de força bruta
- Verificação de validação de segurança
- Varredura de vulnerabilidades
  
### Tecnologias 
- **VirtualBox:** Para gerenciar a máquina virtual do Kali Linux.
- **Kali Linux:** Para simular a máquina de um atacante.
- **Burp Suite:** Para interceptar e modificar o tráfego HTTP.
- **Sqlmap:** Para explorar vulnerabilidades de injeção SQL.
- **Hydra:** Para realizar ataques de força bruta testando listas de usuários e senhas.
- **WMAP:** Para escanear o servidor web e identificar vulnerabilidades.

![VirtualBox Badge](https://img.shields.io/badge/VirtualBox-183A61?logo=virtualbox&logoColor=fff&style=for-the-badge) ![Kali Linux Badge](https://img.shields.io/badge/Kali%20Linux-557C94?logo=kalilinux&logoColor=fff&style=for-the-badge) ![Burp Suite Badge](https://img.shields.io/badge/Burp%20Suite-F63?logo=burpsuite&logoColor=fff&style=for-the-badge) ![Metasploit Badge](https://img.shields.io/badge/Metasploit-2596CD?logo=metasploit&logoColor=fff&style=for-the-badge)

## Vulnerabilidades

### Arquivo “security.txt” faltando

**Descrição do risco:** O arquivo "security.txt" é crucial porque oferece um canal designado para relatar vulnerabilidades e problemas de segurança. No entanto, a ausência deste arquivo não representa um risco específico imediato. 

**Recomendação:** Recomenda-se a implementação do arquivo "security.txt" de acordo com o [padrão](https://securitytxt.org/), para permitir que pesquisadores ou usuários relatem quaisquer problemas de segurança que encontrarem. Isso melhora os mecanismos de defesa do servidor, facilitando a comunicação e a resposta a potenciais ameaças.

### Falta de bloqueio a múltiplas tentativas de login

**Descrição do risco:** Se um site não bloqueia o acesso após várias tentativas de senha incorretas, ele fica vulnerável a ataques de força bruta. Nesse tipo de ataque, um invasor pode tentar inúmeras combinações até encontrar a correta, resultando no comprometimento de contas, exposição de dados pessoais e danos à reputação.

**Recomendação:** Recomenda-se a implementação de bloqueio temporário da conta após um número específico de tentativas falhas. Outras medidas incluem o uso de CAPTCHA, notificação ao usuário sobre tentativas de login falhas, aumento progressivo do tempo de bloqueio, monitoramento e análise de logs de tentativas de login, e a implementação de autenticação multifator (MFA).

## Conclusão

O projeto final do Bootcamp em Segurança da Informação do Programa Desenvolve Boticário permitiu a aplicação prática dos conhecimentos adquiridos ao longo de um semestre sobre segurança cibernética. Durante a análise, foram identificadas apenas vulnerabilidades pouco significativas no site do Boticário, como a ausência do arquivo "security.txt" e a falta de bloqueio contra múltiplas tentativas de login, evidenciando o comprometimento da marca com a privacidade dos usuários. Embora as recomendações tenham sido mínimas, elas ressaltam a importância de realizar testes regulares de segurança para proteger dados sensíveis e preservar a integridade e a reputação da aplicação web de forma integral.


