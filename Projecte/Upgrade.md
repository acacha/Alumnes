## Passos per configurar servidor

Un cop entreu al servidor:

El primer que us pot interessar es canviar-vos la paraula de pas:

```
passwd
```

La password actual està al correu que us he enviat.

És important també que executeu el següent script per tal de deixar l'accés per al professor:

```
sudo adduser sergi
sudo usermod -a -G forge,sudo,www-data sergi
sudo cp -r ~/.ssh/ /home/sergi/
sudo chown -R sergi:sergi /home/sergi/.ssh
```

Podeu deixar com a paraula de pas inicial per al meu usuari la que teniu al email. Busqueu-me algun moment a classe per tal 
que em pugui canviar la paraula de pas al servidor

Instal·leu els locales en català:

```
$ sudo apt-get install language-pack-ca && sudo locale-gen ca_ES.UTF-8
```

Actualitzeu el servidor:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

També és interessant un paquet com molly-guard per evitar apagades involuntaries del servidor:

```
sudo apt-get install molly-guard
```

Canvieu la configuració de git:

```
git config --global user.name "Example Surname"
git config --global user.email "your.email@gmail.com"
```

I pugeu la clau SSH del servidor forge al vostre usuari de git.

La clau pública la trobareu al servidor:

./ssh/id_rsa.pub

Seguiu un altre cop els passos de:

https://help.github.com/articles/connecting-to-github-with-ssh/