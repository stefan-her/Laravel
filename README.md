# Laravel
Cours Larvavel 10


## Install debug
```
composer require barryvdh/laravel-debugbar --dev
```

--------------------------------------------------------------------------

## Artisan Make: Model

```
php artisan make:model modalName
```
--------------------------------------------------------------------------

## Artisan Make: pour DB

### creation d'un fichier migration pour créer une table dans le base de données
```
php artisan make:migration dbtable
```
SoftDelete -> supperion d'un élément via l'ajout une date et donc reversible
dans le fichier migration créé:  

```
public function up(): void
    {
        Schema::create('DBtable', function (Blueprint $table) {
          ....
          $table->softDeletes();
```

### Pour remplire la DB avec des fauses données

#### creation de factory
```
php artisan make:factory DBTableFactories
```

#### creation du seeder basé sur son Model
```
php artisan make:seeder DBtableSeeder 
```

#### Pour remplir la DB
```
php artisan db:seed
```
ou si besoin juste de remplir une table en utilisant son model
```
php artisan db:seed --class=DBtableSeeder
```
--------------------------------------------------------------------------

## contrôle que le formulaire n'est pas remplit par un robot
```
composer require spatie/laravel-honeypot
php artisan vendor:publish --provider="Spatie\Honeypot\HoneypotServiceProvider"
```

dans le recources/views/formulaire.blade.php
```
<x-honeypot />
```

dans le fichier app/Http/Kernel.php
```
  proteced $middelware {
      ...
      \Spatie\Honeypot\ProtectAgainSpam::class
  }
```



