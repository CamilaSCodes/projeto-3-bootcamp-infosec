---

<div align="center">

## Redirecionamento Não Validado 

</div>

A vulnerabilidade de redirecionamento não validado ocorre quando uma aplicação web permite que usuários forneçam uma URL de destino para a qual a aplicação redirecionará, sem validar ou restringir adequadamente essa URL. 

### 1. Lista de Permissões Desatualizada (Outdated Allowlist ⭐)

Na **Página Inicial** do Juice Shop, clique com o botão direito do mouse e selecione **Inspecionar elemento**.

Acesse a aba **Sources** e abra o arquivo `main.js`.

No arquivo, procure pelo termo "blockchain". Copie a URL associada e cole-a no final da URL do navegador.

```
localhost:3000/redirect?to=https://blockchain.info/address/1AbKfgvw9psQ41NbLi8kufDQTezwG8DRZm
```

Ao pressionar `Enter`, você será direcionado para um dos endereços de criptomoedas do Juice Shop que não é mais promovido.

![Blockchain](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Blockchain.png)

<div align="center">

---

### Recomendações

</div>

**1. Evitar Redirecionamentos Baseados em Entradas do Usuário:** Sempre que possível, evite redirecionar usuários com base em dados que eles podem manipular, como parâmetros de URL ou entradas de formulários.

**2. Validação Estrita de Entradas:** Se você precisar usar entradas do usuário para redirecionar, implemente uma validação estrita para garantir que apenas URLs esperadas ou formatos de URLs sejam aceitos.

---
