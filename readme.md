# Git Tecaj 2023/24
## Setup

#### config
Git config se uporablja za ogled in spreminjanje git nastavitev
```
# prikaz trenutno nastavljenih nastavitev
git config user.name 
git config user.email

# spreminjanje nastavitev
git config --global user.name "Username"
git config --global user.email "user@example.com"

# --global parameter lahko zamenjamo z --local
# ta nastavitev veljala samo za repozitorij ki je trenutno v rabi
git config --local user.name "Username samo za ta repo"
git config --local user.email "user_samo_za_ta_repo@example.com"
```

#### init
Git init inicializira nov repo.
```
# inicializiramo repozitorij v trenutni mapi
git init

# inicializiramo repozitorij v specificirani mapi
git init <directory>
```

## Osnove

#### remote 
Git remote omogoca nadzor povezav repozitorija na remote repozitorij
(eden izmed teh je origin remote).
```
# osnoven prikaz imen remotov
git remote

# prikaz URLjev in imen remotov (-v / --verbose) 
git remote -v

# dodaj remote
git remote add <name> <url>

# odstrani remote
git remote rm <name>

# preimenuj remote
git remote rename <old-name> <new-name>
```

#### add
Git add doda specificirane datoteke med datoteke, ki jim git sledi.
```
# dodajanje datoteke
git add <file>

# dodajanje mape
git add <directory>

# dodaj vse v trenutni mapi
git add .

# dodaj vse datoteke lokalnega repozitorija (-A / -all)
git add -A
```

#### commit
Git commit shrani trenutno slejene spremembe v kot tocko v repozitoriju.
```
# ustvari commit
git commit

# ustvari commit in mu dodaj sporocilo
git commit -m "opis sprememb"

# ustvari commit in hkrati dodaj spremembe (git add)
git commit -a

# namesto da je ustvarjen nov commit, spreminjamo prejsnji commit
git commit --amend
```

#### push
Git push spremembe lokalnega repozitorija prenese na remote repozitorij.
```
# izvedi push na specificiran remote
git push <remote>

# izvedi git push na specificnem branchu
git push <remote> <branch>

# prisili push na remote repozitorij (-f / --force)
git push <remote> -f
```

#### fetch 
Git fetch prenese spremembe iz remote repozitorija, brez da jih uveljavi.
```
# prenesi vse spremembe remote repozitorija (posodibi vse branche)
git fetch <remote>

# prenesi samo spremembe specificnega brancha
git fetch <remote> <branch>
```

#### pull
Git pull je kombinacija ukazov fetch in merge.
Najprej se izvrsi ukaz git fetch, ki prenese vsebino remote repozitorija, 
nato pa je ta zdruzena z nasim lokalnim repozitorijem.

```
git pull <remote>
```

#### clone
Git clone prenese zeljen repozitorij.
```
# prenesi repo v mapo poimenovano po repozitoriju
git clone <repo>

# prenesi repo v specificirano mapo
git clone <repo> <directory>
```

## Log in ogled sprememb

#### log 
```

```

#### status
```

```

#### diff
```

```

## Branches

#### branch
```

```

#### checkout
```

```

#### merge
```

```

## Ostalo

#### reset
```

```

#### stash 
```

```

#### cherry-pick
```

```

#### rebase
```

```

## Markdown
[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)
