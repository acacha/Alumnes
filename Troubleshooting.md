# Abans que res

Llegiu fitxer InstalacióSite.md i recordeu de fer tots els passos:

```
composer install
yarn
cp .env.example .env
php artisan key:generate
```

sinó normal que no funcioni. I NO OBLIDEU ADAPTAR FITXER .env!!!!!!

# Projectes que utilitzen altres projectes amb studio

Al instal·lar un projecte en explotació heu de reproduir el mateix que teniu el local.

Al executar composer podeu tenir errors com:

```
$ composer install
...
  [RuntimeException]                                              
  Source path "../events" is not found for package acacha/events
```

Recordeu el fitxer studio.json:

```
$ cat studio.json 
{
    "version": 2,
    "paths": [
        "../events"
    ]
}
```

On teniu les dependències del vostre projecte. Jo en el meu cas això passa a un projecte test:

```
/home/forge/events.sergitur.2dam.iesebre.com
```

Per tant he d'anar a carpeta pare (..):

```
/home/forge
```

i instal·lar events:

```
git clone https://github.com/acacha/events
```

#  It is unsafe to run Dusk in production.
  
Afegiu el paquet Laravel Dusk com un paquet que no s'ha d'autodescobrir a composer.json:

```
"extra": {
        "laravel": {
            "dont-discover": [
                "laravel/dusk"
            ]
        }
    },
```

# Problemes de permisos amb Git

Executeu:

```
git config --global user.name "Example Surname"
git config --global user.email "your.email@gmail.com"
```

# Error 500

Consulteu els fitxer de log:

```
cd VOSTRE_PROJECTE
tail -f storage/logs/laravel.log
```

i també podeu mirar:

```
tail -f /var/log/nginx/NOM_DEL_VOSTRE_DOMINI.com-error.log error
```

És molt possible error sigui:

```
production.ERROR: No application encryption key has been specified
```

Us heu deixat executar:

```
php artisan key:generate
```

Després de:

```
cp .env.example .env

Exemple:
```
tail -f /var/log/nginx/events.sergitur.2dam.iesebre.com-error.log error
```

Aquest fitxer de log l'heu posat valtros a la configuració del site (exemple):

```
cat /etc/nginx/sites-available/events.sergitur.2dam.iesebre.com
...
    error_log  /var/log/nginx/events.sergitur.2dam.iesebre.com-error.log error;
...
```
