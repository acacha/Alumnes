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

