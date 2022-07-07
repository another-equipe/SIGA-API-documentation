<hr>

<div style="display: flex; justify-content: left; width: 100%;">
    <span style="padding: 16px;"><a href="https://another-equipe.github.io/SIGA-API-documentation/">Português</a></span>
    <span style="padding: 16px;"><a href="https://another-equipe.github.io/SIGA-API-documentation/lang/en/">Inglês</a></span>
</div>

<hr>

## SIGA API | Documentação


O SIGA API é uma api que fornece uma integração por Rest API, e facilita a integração entre os diversos sistemas da [SaveCash](https://www.savecash.com.br/) ao portal do SIGA.


## Api Key

Para poder ultilizar a API é necessário a ultilzação de uma chave exclusiva para autenticação.

Para obtenção dessa chave [mande um email](mailto:dev.waynerocha@gmail.com) para nós solicitando uma chave.

caso a autenticação falhe será retorndo a seguinte resposta

```json
{
    "status": "error",
    "error": "unauthorized"
}
```


## EndPoints

### Obter uma lista dos candidatos

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
    "candidates": [
        {
            "candidate_nome": "Lorem ipsum dolor sit amet",
            "candidate_email": "email.example@hotmail.com",
            "candidate_vaga": "consultor",
            "candidate_telefone": "+5567940028922",
            "candidate_cpf": "999.999.999-99",
            "candidate_cnpj": "",
            "candidate_razao": "",
            "candidate_status": "contratado",
            "recruiter_nome": "Fabian Moura"
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
            "recruiter_nome": "Fabian Moura"
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
            "recruiter_nome": "Fabian Moura"
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
            "recruiter_nome": "Fabian Moura"
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

| Chave  | Valor |
|---|---|
| **status** *(String)* | Caso a requisição ocorra bem, status será `success` |
| **count** *(number)*  | Quantidades de candidatos existentes |
| **next** *(string \| null)*  | Link para a próxima página de candidatos, caso não haja, será `null` |
| **previous** *(string \| null)*  | Link para a página anterior de candidatos, caso não haja, será `null` |
| **candidates** *(array\<Candidates\>)*  | Array com os candidatos |

<hr>

### Obter um candidato especifíco

```
https://savecash.tech/wp-json/siga/v1/candidates/{numero_de_telefone}?key={sua_chave}
```

Retorna o candidado que tenha o numero de telefone

**Exemplo de resposta**

```json
{
    "status": "success",
    "candidate": {
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

| Chave  | Valor |
|---|---|
| **status** *(String)* | Caso a requisição ocorra bem, status será `success`, caso não seja encontrado nenhum candidato, `not-found` |
| **candidate** *(Object)*  | Dados do candidato |

<hr>

## Páginação

A lista de candidatos é *retornada em partes*. Você pode customizar a forma como a resposta  é páginada por meio dos parâmetros `offset` e `limit`.

```
https://savecash.tech/wp-json/siga/v1/candidates?offset={numero}&limit={numero}&key={sua_chave}
```

| Parâmetro  | Valor |
|---|---|
| **offset** *(number)* | `offset` define a partir de qual registro a resposta começará. Por exemplo, um `offset=5` trará como primeiro ítem da lista o 5º registro no banco de dados. Deve ser um número positivo. *Padrão é 0* |
| **limit** *(number)*  | `limit` define quantos registros serão buscados. Por exemplo, um `limit=30` trará os 30 registros á partir do `offset`. Valor máximo é 100. *Padrão é 100* |

> No corpo da resposta as propriedades `next` e `previous` fornecem a URL para a página posterior e anterior da páginação.


