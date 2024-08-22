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


## Como cheguei ao resultado atual?

Inicialmente lembrei apenas de cadastrar inventories quando efetuava uma compra

Apenas inclui no início

use App\Models\Inventory;

No store()

Como o modelo que eu estava usando de controller vindo do gerador de CRUDs já fazia

Buy::create($requestData);

Apenas adicionei:
Inventory::create($requestData);

Beleza, quando adicionava a primeira compra ele também adicionava os mesmos dados no inventories.

Mas e na próxima compra?

Bem, eu não havia pensado nisso.

As primeiras tentativas de fazer como fiz no Seller não funcionaram, pois quanto ia cadastrar o Seller/Venda já havia um registro em inventories, vindo da Compra. Mas como eu poderia cadastrar o primeiro registro de inventories quando fosse cadastrar comrpas, se inventories não tinha nenhum registro.

Depois de várias tentativas e de consultar a documentação do Eloquent e do QueryBuilder acabei chegando a esta solução:

- Primeiro, quando efetuar a compra, preciso usar o QueryBuilder paraa testar se inventories não tinha registro, caso não tivesse eu cadastrava o registro atual vindo do form create de Compras.

Com inventories já tendo um registro eu consegui fazer parecido com o que fiz em Sales.
Assim cheguei a esta solução.
Deu um certo trabalho, mas isso é a falta de prática, pois realmente o Laravel facilita muito as coisas.
As duas ferramentas que utilizei foram o Eloquent e o QueryBuilder.

https://laravel.com/docs/11.x/eloquent
https://laravel.com/docs/11.x/queries

Depois de boa pesquisa e algumas experiências elaborei os tutoriais que usei aqui abaixo nos itens 3.2 e 3.3

https://github.com/ribafs2/laravel-projetos

https://github.com/ribafs2/laravel-projetos/blob/main/LaravelProjetos.pdf


