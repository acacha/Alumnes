
## Config SSH

Editeu el fitxer ***~/.ssh/config*** i afegiu:

```
Host nomhostdesitgeu
  Hostname IP_SERVIDOR
  User forge
  IdentityFile /home/VOSTRE_USERNAME/.ssh/id_rsa
  Port 22
```

Exemple:

```
Host sergibaucells
  Hostname 188.226.141.249
  User forge
  IdentityFile /home/sergi/.ssh/id_rsa
  Port 22
```

Per accedir al servidor ara només cal escriure:

```
ssh sergibaucells
```
