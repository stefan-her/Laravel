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

## Artisan Make: Controller

```
php artisan make:controller CityController
```

Si besoin des recourses 

```
php artisan make:controller CityController -r
```
--------------------------------------------------------------------------

# Route

Creation des routes en une seul fois lié à un controller 

- index
- create
- store
- show
- edit
- update
- destroy

```
Route::resource('routeName', NameController::class);
```

Pour exclute des méthodes

```
Route::resource('routeName', NameController::class)->except(["show"]);
```

--------------------------------------------------------------------------

### Creation en une commande de migration & controller avec resouces

```
php artisan make:controller CityController -mcr
```

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

#### Creation de la Base de Données

S'il faut la recréer suite à un changement dans une des fichier migration

```
php artisan migrate:fresh
```
Sinon 
```
php artisan migrate  
```
### Pour remplire la DB avec des fausses données

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



