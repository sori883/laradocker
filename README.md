### app container

- Base image
  - [php](https://hub.docker.com/_/php):7.4-fpm-buster
  - [composer](https://hub.docker.com/_/composer):2.0
  - xDebug:3

### web container

- Base image
  - [nginx](https://hub.docker.com/_/nginx):1.18-alpine
  - [node](https://hub.docker.com/_/node):14.2-alpine

### db container

- Base image
  - [postgresql](https://hub.docker.com/_/postgres):12

### mail container

- Base image
  - [mailhog](https://hub.docker.com/r/mailhog/mailhog/)

### ボリュームマウント
- laravel
  - laravelのコード
- db-store
  - DBのデータ(named volume)


### デバッグ
#### laravelのコードマウントを変更した場合はlaunch.jsonを編集する必要があります。
```launch.json
"pathMappings": {
  "/work/backend": "YourLaravelDir"
},
```

#### PHPUnitでCoverageを使う
PHPUnitでCoverageを使う場合は、Composer.jsonでPHPUnit実行時だけ、xdebug.modeを`debug`から`coverage`に変更する必要があります。  
```composer.json
"scripts": {
    "test:coverage": [
        "export XDEBUG_MODE=coverage && phpunit --coverage-html coverage"
    ]
}
```