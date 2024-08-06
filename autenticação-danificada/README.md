---

<div align="center">

## Autenticação Danificada

</div>

A vulnerabilidade de autenticação danificada ocorre quando um sistema de autenticação não protege adequadamente as credenciais de usuário, o que pode permitir que atacantes contornem ou comprometam os mecanismos de autenticação.

### 1. Força da Senha (Password Strength ⭐⭐)

Para tentar adivinhar a senha da conta de administração, utilizaremos o **Burp Suite** e a técnica de **Brute Force**. 

Primeiro, abra o Kali Linux e, em seguida, inicie o **Burp Suite**. No **Burp**, clique em `Target` e depois em `Scope`.

Para garantir que apenas o necessário seja interceptado, siga estas etapas: abaixo de **Include in scope**, clique em `Add`. No campo **Prefix**, adicione a URL `http://localhost:3000/`. 

Clique em `OK`. Na janela pop-up que aparecer, clique em `Yes`.

Em **Request interception rules**, ative a regra **Is in target scope**. Em seguida, abra o navegador do Burp e acesse a página de **Login**.

```
http://localhost:3000/#/login
```

No campo **E-mail**, preencha com o e-mail do administrador, que pode ser encontrado no feedback do produto **Apple Juice (1000ml)**. O e-mail é: `admin@juice-sh.op`.

Volte para o **Burp Suite** e clique no botão `Intercept is off` para ativar a interceptação.

Na página de **Login**, insira uma senha aleatória e clique em `Login`.

No **Burp Suite**, pressione o botão direito do mouse e selecione `Send to Intruder`.

Em seguida, desative a interceptação clicando em `Intercept is on`, antes de navegar até a aba **Intruder**.

Na aba **Intruder**, clique em `Clear`. Selecione o valor da senha, que está entre aspas e destacado em verde, logo após "password", e clique em `Add`. 

Por fim, vá para a aba **Payloads**. Na seção **Payload Options**, clique em `Load` e escolha uma lista de senhas comuns, como a que se encontra abaixo. 

```
https://github.com/danielmiessler/SecLists/blob/master/Passwords/Default-Credentials/default-passwords.txt
```
Clique em `Start Attack` e aguarde enquanto o **Burp Suite** processa as informações. Após um período, o **Burp** indicará a senha correta para a conta.

![Password Strength](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Password%20Strength.png)

Teste a senha encontrada, `admin123`, e você conseguirá acessar a conta do administrador.

### 2. Redefinir a Senha de Jim (Reset Jim's Password ⭐⭐⭐)

Navegando pelos **produtos** da loja Juice Shop, é possível notar que o usuário Jim sempre deixa comentários relacionados a Star Trek.

No Green Smoothie: 

<div align="center">
  
“Fresh out of a _replicator_. “

</div>

No OWASP Juice Shop Holographic Sticker:

<div align="center">
  
“Looks spacy on Bones’ new _tricorder_!”

</div>

No OWASP Juice Shop-CTG Velcro Path:

<div align="center">
  
“Looks so much better on my uniform than the boring _Starfleet_ symbol.”

</div>

Procurando por "Jim Star Trek" no Google, encontra-se um personagem chamado **James T. Kirk**. Com essas informações, podemos tentar descobrir a resposta para a pergunta secreta de Jim.

Vá para a página de **Redefinição de senha**.

```
http://localhost:3000/#/forgot-password
```
Primeiro, insira o e-mail de Jim, que pode ser encontrado em seus feedbacks: `jim@juice-sh.op`.

Podemos ver então que a **Pergunta de segurança** é sobre o nome do meio do irmão mais velho de Jim, ou James, no caso. 

![Question](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Question.png)

Ao buscar por essa informação no Google, descobrimos que o nome do meio do irmão mais velho de James é **Samuel**. 

Insira essa informação no campo da **Pergunta de segurança** e defina uma nova senha para Jim. Clique em `Alterar`.

Feito isso, agora é possível fazer login na conta de Jim com a nova senha atribuída.

![Jim](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Jim.png)

---

<div align="center">
  
### Recomendações

</div>

**1. Use Senhas Fortes e Complexas:** Exija senhas complexas que incluam uma combinação de letras maiúsculas e minúsculas, números e caracteres especiais. Implemente políticas de expiração e histórico de senhas.

**2. Implementação de Multi-Fator de Autenticação (MFA):** Adote métodos de MFA, como códigos enviados por SMS, aplicativos de autenticação, ou biometria. Isso adiciona uma camada extra de segurança além da senha.

**3. Proteja Contra Ataques de Força Bruta:** Use limites de tentativas de login e bloqueie temporariamente contas após várias tentativas malsucedidas. Implemente captchas para dificultar a automação dos ataques.

---
