<div style="display: flex; justify-content: left; width: 100%;">
    <span style="padding: 4px 2rem;"><a href="https://another-equipe.github.io/SIGA-API-documentation/">Português</a></span>
    <span style="padding: 4px 2rem;"><a href="https://another-equipe.github.io/SIGA-API-documentation/lang/en/">Inglês</a></span>
</div>

## SIGA API | Documentação

O SIGA API é uma api que fornece uma integração por Rest API, e facilita a integração entre os diversos sistemas da [SaveCash](https://www.savecash.com.br/) ao portal do SIGA.

## Api Key

Para poder ultilizar a API é necessário a ultilzação de uma chave exclusiva para autenticação.

Para obtenção dessa chave [mande um email](mailto:rodrigo.zillesg@savecash.com.br) para nós solicitando uma chave.

caso a autenticação falhe será retornado a seguinte resposta

```json
{
  "status": "error",
  "error": "unauthorized"
}
```

## EndPoints

### Obter uma lista dos candidatos

#### GET

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidates?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidates?key={sua_chave}
```

Retorna uma lista dos candidatos.

**Exemplo de resposta**

```json
{
    "status": "success",
    "count": 3000,
    "next": "https://savecash.tech/wp-json/siga/v1/candidates?offset=0&limit=100&key={sua_chave}",
    "previous": null,
    "data": [
        {
            "candidate_nome": "Lorem ipsum dolor sit amet",
            "candidate_email": "email.example@hotmail.com",
            "candidate_vaga": "consultor",
            "candidate_telefone": "+5567940028922",
            "candidate_cpf": "999.999.999-99",
            "candidate_cnpj": "",
            "candidate_razao": "",
            "candidate_status": "contratado",
            "recruiter_nome": "Fabian Moura",
            "recruiter_email": "f@savecash.com.br",
            "recruiter_telefone": "+5567994984911",
            "diretor_nome": null,
            "lider_nome": null,
            "gerente_nome": null,
            "supervisor_nome": null
        },
        {
            "candidate_nome": "Lorem ipsum dolor sit amet",
            "candidate_email": "email.example@hotmail.com",
            "candidate_vaga": "consultor",
            "candidate_telefone": "+5567940028922",
            "candidate_cpf": "999.999.999-99",
            "candidate_cnpj": "",
            "candidate_razao": "",
            "candidate_status": "contratado",
            "recruiter_nome": "Fabian Moura",
            "recruiter_email": "f@savecash.com.br",
            "recruiter_telefone": "+5567994984911",
            "diretor_nome": null,
            "lider_nome": null,
            "gerente_nome": null,
            "supervisor_nome": null
        },
        {
            "candidate_nome": "Lorem ipsum dolor sit amet",
            "candidate_email": "email.example@hotmail.com",
            "candidate_vaga": "consultor",
            "candidate_telefone": "+5567940028922",
            "candidate_cpf": "999.999.999-99",
            "candidate_cnpj": "",
            "candidate_razao": "",
            "candidate_status": "contratado",
            "recruiter_nome": "Fabian Moura",
            "recruiter_email": "f@savecash.com.br",
            "recruiter_telefone": "+5567994984911",
            "diretor_nome": null,
            "lider_nome": null,
            "gerente_nome": null,
            "supervisor_nome": null
        },
        {
            "candidate_nome": "Lorem ipsum dolor sit amet",
            "candidate_email": "email.example@hotmail.com",
            "candidate_vaga": "consultor",
            "candidate_telefone": "+5567940028922",
            "candidate_cpf": "999.999.999-99",
            "candidate_cnpj": "",
            "candidate_razao": "",
            "candidate_status": "contratado",
            "recruiter_nome": "Fabian Moura",
            "recruiter_email": "f@savecash.com.br",
            "recruiter_telefone": "+5567994984911",
            "diretor_nome": null,
            "lider_nome": null,
            "gerente_nome": null,
            "supervisor_nome": null
        },

        ...

    ]
}
```

| Chave                                  | Valor                                                                 |
| -------------------------------------- | --------------------------------------------------------------------- |
| **status** _(String)_                  | Caso a requisição ocorra bem, status será `success`                   |
| **count** _(number)_                   | Quantidades de candidatos existentes                                  |
| **next** _(string \| null)_            | Link para a próxima página de candidatos, caso não haja, será `null`  |
| **previous** _(string \| null)_        | Link para a página anterior de candidatos, caso não haja, será `null` |
| **candidates** _(array\<Candidates\>)_ | Array com os candidatos                                               |

<hr>

### Obter um candidato especifíco

#### GET

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidates/{numero_de_telefone}?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidates/{numero_de_telefone}?key={sua_chave}
```

Retorna o candidado que tenha o numero de telefone

##### O campo de telefone deve estar sanitizado, apenas com números

**Exemplo de resposta**

```json
{
  "status": "success",
  "data": {
    "candidate_nome": "Lorem ipsum dolor sit amet",
    "candidate_email": "example.mail@gmail.com",
    "candidate_vaga": "gerente",
    "candidate_telefone": "+5531984821900",
    "candidate_cpf": "999.999.999-99",
    "candidate_cnpj": "",
    "candidate_razao": "",
    "candidate_status": "contratado",
    "recruiter_nome": "Lorem ipsum dolor sit amet",
    "recruiter_email": "example.mail@gmail.com",
    "recruiter_telefone": "+5531983707444",
    "diretor_nome": null,
    "lider_nome": null,
    "gerente_nome": null,
    "supervisor_nome": null
  }
}
```

| Chave                    | Valor                                                                                                       |
| ------------------------ | ----------------------------------------------------------------------------------------------------------- |
| **status** _(String)_    | Caso a requisição ocorra bem, status será `success`, caso não seja encontrado nenhum candidato, `not-found` |
| **candidate** _(Object)_ | Dados do candidato

<hr>

### Obter um time

#### GET

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/team/{id}?key={chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/team/{id}?key={chave}
```

Retorna todo o time de um candidato

**Exemplo de resposta**

```json
{
  "status": "success",
  "data": {
    "diretor": [{}, {}, {}],
    "lider": [{}, {}, {}],
    "gerente": [{}, {}, {}],
    "supervisor": [{}, {}, {}, {}],
    "consultor": [{}, {}, {}, {}],
  },
  "date": 1646949194
}
```

<hr>

### Distratar candidato

#### POST

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidate?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidate?key={sua_chave}
```

Distrata um candidato, lhe envia um distrato e delete seu úsuario na plataforma, tranfere seu time para outro candidato da mesma hierarquia.

#### body da requisição

```
{
    "trigger": "distract-candidate",
    "from": {id_que_sera_distratado},
    "to": {id_de_quem_assumirá_a_equipe},
}
```

### Distratar time

#### POST

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidate?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidate?key={sua_chave}
```

#### body da requisição

```
{
    "trigger": "distract-team",
    "id": {id_do_superior},
}
```

Distrata _todo o time_ a partir do primeiro nó. Se um gerente for passado, todos os subordinados(supervisor, consultor) dele serão distratados.


**Exemplo de resposta**

```json
{
    "status": "success",
    "data": {
        "distracted": {
            "id": "71796",
            "candidate_email": "mbugler62@addtoany.com",
            "recruiter_email": "f@savecash.com.br",
            "candidate_vaga": "diretor"
        },
        "assumed": {
            "id": "71796",
            "candidate_email": "mbugler62@addtoany.com",
            "recruiter_email": "f@savecash.com.br",
            "candidate_vaga": "diretor"
        },
        "old_team": {
            ...
        },
        "new_team": {
            ...
        }
    },
    "date": 1646949194
};
```

### Promover candidato

#### POST

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidate?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidate?key={sua_chave}
```

#### body da requisição

```
{
    "trigger": "promote-candidate",
    "id": {id_do_candidado},
    "new_recruiter_id": {id_do_novo_recrutador},
    "hierarquie": "{nova_posição}",
    "to_assume": {id_de_quem_assumirá_o_time_do_promovido}
}
```

Promove um candidato _todo o time_ a partir do primeiro nó. Se um gerente for passado, todos os subordinados(supervisor, consultor) dele serão distratados.


### Mandar distrato

#### POST

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidate?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidate?key={sua_chave}
```

#### body da requisição

```
{
    "trigger": "send-distract",
    "id": {id_do_candidado},
}
```

Manda um distrato ao candidato com ID especificado


### Mandar contrato SCP

#### POST

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidate?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidate?key={sua_chave}
```

#### body da requisição

```
{
    "trigger": "send-spc-contract",
    "id": {id_do_candidado},
}
```

Manda um contrato SCP ao candidato com ID especificado

### Mandar contrato de anexo

#### POST

> ambiente de desenvolvimento

```
https://siga.devsavecash.xyz/wp-json/siga/v1/candidate?key={sua_chave}
```

> ambiente de produção

```
https://savecash.tech/wp-json/siga/v1/candidate?key={sua_chave}
```

#### body da requisição

```
{
    "trigger": "send-attachment-contract",
    "id": {id_do_candidado},
}
```

Manda um contrato de anexo ao candidato com ID especificado

## Páginação

A lista de candidatos é _retornada em partes_. Você pode customizar a forma como a resposta é páginada por meio dos parâmetros `offset` e `limit`.

```
https://savecash.tech/wp-json/siga/v1/candidates?offset={numero}&limit={numero}&key={sua_chave}
```

| Parâmetro             | Valor                                                                                                                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **offset** _(number)_ | `offset` define a partir de qual registro a resposta começará. Por exemplo, um `offset=5` trará como primeiro ítem da lista o 5º registro no banco de dados. Deve ser um número positivo. _Padrão é 0_ |
| **limit** _(number)_  | `limit` define quantos registros serão buscados. Por exemplo, um `limit=30` trará os 30 registros á partir do `offset`. Valor máximo é 100. _Padrão é 100_                                             |

> No corpo da resposta as propriedades `next` e `previous` fornecem a URL para a página posterior e anterior da páginação.
