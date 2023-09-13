# Laravel

* php artisan serve --host=192.168.3.6 --port=8001

## Composer
` composer install `<br>
` composer update `<br>
` composer status -v `<br>
` cp .env.example .env `<br>
` php artisan key:generate`<br>

> Obs foi necessário alterar o "C:\php82\php.ini"
> habilitando extension=gd removendo o ;

* php artisan --version (versão do laravel)
## Criando projeto
`composer create-project --prefer-dist laravel/laravel evolucao "9.*" `

Com detalhes <br>
`php composer.phar show laravel/framework `<br>
ou<br>
`composer show laravel/framework `

## Criando migrations

` php artisan make:migration create_users ` <br>
` php artisan make:migration alter_users ` <br>
` php artisan make:migration alter_users_table --create=usuarios `

## Config database

* .env

## Rodar migration

` php artisan migrate `
` php artisan migrate:status `

## Desfazer migration

` php artisan migrate:rollback `
` php artisan migrate:rollback --step=1 `

## Apagar e refazer migration

` php artisan migrate:fresh `

## Storage link

` ll public - mostra se já existe o link`

` php artisan storage:link `

## Mostar comandos

` php artisan list `
