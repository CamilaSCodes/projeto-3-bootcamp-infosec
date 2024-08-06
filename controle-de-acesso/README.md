---

<div align="center">

## Controle de Acesso

</div>

A vulnerabilidade de controle de acesso ocorre quando um sistema não aplica corretamente as regras que definem quem tem permissão para acessar recursos específicos, como dados, arquivos ou funcionalidades.

### 1. Sessão de Admin (Admin Section ⭐⭐)
 
Tente acessar a página da **Administração**.

```
http://localhost:3000/#/administration
```

Você receberá um erro 403, acompanhado da mensagem: "Você não tem permissão para acessar esta página!".

Para obter acesso, faça login como administrador. Para instruções sobre como proceder, consulte o primeiro desafio na página [SQL Injection](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/tree/main/sql-injection).

Após fazer o login, tente acessar novamente a página da **Administração**. Você deverá conseguir visualizar todos os usuários e os comentários feitos pelos clientes.

![Admin Page](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Admin%20Page.png)

### 2. Feedback de Cinco Estrelas (Five-Star Feedback ⭐⭐)

Ainda na página da **Administração**, verifique se seus privilégios estão funcionando corretamente clicando no ícone de 🗑️ ao lado do feedback de 5 estrelas.

Se tudo correu conforme o esperado, você conseguiu manipular as opiniões dos clientes sobre a loja, eliminando o feedback ideal.

![Deleted Feedback](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Deleted%20Feedback.png)

---

<div align="center">

### Recomendações

</div>

**1. Princípio do Menor Privilégio:** Garanta que os usuários tenham apenas as permissões necessárias para realizar suas tarefas.

**2. Controle de Acesso Baseado em Função (RBAC):** Atribua permissões com base nas funções que os usuários desempenham dentro da organização.

**3. Auditorias e Monitoramento:** Realize auditorias regulares de permissões e atividades de acesso. Configure alertas para detectar atividades suspeitas ou não autorizadas.

---
