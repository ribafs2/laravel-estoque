# laravel-estoque

## Controle de Estoque simplificado com Laravel 11

Criar um CRUD com laravel e fazer tudo funcionar é algo muito trivial, pois seguindo as convenções o  laravel faz quase tudo sozinho.

Mas efetuar o cadastro no estoque ao mesmo tempo em que cadastra na tabela de compras já não é tão simples. Como também a cada venda abater a quantidade no estoque do referido id, também não. 

É algo muito interessante usar o Eloquent ORM e o QueryBuuilder para controlar o fluxo do código do laravel.

É isso que mostro neste protótipo de estoque, especialmente nos controllers Buys e Sales.

Para complementar veja o repo:
https://github.com/ribafs2/laravel-projetos

Com vários projetos e um livro.


## Como executar

Descompactar

Acessar a pasta

composer install

Criar o banco e ajustar no .env

php artisan migrate --seed

php artisan serve

http://127.0.0.1:8000


# Sequência de cadastro

Products já vem com dois  registros no seeder, banana e manga

Vamos efetuar duas compras de bananas

comprar
	banana - 100 - 1 - hoje

Ver Estoques
	Veja que o id das bananas está com quantity 100
	
comprar	
	banana - 10 - 1 - hoje

Ver Estoques
	Veja que o id das bananas está com quantity 110 (os 100 que havia mais estes 10 comprados)
	
Está funcionando redondinho.	

