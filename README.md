# Day-4

This project is a small API built with FastAPI, designed to practice the concepts of routes, parameters, and dynamic responses.
The application simulates a simple sales system, allowing users to list the total number of sales and retrieve the details of each one using its ID.

###################################################################################################################################################

Este projeto é uma pequena API desenvolvida com FastAPI, com o objetivo de praticar conceitos de rotas, parâmetros e respostas dinâmicas.
A aplicação simula um sistema de vendas, permitindo listar o total de vendas e consultar os detalhes de cada uma através de um ID.



First, we have this line:

from fastapi import FastAPI


This line imports the FastAPI library — the framework I used to build this API.

Then we have:

app = FastAPI()


This creates an instance of the FastAPI application.
Basically, it means my app is now a FastAPI project.

Next, I created a dictionary called vendas (which means “sales” in Portuguese):

vendas = {
    1: {"item": "lata", "preco_unitario": 4, "quantidade": 5},
    2: {"item": "garrafa 2L", "preco_unitario": 15, "quantidade": 5},
    3: {"item": "garrafa 750ml", "preco_unitario": 10, "quantidade": 5},
    4: {"item": "lata mini", "preco_unitario": 2, "quantidade": 5},
}


Each number (1, 2, 3, 4) is a sale ID, and inside each one we have the product’s details:
the item name, its unit price, and the quantity sold.

Then come the routes, which define where users go when they access the API:

@app.get("/")
def home():
    return {"vendas": len(vendas)}


The decorator @app.get("/") defines a route — in this case, the home page (/).
The home() function returns how many sales exist in total.
The len(vendas) part counts how many items are in the vendas dictionary.

Now for the second route:

@app.get("/vendas/{id_venda}")
def pegar_venda(id_venda: int):
    if id_venda in vendas:
        return vendas[id_venda]
    else:
        return {"Erro": "ID venda inexistente"}


This route shows the details of a specific sale based on its ID.
For example, if you access /vendas/1, it returns the data for sale number 1.

The id_venda: int means that the parameter must be an integer.
The if id_venda in vendas checks if that ID exists.
If it does, the function returns its details (return vendas[id_venda]).
If it doesn’t, the else part returns an error message saying the ID doesn’t exist.

For this project, I used FastAPI, Python 3 and Uvicorn (which runs the local server so I can test the API).
It was my first time working with FastAPI, and I learned how to create routes, return data, and work with dictionaries inside an API.



###################################################################################################################################################


Primeiro, temos esta linha:

from fastapi import FastAPI


Ela serve para importar a biblioteca FastAPI, que é o framework que usei para criar a API.

Depois vem:

app = FastAPI()


Aqui eu estou dizendo que o meu aplicativo (app) vai ser feito com o FastAPI. É como se eu dissesse: “agora o meu programa é um app da FastAPI”.

Em seguida, temos o dicionário:

vendas = {
    1: {"item": "lata", "preco_unitario": 4, "quantidade": 5},
    2: {"item": "garrafa 2L", "preco_unitario": 15, "quantidade": 5},
    3: {"item": "garrafa 750ml", "preco_unitario": 10, "quantidade": 5},
    4: {"item": "lata mini", "preco_unitario": 2, "quantidade": 5},
}


Aqui eu criei um dicionário de vendas, onde cada número (1, 2, 3, 4) é o ID da venda, e dentro de cada um tem as informações do item: nome, preço e quantidade.

Depois vem as rotas, que dizem pra onde o usuário vai quando acessa a API:

@app.get("/")
def home():
    return {"vendas": len(vendas)}


O @app.get("/") define uma rota, que é o “endereço” da página principal (/ quer dizer a home page).
A função home() retorna a quantidade total de vendas.
O len(vendas) serve pra contar quantos itens tem no dicionário vendas.

Agora temos outra rota:

@app.get("/vendas/{id_venda}")
def pegar_venda(id_venda: int):
    if id_venda in vendas:
        return vendas[id_venda]
    else:
        return {"Erro": "ID venda inexistente"}


Essa rota mostra os detalhes de uma venda específica, usando o número do ID.
Por exemplo: se eu acessar /vendas/1, ele mostra os dados da venda 1.

A parte id_venda: int quer dizer que o ID precisa ser um número inteiro.
O if id_venda in vendas verifica se o ID existe.
Se existir, ele mostra as informações (return vendas[id_venda]).
Se não existir, o else devolve uma mensagem dizendo que o ID é inexistente.

Nesse projeto eu usei o FastAPI, Python 3 e o Uvicorn (que serve pra rodar o servidor local e testar a API).
Foi meu primeiro contato com FastAPI, e deu pra entender bem como criar rotas, retornar dados e trabalhar com dicionários.
