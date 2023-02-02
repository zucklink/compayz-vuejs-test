# Desafio

# O que preciso fazer?

Vamos ser práticos e diretos, se você quer trabalhar conosco siga os passos abaixo:

* Faça um "fork" desse projeto para sua conta GitHub.
* Implemente o desafio descrito no tópico abaixo.
* Faça um push para seu repositório com o desafio implementado.
* Envie um email para (fernandomoraes@compayz.com) com cópia para (juniorabranches@compayz.com)
  avisando que finalizou o desafio com a url do seu fork.

# Desafio

Você deverá criar 1 aplicação conforme apresentada no video

https://www.loom.com/share/02ca70dfb7d14798afc6d95a5dd91ad9

**Requisitos:**

- Listar os planos disponiveis
- Permitir selecionar plano 4D e 5D
- Permitir o usuario aumentar quantidade de dominios no plano 4D e 5D
- Permitir o usuario informar dados do cartao
    - Dados pessoais
    - Endereço de fatura do cartao
     - Consultar CEP usando API : https://viacep.com.br/
    - Dados do cartao

### Tecnologias

- Escolha umas das opções abaixo para implementar sua solução. Não se preocupe com autenticação ou seguir fielmente as cores.

#### FRONT-END

* Vue.js 2 com Nuxt

Utilizar Bootstrap (http://getbootstrap.com/)

**Recomendações gerais:**

* Não utilize frameworks que não foram indicados

### Arquitetura e documentação

No arquivo README do projeto explique o funcionamento e a arquitetura da solução adotada na sua implementação. Descreva também os passos para executar corretamente seu projeto.

### Avaliação

Entre os critérios de avaliação estão:

* Atenção aos detalhes
* Facilidade de configuração do projeto
* Performance
* Código limpo e organização
* Documentação de código
* Documentação do projeto (readme)
* Arquitetura
* Boas práticas de desenvolvimento
* Design Patterns
* Testes unitários

## JSONs de exemplo a serem utilizados na aplicação

### JSON de Planos disponiveis

##### Metadata

| Nome da Coluna | Observacao                                                |
|----------------|-----------------------------------------------------------|
| id             | Identificador do Plano                                    |
| seqno          | Sequencia que deve ser apresentado o plano para o usuario |
| name           | Nome                                                      |

##### Example

```json
{
  "data": {
    "activePlans": [
      {
        "id": 1,
        "seqno": 10,
        "name": "Plano 4D"
      },
      {
        "id": 2,
        "seqno": 20,
        "name": "Plano 5D"
      },
      {
        "id": 3,
        "seqno": 30,
        "name": "Plano 6D"
      },
      {
        "id": 4,
        "seqno": 40,
        "name": "Plano 7D"
      },
      {
        "id": 5,
        "seqno": 50,
        "name": "SPACE"
      }
    ]
  }
}

```

### JSON dados de um plano

#### Response PlanId = 1

##### Metadate

###### PlanInfo

| Nome da Coluna | Observacao             |
|----------------|------------------------|
| id             | Identificador do Plano |
| name           | Nome do Plano          |
| planBaseAmt    | Valor do Plano Base    |
| contents       | Conteudo do Plano      |

###### Contents

| Nome da Coluna   | Observacao                                                                                                                 |
|------------------|----------------------------------------------------------------------------------------------------------------------------|
| baseQuantity     | Valor inicial contido no plano                                                                                             |
| Service          | Nome do Serviço                                                                                                            |
| addOnId          | Quando presente indica que o usuario pode adicionar mais recursos daquele serviço. Serve como parametro para obter o preço |
| packageQuantity  | Indica de quantos em quantos o usuario pode adicionar recurso, exemplo: comprar pacote de SMS de 500 em 500.               |
| maxAddOnQuantity | Indica quantos pacotes extras o usuário pode adquirir no máximo.                                                           |

##### Example

````json
{
  "data": {
    "planInfo": {
      "id": 1,
      "name": "Plano 4D",
      "planBaseAmt": 284,
      "contents": [
        {
          "baseQuantity": 1,
          "service": "MEMBERZ",
          "addOnId": null,
          "packageQuantity": null,
          "maxAddOnQuantity": 1
        },
        {
          "baseQuantity": 3,
          "service": "USERS",
          "addOnId": null,
          "packageQuantity": null,
          "maxAddOnQuantity": 5
        },
        {
          "baseQuantity": 1,
          "service": "DOMAIN",
          "addOnId": 1,
          "packageQuantity": 1,
          "maxAddOnQuantity": 5
        }
      ]
    }
  }
}

````

#### Response PlanId = 2

````json
{
  "data": {
    "planInfo": {
      "id": 2,
      "name": "Plano 5D",
      "planBaseAmt": 341,
      "contents": [
        {
          "baseQuantity": 1,
          "service": "DOMAIN",
          "addOnId": 1,
          "packageQuantity": 1,
          "maxAddOnQuantity": 1
        }
      ]
    }
  }
}
````

### JSON para Obter valor adicional de um recurso conforme demonstrado no video

#### Response

##### Metadata

| Nome da Coluna | Observacao                    |
|----------------|-------------------------------|
| addOnPriceAmt  | Valor adicional de X dominios |

##### Example

````json

{
  "data": {
    "addOnPriceAmt": 70
  }
}

````
