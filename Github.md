Totes les pases s'executen al servidor

## Configuració

Canvieu el fitxer .gitconfig (poseu les vostres dades)

```
$ cat .gitconfig 
[user]
	name = eric98
	email = ergare.17@gmail.com
```

#Clau SSH

Poseu:

```
ssh-keygen -t rsa -b 4096 -C "emailvostrequeutilitzeualgithub@example.com"
```

Al assistent per crear la nova clau NO US CARREGUEU LA CLAU EXISTENT escolliu un nou nom id_rsa_github

```
Enter a file in which to save the key (/home/you/.ssh/id_rsa): /home/you/.ssh/id_rsa_github
```

NO POSEU CAP PARAULA DE PAS

Afegiu la clau al vostre usuari de Github:

- https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/

Configureu SSH per utilitzar aquesta clau amb el domini github.com (domini per defecte que es posa al fer un clone de repositoris)

```
$ editor ~/.ssh/config 
host github.com
  HostName github.com
  IdentityFile ~/.ssh/id_rsa_github
  User git
```

Recursos
- https://help.github.com/articles/connecting-to-github-with-ssh/
