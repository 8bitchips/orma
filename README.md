# ORMA

 - you can create tables
 - add columns
 - insert data
 - CR of CRUD operations
 - designed for sqlite or postgresql

## install

```
composer require sensorario/orma
```

Copy `vendor/sensorario/orma/public/index.php` on your project root.
SQLite does not require any installation. Postgres can be used with docker: `vendor/sensorario/orma/docker-compose.yaml`.

Happy coding

## pdo

Postgres data refers to docker machine inside the project.

```php
$config = [
    'postgresql' => [
        'dns' => 'pgsql:host=database;dbname=your_database_name',
        'username' => 'your_username',
        'password' => 'your_password',
    ],
    'sqlite' => [
        'dns' => 'sqlite:./erdatabase',
    ],
    'db' => 'postgresql',
    'db' => 'sqlite',
];

$pdo = new PDO(
    $config[$config['db']]['dns'],
    $config[$config['db']]['username'],
    $config[$config['db']]['password'],
);
```

## init

```php
$orma = new Orma($pdo, match($driver) {
    'sqlite' => new SQLiteDriver,
    'postgresql' => new PostgreSQLDriver,
});
```

## create a table

```php
$orma($table)->createTable();
```

## add a column

```php
$orma->addColumn($column);
```
## insert

```php
$orma('table_name')->insert([
    'id' => 42,
]);
```

PS. This repo is made just to play.