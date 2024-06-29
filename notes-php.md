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
```
composer create-project --prefer-dist laravel/laravel nome-do-projeto "versão-do-laravel"
```
## Criando projeto em uma pasta existente
`composer create-project laravel/laravel . `

Com detalhes <br>
`php composer.phar show laravel/framework `<br>
ou<br>
`composer show laravel/framework `

## Criando migrations

` php artisan make:migration create_users ` <br>
` php artisan make:migration alter_users ` <br>
` php artisan make:migration alter_users_table --create=usuarios `

## Criando model com migration
### m: migration c: controller r: request

` php artisan make:model Category -m` <br>
` php artisan make:model Category -mcr`

## Config database

* .env

## Rodar projeto especificando porta e IP
` php artisan serve --host=0.0.0.0 --port=0000 `

## Rodar migration

` php artisan migrate ` <br>
` php artisan migrate:status `

## Desfazer migration

` php artisan migrate:rollback ` <br>
` php artisan migrate:rollback --step=1 `

## Apagar e refazer migration

` php artisan migrate:fresh ` <br>
` php artisan migrate:reset `

## Storage link

` ll public - mostra se já existe o link`

` php artisan storage:link `

## Mostar comandos

` php artisan list `

## Criar component inline

` php artisan make:component PageLayout --inline `

## Seed tabelas migration

` php artisan db:seed ` <br>
` php artisan db:seed --class=CategoryTableSeeder `

## Laravel.log

` tail -f storage/logs/laravel.log `

# Livewire

## Publishing The Config File
` php artisan livewire:publish --config `
> 'layout' => 'layouts.app',


 
