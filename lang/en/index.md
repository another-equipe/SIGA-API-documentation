<hr>

<div style="display: flex; justify-content: space-around; width: 100%;">
    <span style="padding: 4px 2rem;"><a href="https://another-equipe.github.io/SIGA-API-documentation/">Português</a></span>
    <span style="padding: 4px 2rem;"><a href="https://another-equipe.github.io/SIGA-API-documentation/lang/en/">Inglês</a></span>
</div>

<hr>

## SIGA API | Documentação


The SIGA API is an api that provides an integration by Rest API, and facilitates the integration between the various systems of [SaveCash](https://www.savecash.com.br/) to the SIGA portal.


## Api Key

To be able to use the API it is necessary to use a unique key for authentication.

To obtain this key [send an email](mailto:dev.waynerocha@gmail.com) to us requesting a key.

if authentication fails, the following response will be returned

```json
{
    "status": "error",
    "error": "unauthorized"
}
```


## EndPoints

### Get a list of candidates

```
https://savecash.tech/wp-json/siga/v1/candidates?key={sua_chave}
```

Return a list of candidates

**Response**

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

| Key  | Value |
|---|---|
| **status** *(String)* | if the request goes well, status will be `success`
| **count** *(number)*  | Quantities of existing candidates |
| **next** *(string \| null)*  | Link to next page of candidates, if not, it will be `null` |
| **previous** *(string \| null)*  | Link to previous page of candidates, if not, it will be `null` |
| **candidates** *(array\<Candidates\>)*  | Array with candidates

<hr>

### Get a specific candidate

```
https://savecash.tech/wp-json/siga/v1/candidates/{numero_de_telefone}?key={sua_chave}
```

Returns the candidate that has the phone number pass by parameter

**Response**

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
| **status** *(String)* | If the request goes well, status will be `success`, if no candidate is found, `not-found` |
| **candidate** *(Object)*  | Candidate data |

<hr>

## Pagination

The list of candidates is *returned in parts*. You can customize the way the response is paged through the `offset` and `limit` parameters.

```
https://savecash.tech/wp-json/siga/v1/candidates?offset={numero}&limit={numero}&key={sua_chave}
```

| Parâmetro  | Valor |
|---|---|
| **offset** *(number)* | `offset` defines from which register the response will start. For example, `offset=5` will bring the 5th register in the database as the first item in the list. It must be a positive number. *Default is 0* |
| **limit** *(number)*  | `limit` defines how many registers will be fetched. For example, `limit=30` will bring the 30 records from the `offset`. Maximum value is 100. *Default is 100* |

> In the response body the `next` and `previous` properties provide the URL to the next and previous page.


