## Proyect Codeholic

# PART-1

```bash
curl -s https://laravel.build/laravel-social-media | bash

./vendor/bin/sail up -d

./vendor/bin/sail bash

./vendor/bin/sail stop

composer require laravel/breeze --dev

php artisan breeze:install

php artisan migrate
npm install
npm run dev

git config --global user.name "ti-ism"
git config --global user.email "institutosonorensemujerti@gmail.com"

ssh-keygen -o -t rsa -C "institutosonorensemujerti@gmail.com"

git push -u origin master

```


# PART-2

```bash
php artisan make:model Post -m
php artisan make:model PostAttachment -m
php artisan make:model PostReaction -m
php artisan make:model Comment -m
php artisan make:model Group -m
php artisan make:model GroupUser -m
php artisan make:model Follower -m

php artisan make:migration add_columns_to_users_table

php artisan migrate
```

# PART-3

```bash


```