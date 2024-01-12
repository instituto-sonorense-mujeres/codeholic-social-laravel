# agregando path de php en ./vendor/bin/sail para php en vscode
```json
{
    "php.validate.executablePath": "D:/Ubuntu/home/razzor/www/laravel/laravel-social-media/vendor/bin/sail",
}

```

```bash
# commands:

sudo touch /usr/local/bin/php

sudo chmod +x /usr/local/bin/php

# content:

path=$(printf '%s\n' "${PWD##*/}")
command="docker exec laravel.test-1 php "$@""
echo "Running php on docker laravel.test-1"
$command
```