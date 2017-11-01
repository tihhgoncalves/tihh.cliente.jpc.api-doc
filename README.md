A API do Jesus Para Crianças (JPC)
==================================

# Introdução

A API do Jesus Para Crianças (JPC) possibilita que aplicações se comuniquem com a sua conta no sistema. Este documento explica como o Jesus Para Crianças (JPC) funciona, quais são os objetos envolvidos e como esta comunicação pode ser feita. Esta é a primeira versão da API, ainda em versão beta, algumas mudanças e melhorias serão implementadas futuramente.

A URL base da API (endpoint) é http://publico.tiago.art.br/jpc-api

# Apenas JSON

A API só suporta JSON, nós não vamos dar suporte a outro formato. Mesmo que você não utilize o header ```Content-Type: application/json; charset=utf-8``` a resposta será em JSON e com charset utf-8.



Usuários
====
# Fazendo login para receber um token.

### Request:

```GET /login```

### Response:

```json
[
    {
        "code": "200",
        "data": {
            "token": "9b4ed8d73052eaaa19f350b72e89ef44",
            "id": "1",
            "name": "Tihh Gonçalves",
            "avatar": "tihh.jpg",
            "gender": "M",
            "age": "18"
        }
    }
]
```

Autor

Esse API REST de PHP foi desenvolvido por Tihh Gonçalves (tiago@tiago.art.br).
 
![logo](https://raw.githubusercontent.com/tihhgoncalves/tihh.cliente.jpc.api-doc/master/logo.png)

Mais informações: www.tiago.art.br
