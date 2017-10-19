
## Exemple site configurat per Forge:

Exemple:
- Nom del domini : provaforge.acacha.org
- El fitxer de configuració l'anomenarem igual al nom de domini i el posarem a /etc/nginx/sites-available
- Els vostres sites van a la carpeta /home/forge i el nom de la carpeta igual al nom del domini. Exemple /home/forge/provaforge.acacha.org

El site es troba a:

```
/home/forge/provaforge.acacha.org
```

Config Nginx
 
```
 $ cat /etc/nginx/sites-available/provaforge.acacha.org 

 server {
     listen 80;
     listen [::]:80;
     server_name provaforge.acacha.org;
     root /home/forge/provaforge.acacha.org/public;
 
     # FORGE SSL (DO NOT REMOVE!)
     # ssl_certificate;
     # ssl_certificate_key;
 
     ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
     ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA:!3DES';
     ssl_prefer_server_ciphers on;
     ssl_dhparam /etc/nginx/dhparams.pem;
 
     add_header X-Frame-Options "SAMEORIGIN";
     add_header X-XSS-Protection "1; mode=block";
     add_header X-Content-Type-Options "nosniff";
 
     index index.html index.htm index.php;
 
     charset utf-8;
 
     location / {
         try_files $uri $uri/ /index.php?$query_string;
     }
 
     location = /favicon.ico { access_log off; log_not_found off; }
     location = /robots.txt  { access_log off; log_not_found off; }
 
     access_log off;
     error_log  /var/log/nginx/provaforge.acacha.org-error.log error;
 
     error_page 404 /index.php;
 
     location ~ \.php$ {
         fastcgi_split_path_info ^(.+\.php)(/.+)$;
         fastcgi_pass unix:/var/run/php/php7.1-fpm.sock;
         fastcgi_index index.php;
         include fastcgi_params;
     }
 
     location ~ /\.(?!well-known).* {
         deny all;
     }
 }
 
```

Aquest fitxer és un exemple/plantilla. El podeu utilitzar tal qual només cal canviar:

- Nom del fitxer: nom del vostre domini
- Buscar i remplaçar tots els provaforge.acacha.org per nom complet del vostre domini
 
Un cop teniu el fitxer feu un link de sites-enabled a sites-available:

 $ sudo ln -s /etc/nginx/sites-available/NOM_DEL_DOMINI /etc/nginx/sites-enabled/


Exemple:

```
 $ sudo ln -s /etc/nginx/sites-available/provaforge.acacha.org /etc/nginx/sites-enabled/
```
 
Apliqueu els canvis a Nginx:

```
$ sudo service nginx reload
```

A la carpeta /home/forge i sent l'usuari forge

```
cd /home/forge
git clone URL_DEL_REPOSITORI_PROJECTE_LARAVEL_O_PHP NOM_DEL_DOMINI
cd NOM_DEL_DOMINI
composer install
```