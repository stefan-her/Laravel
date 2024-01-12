# Laravel
Cours Larvavel 10


## Install debug
```
composer require barryvdh/laravel-debugbar --dev
```


## Artisan Make:

### creation d'un fichier migration pour créer une table dans le base de données
```
php artisan make:migration dbtable
```




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



