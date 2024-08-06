---

<div align="center">

## Anti-automação Danificada

</div>

A vulnerabilidade anti-automação danificada, também conhecida como "broken anti automation", ocorre quando as medidas implementadas para prevenir a automação de tarefas são ineficazes ou mal configuradas, permitindo que scripts automatizados ou bots contornem essas proteções.

### 1. Desvio de CAPTCHA (CAPTCHA Bypass ⭐⭐⭐)

No Kali Linux, abra o **Burp Suite** e vá para a aba **Proxy**. Em seguida, abra o Browser e acesse a seção de **Comentários dos Clientes** no Juice Shop.

```
http://localhost:3000/#/contact
```

Escreva um comentário qualquer, atribua uma classificação e preencha o CAPTCHA.

No **Burp**, clique em `Intercept is off`. Volte ao Browser e clique em `Enviar`.

De volta ao **Burp**, pressione o botão direito sobre o texto e selecione `Send to Repeater`. Clique em `Intercept is on`.

Na aba **Repeater**, clique em `Send` algumas vezes e note que você pode reutilizar o CAPTCHA anterior em novas requisições sem problemas.

Sabendo disso, pressione o botão direito no texto que está em **Request** e clique em `Send to Intruder`.

Na aba **Intruder**, clique em `Clear`. Em seguida, vá até a aba **Payloads**.

No campo **Payload type**, altere o valor para **Null payloads**, pois não serão feitas mudanças no CAPTCHA. Em **Payload Settings**, altere o campo vazio após **Generate** para qualquer valor **maior ou igual a 10**. 

Clique em `Start attack` e os feedbacks serão enviados automaticamente.

![CAPTCHA Bypass](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/CAPTCHA%20Bypass.png)

### 2. Linguagem Extra (Extra Language ⭐⭐⭐⭐⭐)

Na aba **Proxy** do **Burp Suite**, clique em `Intercept is off`. Abra o Browser, altere a linguagem do site para outra qualquer, por exemplo, inglês.

No **Burp Suite**, observe que a primeira linha do texto interceptado será como abaixo.

```
GET /assets/il8n/en.json HTTP/1.1
```

Clique em `Intercept is on`, atualize a página no Browser e clique novamente em `Intercept is off`. Troque a linguagem do site novamente, agora para espanhol, por exemplo.

No **Burp Suite**, a requisição terá a primeira linha como esta.

```
GET /assets/il8n/es_ES.json HTTP/1.1
```

Note que a única diferença é o nome do arquivo .json, que muda de acordo com a abreviação da linguagem.

Agora, precisamos encontrar uma linguagem não convencional suportada pelo Juice Shop, o que pode ser feito acessando o link abaixo. 

```
https://crowdin.com/project/owasp-juice-shop
```
Navegando pelas linguagens, você encontrará **Klingon**, que, diferente das outras, é usada não por um país real, mas em Star Trek. Clique nela e observe que a abreviação usada na URL é “tlh-AA”.

De volta ao Burp Suite, clique com o botão direito no texto da requisição e selecione `Send to Repeater`.

Na aba **Repeater**, altere a primeira linha do texto para utilizar a abreviação da linguagem Klingon encontrada, mantendo o mesmo formato das outras.

```
GET /assets/il8n/tlh_AA.json HTTP/1.1
```
Pressione `Send` e você terá encontrado o arquivo da linguagem secreta do site.

![Klingon](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Klingon.png)

<div align="center">

---

### Recomendações

</div>

**1. Limitação de Taxa (Rate Limiting):** Implemente limitações de taxa para restringir o número de solicitações que um usuário pode fazer em um determinado período de tempo. 

**2. Análise de Padrões de Comportamento:** Monitore e analise o comportamento dos usuários para identificar padrões típicos de bots. Por exemplo, cliques repetitivos e rápidos, ou navegação sem uso do mouse.

---
