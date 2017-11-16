# A API do Jesus Para Crianças (JPC)

A API do Jesus Para Crianças (JPC) possibilita que aplicações se comuniquem com a sua conta no sistema. Este documento explica como o Jesus Para Crianças (JPC) funciona, quais são os objetos envolvidos e como esta comunicação pode ser feita. Esta é a primeira versão da API, ainda em versão beta, algumas mudanças e melhorias serão implementadas futuramente.

### Sumário

- [Apenas JSON](#apenas-json)
- [Regras de Segurança](#regra-de-segurança)
- [Requisições](#requisições)
    - [Fazendo Login](#fazendo-login) ```GET /login```
    - [Retornando Usuário](#retornando-usuário) ```GET /user```
    - [Retornando Jogos](#retornando-jogos) ```GET /games```
    - [Retornando Relatório](#retornando-relatório) ```GET /school-report```
    - [Retorna Status do Game](#retorna-status-do-game) ```GET /library```

### A URL base da API:
 
```endpoint``` http://publico.tiago.art.br/jpc-api

> [@tihhgoncalves](https://github.com/tihhgoncalves) -  Para testar os _requests_ já disponíveis da API, utilize login: ```teste``` e senha: ```teste```

# Apenas JSON

A API só suporta JSON, nós não vamos dar suporte a outro formato. Mesmo que você não utilize o header ```Content-Type: application/json; charset=utf-8``` a resposta será em JSON e com charset utf-8.

# Regra de Segurança

A regra de segurança é muito simples. Através da requisição ```/login``` você recebe um _token_ e com essa chave de _token_ consegue utilizar todas as demais requisições do sistema.

Os tokens têm validade de 15 dias (na fase de desenvolvimento, 15 minutos) de utilização. Toda vez que uma nova requisição é feita com determinado token, esse prazo é zerado.

# Requisições

---

### Fazendo Login
Faz login e retorna um_token_(e informações do usuário).

#### Requisição:

```GET /login```

#### Parâmetros
 - ```mail``` - E-mail do login.
 - ```pass``` - Senha do login.

#### Resposta:

```json
{
    "code": "202",
    "data": {
        "token": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
        "id": "1",
        "name": "Nome do Aluno",
        "avatar": "avatar.jpg",
        "gender": "1",
        "age": "1986-10-01"
    }
}
```

##### Considerações
 - ```data.token``` - Token gerado automaticamente. 
 - ```data.id``` - Registro ```aluno.id```
 - ```data.name``` - Registro ```aluno.nome``` 
 - ```data.avatar``` - ~~(ainda não especificado)~~
 - ```data.gender``` - Registro ```aluno.sexo``` 
 - ```data.age``` - Registro ```aluno.data_nasc``` 

---

### Retornando Usuário
Retorna informaçoes do usuário.


#### Requisição:

```GET /user```

#### Parâmetros
 - ```token``` - _Token_ de autenticação.

#### Resposta:

```json
{
    "code": "202",
    "data": {
        "token": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
        "token_build_date": "2017-10-31 23:40:02",
        "id": "1",
        "name": "Tihh Gonçalves",
        "avatar": "",
        "gender": "",
        "age": ""
    }
}
```

##### Considerações
 - ```data.token``` - Token gerado automaticamente. 
 - ```data.token_build_date``` - Data em que o Token foi criado.
 - ```data.id``` - Registro ```aluno.id```
 - ```data.name``` - Registro ```aluno.nome``` 
 - ```data.avatar``` - ~~(ainda não especificado)~~
 - ```data.gender``` - Registro ```aluno.sexo``` 
 - ```data.age``` - Registro ```aluno.data_nasc``` 
 
---
 
### Retornando Jogos
 Retorna os jogos do usuário (aluno).
 
 
#### Requisição:
 
 ```GET /games```
 
#### Parâmetros
  - ```token``` - _Token_ de autenticação.
 
#### Resposta:
 
 ```json
    {
        "code": "202",
        "games": [
            {
                "id": "1",
                "name": "Game Biblico",
                "bundle": "http://emnomedejesus.com.br/arquivosApp/file.file"
            },
            {
                "id": "2",
                "name": "Decora Versículos",
                "bundle": "http://emnomedejesus.com.br/arquivosApp/file2.file"
            }
        ]
    }
 ```
 
##### Considerações
  - ```games.id``` - Registro ```atividade.id``` 
  - ```games.name``` - Registro ```atividade.nome``` 
  - ```games.bundle``` - Registro ```atividade.link_app``` 

---

### Retornando Relatório
 Retorna o relatório com a pontuação dos jogos do aluno.
 
 
#### Requisição:
 
 ```GET /school-report```
 
#### Parâmetros
  - ```token``` - _Token_ de autenticação.
 
#### Resposta:
 
 ```json
    {
        "code": "202",
        "games": [
            {
                "id": "1",
                "score": "350"
            },
            {
                "id": "2",
                "score": "550"
            }
            
        ]
    }
 ```
 
##### Considerações
  - ```games.id``` - Registro ```aluno_atividade.id``` 
  - ```games.score``` - Registro ```aluno_atividade.pontos```  
  

---

### Retorna Status do Game
 
 
#### Requisição:
 
 ```GET /library```
 
#### Parâmetros
  - ```token``` - _Token_ de autenticação.
 
#### Resposta:
 
 ```json
    {
        "code": "202",
        "games": [
            {
                "id": "1",
                "available": "1"
            },
            {
                "id": "2",
                "available": "0"
            }
            
        ]
    }
 ```
 
##### Considerações
  - ```games.id``` - Registro ```atividade.id``` 
  - ```games.available``` - Registro ```aqluno_atividade.status```    

# Autor

Esse API REST de PHP foi desenvolvido por Tihh Gonçalves (tiago@tiago.art.br).
 
![logo](https://raw.githubusercontent.com/tihhgoncalves/tihh.cliente.jpc.api-doc/master/logo.png)

Mais informações: www.tiago.art.br
