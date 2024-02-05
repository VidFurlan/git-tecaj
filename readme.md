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
![Remotes](https://wac-cdn.atlassian.com/dam/jcr:df13d351-6189-4f0b-94f0-21d3fcd66038/01.svg?cdnVersion=1427)
Remota na sliki bi bili v primeru na sliki Centralni in Johnov repozitorij.
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
![](https://wac-cdn.atlassian.com/dam/jcr:63e58c34-b273-4e48-a6b1-6e3ba4d4a0ea/01%20bubble%20diagram-01.svg?cdnVersion=1427)
Najprej se izvrsi ukaz git fetch, ki prenese vsebino remote repozitorija.
![](https://wac-cdn.atlassian.com/dam/jcr:0269bb2d-eb7f-43d8-80a2-8afa88d11eea/02%20bubble%20diagram-02.svg?cdnVersion=1427)
Nato se izvede git merge med prenesenim origin branchom in lokalnim branchom.

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
Git log je namenjen izpisu preteklih commitov.
```
# osnoven ispis
git log

#   commit bcf254309eddf4c1e9fa775a9dce01a0669a635e (HEAD -> main, origin/main)
#   Author: Vid Furlan <vidfurlan@example.com>
#   Date:   Mon Feb 5 18:43:10 2024 +0100
#
#       Commit message

# natancen prikaz sprememb (-p)
git log -p
```
#### status
Git status izpise trenutno stanje datotek, kar se tice git sledenja
```
git status

#   On branch main
#   Your branch is up to date with 'origin/main'.
#
#   Changes to be committed:
#   (use "git restore --staged <file>..." to unstage)
#        new file:   dodano
#
#   Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git restore <file>..." to discard changes in working directory)
#       modified:   readme.md
#
#   Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#       nesledeno
```

#### diff
Git diff prikaze razlike med izbranima viroma (commiti, datoteke, branchi...)
```
git diff <source1> <source2>
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

## Workflow
![Workflow](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=1427)
