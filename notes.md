## llum boot

Millorar per tal que funcioni en apps Laravel baixades de Github amb git clone: fitxer .env, php atisan generate:key, etc

https://blog.lanin.me/add-handy-setup-wizard-to-your-laravel-project/

## llum deploy

Fer una comanda per automatitzar el deployment d'una aplicació que estem desenvolupant

CONFIGURACIÓ PER SITE:
- Fitxer .env.production (afegir a .gitginore)
-

Tasques que realitza un deploy
- Primer assegurar-se que té totes les dades necessàries:
  - Configuració global: dades accés servidor SSH. NO es tenen? proposar l'execució de llum deploy:init
  - Configuració site:
    - Hi ha fitxer .env.production? 
    - APP_URL del fitxer 

## llum deploy:init

CONFIGURACIÓ GLOBAL

Permet guardar dades personals referents al deployment al fitxer: ~/.llumrc 

- Dades accés SSH: només preguntar pel nom de la config afegida a .ssh/config i no cal preguntar:
  - IP del servidor en explotació
  - Nom de l'usuari
  - Port?
  - Si preguntem totes aquestes dades que sigui potser per afegir a partir d'una plantilla crear aquesta entrada
    - llum deploy:config_ssh?
    