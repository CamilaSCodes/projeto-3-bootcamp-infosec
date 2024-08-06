---

<div align="center">

## Configuração Incorreta de Segurança

</div>

A vulnerabilidade de configuração incorreta de segurança ocorre quando sistemas ou aplicativos não são configurados corretamente, resultando em falhas de segurança que podem ser exploradas por atacantes. Esta vulnerabilidade é bastante comum e pode ter várias causas, incluindo configurações padrão inseguras, permissões inadequadas, falta de patches de segurança, ou a não desativação de funcionalidades desnecessárias.

### 1. Manipulação de Erro (Error Handling ⭐)

Para provocar um erro, acesse a página de login do site.

```
http://localhost:3000/#/login
```
No campo **E-mail**, insira apenas um apóstrofo: “ ‘ ”. No campo **Senha**, insira qualquer senha aleatória.

Clique em `Login` e você verá uma mensagem de erro em vermelho, que não faz muito sentido, mas deveria indicar a ocorrência de um erro.

![Error Handling](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Error%20Handling.png)

### 2. Interface Obsoleta (Deprecated Interface ⭐⭐)

Inspecione a página do Juice Shop, acesse a aba **Sources** e abra o arquivo `main.js`. Observe que os tipos de arquivos permitidos são .pdf, .zip e, dentre eles, o menos comum e desatualizado, **.xml**.

Caso não esteja logado, faça login e navegue até a página de **Reclamação**.
```
http://localhost:3000/#/complain
```

Digite uma mensagem aleatória e clique em `Escolher arquivo`. Altere o campo **Arquivos personalizados** para **Todos os arquivos**, selecione um arquivo **.xml** e clique em `Abrir`. 

![Deprecated Interface](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Deprecated%20Interface.png)

Em seguida, clique em `Enviar` e observe que o arquivo de formato incomum foi enviado sem problemas.

---

<div align="center">
  
### Recomendações

</div>

**1. Configuração Mínima Necessária:** Configure seus sistemas e aplicativos apenas com as permissões e funcionalidades essenciais. Reduza a superfície de ataque desabilitando serviços e funcionalidades desnecessárias.

**2. Segurança por Design:** Implemente práticas de segurança desde o início do desenvolvimento. Garanta que as configurações padrão sejam seguras e modifique-as conforme necessário.

**3. Revisão de Configurações:** Realize revisões regulares e auditorias de configuração para identificar e corrigir configurações incorretas ou inseguras.

---
