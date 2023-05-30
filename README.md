# ORMA

 - puoi creare tabelle
 - aggiungere colonne
 - puoi farlo tanto con sqlite quanto con postgresql

## Installazione

 > composer require sensorario/orma

Puo copiare `vendor/sensorario/orma/public/index.php` nella root del progetto ed eseguire l'esempio.

## Utilzzo

```php
$orma = new Orma($pdo, match($driver) {
    'sqlite' => new SQLiteDriver,
    'postgresql' => new PostgreSQLDriver,
});

$orma($table)->createTable();
$orma->addColumn($column);
```

## PDO

I dati PostgreSQL fanno riferimento alla docker presente nel progetto.

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
];

$pdo = new PDO(
    $config[$config['db']]['dns'],
    $config[$config['db']]['username'],
    $config[$config['db']]['password'],
);
```
