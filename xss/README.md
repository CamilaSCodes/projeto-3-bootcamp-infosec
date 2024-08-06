---

<div align="center">

## XSS

</div>

XSS (Cross-Site Scripting) é um tipo de vulnerabilidade de segurança encontrada em aplicações web, onde um atacante consegue injetar scripts maliciosos no conteúdo enviado por um site confiável e fazê-los ser executados no navegador de outros usuários.

### 1. DOM XSS (DOM XSS ⭐)

Um ataque XSS tipo DOM (Document Object Model) é uma forma de Cross-Site Scripting onde o script malicioso é injetado e executado diretamente no lado do cliente, manipulando o DOM da página web. 

Para realizar o ataque, vá até o campo de busca e insira o comando: 
```
<iframe src="javascript:alert(`xss`)">
```
Aperte `Enter`. A pop-up a seguir irá surgir na tela.

![DOM XSS](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/DOM%20XSS.png?raw=true)

### 2. Carga Bônus (Bonus Payload ⭐)

Em seguida, copie o payload e insira no campo de busca: 
```
<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>
```
Aperte `Enter`. Uma música deverá começar a tocar. 

![Bonus Payload](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Bonus%20Payload.png?raw=true)

---

<div align="center">

### Recomendações

</div>

**1. Validação de Entrada:** Sempre validar e sanitizar os dados de entrada fornecidos pelos usuários. Nunca confiar em dados que vêm do cliente.

**2. Política de Segurança de Conteúdo (CSP):** Implementar uma CSP que restrinja as fontes de conteúdo permitidas na aplicação web, mitigando a execução de scripts não autorizados.

**3. Evitar HTML Não Seguro:** Evitar o uso de funções ou métodos que geram HTML dinamicamente a partir de entradas do usuário, como innerHTML em JavaScript.

---
