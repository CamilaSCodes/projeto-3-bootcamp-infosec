---

<div align="center">

## Componentes Vulneráveis 

</div>

A vulnerabilidade de componentes vulneráveis refere-se a riscos de segurança decorrentes do uso de bibliotecas, frameworks e outros componentes de software que contêm falhas conhecidas. 

### 1. Typosquatting Legado (Legacy Typosquatting ⭐⭐⭐⭐)

Acesse o diretório **ftp**. Para mais informações de como esse diretório foi encontrado, veja o [primeiro desafio](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/tree/main/exposição-de-dados-sensíveis).  

```
http://localhost:3000/ftp
```

Abra o arquivo `package.json.bak`. Ao abri-lo, complete a URL com "%2500.md".

```
localhost:3000/ftp/package.json.bak%2500.md
```

Ao pressionar `Enter`, o download do arquivo será iniciado. Abra-o e verifique que, na seção **dependecies**, há uma biblioteca vulnerável utilizada para Typosquatting, chamada **“epilogue-js”**.

Agora, é necessário informar a equipe do Juice Shop. Para isso, abra o menu, clique em **Comentário dos Clientes** e, em **Comentário**, digite o nome do módulo.

![Epilogue-js](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Epilogue-js.png)

Em seguida, atribua uma classificação, complete o Captcha e clique em `Enviar`.

### 2. Ataque à Cadeia de Suprimentos (Supply Chain Attack ⭐⭐⭐⭐⭐)

Novamente, acesse o arquivo `package.json.bak`. 

Navegando até a seção **devDependencies**, você encontrará um componente vulnerável chamado **"eslint-scope"**.

A equipe do Juice Shop precisa ser informada sobre esta segunda vulnerabilidade. Mais informações podem ser encontradas no link abaixo.

```
https://github.com/eslint/eslint-scope/issues/39
```

Repita o processo do desafio anterior, enviando um comentário com o link que descreve o problema.

![Eslint-scope](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Eslint-scope.png)

Escolha uma classificação, complete o Captcha e clique em `Enviar`.

---

<div align="center">

### Recomendações

</div>

**1. Atualizações Regulares:** Mantenha todos os componentes e bibliotecas atualizados. Isso inclui o sistema operacional, servidores, frameworks, e bibliotecas de terceiros. Acompanhe os lançamentos de novos patches e atualizações de segurança.

**2. Gerenciamento de Dependências:** Use gerenciadores de dependências que verificam a integridade e a segurança dos pacotes. Mantenha uma lista de permissões de dependências e evite usar pacotes desatualizados ou não mantidos.

**3. Revisões de Código:** Realize revisões de código regulares e adote práticas de desenvolvimento seguro. Isso inclui verificar a segurança de componentes externos e garantir que o código não introduza vulnerabilidades.

**4. Configuração Segura:** Certifique-se de que todos os componentes e serviços estejam configurados de forma segura. Isso pode incluir desabilitar funcionalidades desnecessárias, usar configurações padrão seguras, e proteger arquivos e diretórios sensíveis.

---
