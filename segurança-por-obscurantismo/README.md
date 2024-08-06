## Segurança por Obscurantismo

</div>

A segurança por obscurantismo (ou "security through obscurity", em inglês) é uma abordagem na qual a proteção de um sistema depende do segredo de seus mecanismos de segurança ou detalhes de implementação. Essa técnica é considerada uma prática controversa e geralmente não é recomendada como a única linha de defesa em um sistema de segurança. 

### 1. Inspeção da Política de Privacidade (Privacy Policy Inspection ⭐⭐⭐)

Vá para a página de **Política de Privacidade** do Juice Shop.

```
http://localhost:3000/#/privacy-security/privacy-policy
```
Ao passar o mouse sobre o texto, simulando uma leitura, é possível observar que, na terceira linha, o texto “http://localhost” fica destacado.

![Colorful Privacy Policy](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Colorful%20Privacy%20Policy.png)

O mesmo ocorre com as primeiras palavras da seção **A1.2 Usage Data**, que são “We may also”.

Pressione o botão direito e selecione `Inspect (Q)`. Ao procurar por esses textos no **Inspector**, podemos ver que eles estão dentro de uma classe chamada **“hot”**.

Procure pelos demais textos com esse padrão e reúna todos eles. Com base no primeiro texto, podemos inferir que o resultado será uma URL.

```
http://localhost:3000/we/may/also/instruct/you/to/refuse/all/reasonably/necessary/responsibility
```

Insira esta URL no navegador e pressione `Enter`. Você será redirecionado para uma nova página.

![Privacy Policy](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Privacy%20Policy.png)

<div align="center">

---
  
### Recomendações

</div>

**1. Transparência e Boas Práticas:** Use métodos de segurança estabelecidos e bem documentados, como criptografia robusta e autenticação multifatorial.

**2. Documentação Clara:** Documente todas as práticas de segurança e configurações do sistema de forma clara e acessível.

---
