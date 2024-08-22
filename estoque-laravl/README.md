Como executar

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

