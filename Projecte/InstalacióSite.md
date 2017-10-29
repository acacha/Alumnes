## Passos a seguir

```
cd /home/forge
git clone GITHUB_URL_PROJECTE_PHP_O_LARAVEL_OCO_TEST! nomdeldomini.com
```

Instal·leu altres dependències locals si el paquet utilitza ***Studio***

```
git clone GITHUB_URL_PROJECTE_PAQUET!
```

Noteu que el site Laravel (projecte TEST) té un nom de carpeta igual al nom del domini en explotació però el paquet no.

Aneu al projecte i execute composer i npm:

```
cd nom_del_domini
composer install
npm install
```

Llegiu:

 https://laravel.com/docs/5.5/installation#server-requirements
 
Els server requirements ja es compleixen gràcies a que és un server creat amb Forge. Però cal tenir en compte:

Configuració entorn

```
cp .env.example .env
```

Modifiqueu els valors:
- APP_ENV = production
- APP_DEBUG = false
- Configureu la base de dades mysql o sqlite i creu la base de dades sqlite o Mysql (el que pertoqui)
- Configureu altres serveis com EMAIL, CACHE, SESSIó o el que convingui/utilitzi el projecte

Altres no tant importants però que potser voleu canviar:
- APP_NAME

Penseu en posar també els valors que no siguin secrets a .env.example o .env.example.production

Us cal base de dades sqlite:

```
touch database/database.sqlite
```

Executeu les migracions i els seeds:

```
php artisan migrate:fresh --seed
```

Creu clau de seguretat:

```
php artisan key:generate
```

Executeu els test per comprovar tot està ok.

Consulteu el fitxer Troubleshooting si teniu problemes.

Exemple:

```
cd /home/forge
git clone https://github.com/acacha/events_test events.sergitur.2dam.iesebre.com
git clone https://github.com/acacha/events
cd events.sergitur.2dam.iesebre.com
composer install
yarn
cp .env.example .env
php artisan key:generate
touch database/database.sqlite
php artisan migrate:fresh --seed
phpunit
```

## Configuració Nginx:

Consulteu el fitxer nginx.md