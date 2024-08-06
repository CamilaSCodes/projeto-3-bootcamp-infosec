---

<div align="center">

## Exposição de Dados Sensíveis

</div>

A vulnerabilidade de exposição de dados sensíveis ocorre quando informações confidenciais são acessadas, divulgadas ou obtidas por pessoas não autorizadas. Esses dados podem incluir informações pessoais identificáveis (PII), dados financeiros, informações de saúde, segredos comerciais, entre outros.

### 1. Documento Confidencial (Confidential Document ⭐)

Ao acessar a página **Sobre Nós** e clicar no link que leva aos **Termos de Uso**, é possível observar que o documento está armazenado em um diretório chamado `ftp`.

![About Us](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/About%20Us.png)

Acesse o diretório: 

```
http://localhost:3000/ftp
```

Agora, você pode ter acesso à arquivos que não deveriam estar disponíveis ao público. Como exemplo, clique no arquivo `acquisitions.md`. Você terá acesso a informações confidenciais. 

![Condifendial Document](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Confidential%20Document.png)

### 2. Perseguição Meta-geográfica (Meta Geo Stalking ⭐⭐)

Acesse a **Parede de Fotos**. Ao rolar para baixo, você encontrará uma foto de uma pessoa fazendo caminhada.

![Condifendial Document](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Parede%20de%20Fotos%20-%20Meta%20Geo%20Stalking.png)

Para verificar se é possível extrair informações confidenciais a partir desta foto, comece salvando-a. Note que a foto está nomeada como `favorite-hiking-place`, o que revela o local preferido para caminhadas do usuário que a publicou, John.

Voltando à página principal e clicando em qualquer produto, é possível observar nas avaliações que o e-mail padrão dos usuários segue o formato **nome do usuário + @juice-sh.op**. Portanto, podemos inferir que o e-mail de John é `john@juice-sh.op`. 

Estando em posse dessas informações, vamos tentar descobrir as credenciais de John. Vá até a página de login e clique em `Esqueceu sua senha?`. Ao ser redirecionado, insira o e-mail de John no campo **E-mail**. 

Acesse o campo **Pergunta de segurança** e note que, no caso de John, a pergunta refere-se ao seu local de caminhada preferido, o qual é justamente o que a foto exibe. 

Se John não tiver sido cuidadoso o suficiente, as informações sobre o local onde a foto foi tirada podem ser obtidas por meio dos **metadados**.

Para verificar, utilize uma ferramenta especializada em leitura de metadados, como o **ExifTool**, por exemplo. Rode os seguintes comandos.

```
sudo apt install libimage-exiftool-perl
exiftool favorite-hiking-place.png
```

No final do output, é possível encontrar a localização exata do GPS onde John estava quando tirou a foto. Copie esta informação e substitua "deg" por "°" para facilitar a pesquisa.

```
36°57’31.38″ N 84°20’53.58″ W
```

Insira essas coordenadas no Google Maps para obter a sua localização. No caso, elas correspondem à **Daniel Boone National Forest**.

![Daniel Boone National Forest](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/Daniel%20Boone%20National%20Forest.png
)

Volte à página de redefinição de senha e insira a localização encontrada no campo **Pergunta de segurança**. Em seguida, defina uma nova senha para a conta de John.

Agora, você deve conseguir acessar a conta de John com a nova senha e até mesmo atualizar suas informações.

![John](https://github.com/CamilaSCodes/projeto-3-bootcamp-infosec/blob/main/imagens-vulnerabilidades/John.png)

<div align="center">

---

### Recomendações

</div>

**1. Redução de Dados:** Coleta e armazene apenas os dados necessários para suas operações e elimine dados que não são mais necessários.

**2. Criptografia:** Use criptografia para proteger dados em trânsito e em repouso. Isso inclui dados armazenados em bancos de dados e arquivos, bem como dados enviados por e-mail ou outros meios de comunicação.

**3. Controle de Acesso:** Implemente controles de acesso rigorosos. Garanta que apenas usuários autorizados possam acessar dados sensíveis, usando autenticação multifatorial (MFA) e privilégios mínimos.

**4. Políticas e Treinamento:** Desenvolva políticas claras sobre o manuseio de dados sensíveis e ofereça treinamento regular para funcionários sobre boas práticas de segurança e como reconhecer ameaças.

---
