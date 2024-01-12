# Laravel
Cours Larvavel 10


## Install debug
```
composer require barryvdh/laravel-debugbar --dev
```

## contrôle que le formulaire n'est pas remplit par un robot
```
composer require spatie/laravel-honeypot
php artisan vendor:publish --provider="Spatie\Honeypot\HoneypotServiceProvider"
```

dans le formulaire 
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

