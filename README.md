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


# HOME-PC-REQUIREMENTS

```bash

# se tiene qeu apagar mysql en ubuntu y windows primero
sudo service mysql stop
sudo systemctl stop mysql

#comprobar que este apagado con:


# destruir y re instalar contenedores
docker-compose down --volumes
./vendor/bin/sail build --no-cache
./vendor/bin/sail up --build -d

# iniciar laravel en puerto '89'
sudo APP_PORT=89 ./vendor/bin/sail up -d

# entrar a shell como root
./vendor/bin/sail root-shell

# elininar directorio node_moudles recursivamente
rm -rf node_modules

# cambiar permisos linux
chmod -R 777 /var/www/html/
chown -R 777 www-data:www-data *

# mysql container debug
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' 1c8a0e4dc5d6

# cambiar 'DB_HOST' en archivo .env por la ip retornada o nombre del contenedor, ejemplo:
DB_HOST=codeholic-social-laravel-mysql-1

```


# PART-3

```bash

composer require spatie/laravel-sluggable

```