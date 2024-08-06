---

<div align="center">

## Problemas Criptográficos

</div>

Problemas criptográficos são vulnerabilidades relacionadas à forma como os sistemas utilizam criptografia para proteger dados. Esses problemas podem surgir de várias maneiras e têm o potencial de comprometer a confidencialidade e a integridade das informações. 

### 1. Criptografia Estranha (Weird Crypto ⭐⭐)

Vamos investigar o algoritmo de criptografia utilizado pelo Juice Shop no repositório do GitHub onde ele está localizado.

```
https://github.com/juice-shop/juice-shop
```

Ao navegar pelo repositório, você encontrará um arquivo chamado `insecurity.ts` na pasta `lib`. 
```
https://github.com/juice-shop/juice-shop/blob/master/lib/insecurity.ts
```

Dentro deste arquivo, podemos identificar na linha 43 que o algoritmo utilizado é o **md5**, que possui diversas vulnerabilidades conhecidas.

Acesse a página de contato e informe ao Juice Shop sobre a vulnerabilidade do algoritmo no campo de comentário.

![MD5](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/MD5.png)

Preencha o CAPTCHA e clique em `Enviar`.

---

<div align="center">
  
### Recomendações

</div>

**1. Utilize Algoritmos Criptográficos Confiáveis:** Use algoritmos que sejam amplamente aceitos e considerados seguros. Evite algoritmos obsoletos ou vulneráveis.

**2. Gerencie Chaves de Forma Segura:** Assegure-se de que suas chaves criptográficas sejam armazenadas de forma segura, com acesso restrito e, se possível, utilizando hardware seguro.

**3. Evite Criptografia Personalizada:** Criptografia feita por conta própria pode ter falhas. Utilize algoritmos e técnicas que foram revisados e testados pela comunidade de segurança.

---
