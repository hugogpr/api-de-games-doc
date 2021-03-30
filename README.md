# API de Games

>Essa API é utilizada para tal e tal......

## Endpoints

### GET /games
Esse endpoint é responsavel por retornar a listagem de todos os games cadastrados no banco de dados.

#### Parametros
nenhum

#### Respostas
##### OK! 200
Caso essa resposta aconteça você irá receber a listagem de todos os games.

Exemplo de resposta:
```json
[
    {
        "id": 3,
        "title": "Star Wars - Battle Front 3",
        "year": 2018,
        "price": 350
    },
    {
        "id": 5,
        "title": "Minecraft",
        "year": 2011,
        "price": 50
    },
    {
        "id": 6,
        "title": "GTA V",
        "year": 2013,
        "price": 69
    }
]
```

##### Falha na autenticação! 401
Caso essa reposta aconteça, isso significa que alguma falha durante o processo de autenticação da requisição. Motivos: Token inválido, Token expirado.

Exemplo de resposta:
```json
{
    "err": "Token invalido"
}
```
### POST /auth
Esse endpoint é responsavel por fazer o processo de login.

#### Parametros
**email** - email do usuario cadastrado no sistema.

**password** - senha do usuario cadastrado no sistema, com aquele determinado email.

Exemplo:
```json
{
    "email": "teste@gmail.com",
    "password": "123123"
}
```

#### Respostas
##### OK! 200
Caso essa resposta aconteça você irá receber um token JWT para conseguir acessar endpoints protegidos na API.

Exemplo de resposta:
```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJ0ZXN0ZUBnbWFpbC5jb20iLCJpYXQiOjE2MTcxMDc4NDEsImV4cCI6MTYxNzExMTQ0MX0.UkLIQnH_4usdmDX-lLh_eUTGIRGbFGnGUIQxcedP4e4"
}
```

##### Falha na autenticação! 401
Caso essa reposta aconteça, isso significa que alguma falha durante o processo de autenticação da requisição. Motivos: Senha e email incorretos, email não cadastrado no sistema.

Exemplo de resposta:
Senha não correspondendo ao email cadastrado.
```json
{
    "err": "Credenciais inválidas!"
}
```

Email escrito errado. 
```json
{
    "err": "E-mail invalido!"
}
```
Email não cadastrado.
```json
{
    "err": "E-mail não cadastrado"
}
```
