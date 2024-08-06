---

<div align="center">

## Validação Imprópria De Input 

</div>

A vulnerabilidade de validação imprópria de input ocorre quando um sistema ou aplicação não verifica ou filtra corretamente os dados de entrada fornecidos pelo usuário. 

### 1. Registro Repetitivo (Repetitive Registration ⭐)

Acesse a página de **Registro**. 

```
http://localhost:3000/#/register
```

Preencha todos os campos obrigatórios para completar o registro. Primeiro, certifique-se de que os valores nos campos **Senha** e **Repita a senha** coincidem.

![Jane Doe](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Jane%20Doe.png)

Em seguida, volte ao campo **Senha** e altere o valor para algo diferente. Clique em `Cadastre-se`.

Note que o sistema exibe uma mensagem de sucesso, indicando que a verificação para confirmar se os valores da senha são iguais ocorre apenas da primeira vez.

Agora, você deve ser capaz de fazer login com o usuário, utilizando o valor inserido no campo **Senha** que não foi validado.

![Repetitive Registration](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Repetitive%20Registration.png)

### 2. Registro De Usuário Vazio (Empty User Registration ⭐⭐)

Se ainda não o fez, baixe e acesse a distribuição [Kali Linux](https://www.kali.org). 

Ao fazer login, procure e abra o aplicativo **Burp Suite**. Navegue até **Proxy** e clique em `Open browser`.

Com o Browser aberto, navegue até a página de **Registro**. 

```
http://localhost:3000/#/register
```

Preencha todos os campos necessários, volte ao **Burp Suite** e ative a intercepção do tráfego clicando em `Intercept is off`, o que fará o botão ficar azul.

De volta ao Browser, clique em `Cadastre-se`. 

No **Burp Suite**, clique em `Forward` e observe que a requisição do usuário, contendo todas as suas informações, foi interceptada.

![Empty User Registration](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Empty%20User%20Registration.png)

Apague os valores de e-mail e senha do usuário, que estão entre aspas e destacados em verde. Em seguida, clique em `Forward` e depois em `Intercept is on`.

Feito isso, um novo usuário vazio foi registrado com sucesso, o que não deveria ter sido possível.

---

<div align="center">

### Recomendações

</div>

**1. Validação no Lado do Servidor e do Cliente:** Sempre valide dados no lado do servidor, mesmo que você já faça a validação no lado do cliente. Isso ajuda a proteger contra ataques onde o lado do cliente pode ser manipulado.

**2. Sanitização de Input:** Realize a sanitização dos dados de entrada para remover caracteres indesejados e perigosos. Isso é especialmente importante para campos que serão exibidos em uma interface de usuário ou executados em comandos.

**3. Verificação de Comprimento e Formato:** Use expressões regulares ou outras técnicas para verificar se os dados de entrada estão no comprimento e formato esperados. 

**4. Autorização e Autenticação:** Certifique-se de que os usuários tenham permissão para enviar certos dados e que esses dados estejam corretamente autorizados para sua finalidade.

**5. Evitar Interpretação de Dados:** Evite a interpretação direta de dados de entrada em comandos SQL, scripts ou outros contextos sensíveis.

---
