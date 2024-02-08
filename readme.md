# Git Tecaj 2023/24
## Setup

### config
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

# za spreminjanje nastavitev lokalnega repozitorija lahko uporabimo tudi
git config user.name "Username samo za ta repo"
git config user.email "user_samo_za_ta_repo@example.com"
```

### init
Git init inicializira nov repo.
```
# inicializiramo repozitorij v trenutni mapi
git init

# inicializiramo repozitorij v specificirani mapi
git init <directory>
```

## Osnove

### remote 
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

### add
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

### commit
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

### push
Git push spremembe lokalnega repozitorija prenese na remote repozitorij.
```
# izvedi push na specificiran remote
git push <remote>

# izvedi git push na specificnem branchu
git push <remote> <branch>

# prisili push na remote repozitorij (-f / --force)
git push <remote> -f
```

### fetch 
Git fetch prenese spremembe iz remote repozitorija, brez da jih uveljavi.
```
# prenesi vse spremembe remote repozitorija (posodibi vse branche)
git fetch <remote>

# prenesi samo spremembe specificnega brancha
git fetch <remote> <branch>
```

### pull
Git pull je kombinacija ukazov fetch in merge.
![](https://wac-cdn.atlassian.com/dam/jcr:63e58c34-b273-4e48-a6b1-6e3ba4d4a0ea/01%20bubble%20diagram-01.svg?cdnVersion=1427)
Najprej se izvrsi ukaz git fetch, ki prenese vsebino remote repozitorija.
![](https://wac-cdn.atlassian.com/dam/jcr:0269bb2d-eb7f-43d8-80a2-8afa88d11eea/02%20bubble%20diagram-02.svg?cdnVersion=1427)
Nato se izvede git merge med prenesenim origin branchom in lokalnim branchom.

```
git pull <remote>
```

### clone
Git clone prenese zeljen repozitorij.
```
# prenesi repo v mapo poimenovano po repozitoriju
git clone <repo>

# prenesi repo v specificirano mapo
git clone <repo> <directory>
```

## Log in ogled sprememb

### log 
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
### status
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

### diff
Git diff prikaze razlike med izbranima viroma (commiti, datoteke, branchi...)
```
git diff <source1> <source2>
```

## Branches
![](https://wac-cdn.atlassian.com/dam/jcr:a905ddfd-973a-452a-a4ae-f1dd65430027/01%20Git%20branch.svg?cdnVersion=1431)
Git brachi so med seboj neodvisna okolja. 
Ti so lahko namenjeni razvoju novih funkcijonalnosti, bug fixom... (vec o tem pod [git workflow](##Workflow)).

### branch
Git bracnh je namenjen upravljanju branchev
```
# izspis branchev
git branch

# ustvari nov branch
git branch <branch>

# ustvari in se prestavi nanj
git branch -d <branch>

# preimenuj branch
git branch -m <branch>

# izbrisi branch
git branch -D <branch>
```

### checkout
Git checkout nam omogoca premikanje med branchi in commiti
```
# premakni se na branch
git checkout <branch>

# ustvari in se premakni se na nov branch
git checkout -b <branchname>

# podobno velja za remote branche
git fetch --all
git checkout ＜remotebranch＞
git checkout -b ＜remotebranch＞ origin/＜remotebranch＞

# premakni se na commit
git checkout <commit>
```

### merge
Git merge omogoca zdruzitev branchov v enega.
![](https://wac-cdn.atlassian.com/dam/jcr:7afd8460-b7bf-4c42-b997-4f5cf24f21e8/01%20Branch-2%20kopiera.png?cdnVersion=1431)

Najprej imamo main branch in feature branch. Ker zelimo feature branch integrirati v main branch bomo uporabili merge ukaz.
![](https://wac-cdn.atlassian.com/dam/jcr:c6db91c1-1343-4d45-8c93-bdba910b9506/02%20Branch-1%20kopiera.png?cdnVersion=1431)
Stanje branchov po izvedenem mergu.

Preden se izvaja merge poskrbi da so:
- **z git checkoutom se prestavi na prejemajoci branch!**
- branchi up to date (**git fetch** in **git pull**)

```
# zdruzi branch v branch na katerem se trenutno nahajas
git merge <branchname>
```

#### Konflikti pri mergu
Do konfliktov pri mergu pride zaradi razlik na istih mestih v istih datotekah. 
Git nas bo o teh obvestiv in hkrati tudi to oznacil.
```
here is some content not affected by the conflict
<<<<<<< main
this is conflicted text from main
=======
this is conflicted text from feature branch
>>>>>>> feature branch;
```
[**Odpravljanje konfliktov**](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts)

## Ostalo

### reset
Git reset se uporablja podobno kot git commit. Razlikujeta se po tem da git reset premakne HEAD brancha na izbran commit.
```
git reset <commit>

# --hard
# Odstrani dodane spremembe, totalen reset na izbran commit
git reset --hard <commit>

# --mixed (je default opcija)
# Dodane spremembe odindexira (oz. ponovno je potrebno izvesti git add)
git reset --mixed <commit>

# --soft
# Ne odstrani sprememb in premakne HEAD
git reset --soft <commit>
```
#### reset vs checkout
|**Ukaz**       |**Obmocje**    |**Raba**                                           |
|---------------|---------------|---------------------------------------------------|
|git reset      |Commit-level   |Odstrani necommitane spremembe ali commite         |
|git reset      |File-level     |Unstaganje datoteke                                |
|git checkout   |Commit-level   |Premikanje med branchi ali ogled starih commitov   |
|git checkout   |File-level     |Odstrani trenutne spremembe                        |
#### git checkout b
![](https://wac-cdn.atlassian.com/dam/jcr:f45c4a34-8968-4c81-83cf-d55ebf01a447/02%20git-checkout-transparent%20kopiera.png?cdnVersion=1431)
#### git reset b
![](https://wac-cdn.atlassian.com/dam/jcr:bdf5fda3-4aac-4170-ba35-58f7a66ea3c4/03%20git-reset-transparent%20kopiera.png?cdnVersion=1431)
### stash 
Git stash omogoca shranitev brez commita za kasnejso rabo.
```
# naredi stash pod WIP imenom
git stash

# naredi stash pod specificnim imenom
git stash save "Ime stasha"

# delen stash
git stash -p

# naredi stash brancha
git stash branch ime-brancha stash@{0}

# izpis stashov in njihovih
git stash list

#primer izpisa
stash@{0}: WIP on submit: 6ebd0e2... Update git-stash documentation
stash@{1}: On master: 9cc0589... Add git-stash


# izpis sprememb v stashu
git stash show

# podroben izpis sprememb v stashu
git stash show -p

# odstrani stash in povrni spremembe
git stash pop stash@{0}

# ne odstrani stash in povrni spremembe
git stash apply stash@{0}

# odstrani stash in ne povrni spremembe
git stash drop stash@{0}

# odstrani vse stashe
git stash clear
```

### cherry-pick
Git cherry-pick omogoca izbiro specificnega commita in dodajo tega v trenuten HEAD.
```
git cherry-pick <commit>

# spremeni commit message (-edit)
git cherry-pick -edit <commit>

# ne ustvari novega commita (--no-commit)
git cherry-pick --no-commit <commit>
```

### rebase
Git rebase omogoca spreminjanje git zgodovine in stiskanje/squash commitov. 

**TEGA NE POCNI NA MAIN/MASTER BRANCHU!**
```
# interaktiven rebase (--interactive / -i)
git rebase -i <base> (npr. HEAD~3 za rebase zadnjih treh commitov)

# izpis
    pick 2231360 some old commit
    pick ee2adc2 Adds new feature


    # Rebase 2cf755d..ee2adc2 onto 2cf755d (9 commands)
    #
    # Commands:
    # p, pick = use commit
    # r, reword = use commit, but edit the commit message
    # e, edit = use commit, but stop for amending
    # s, squash = use commit, but meld into previous commit
    # f, fixup = like "squash", but discard this commit's log message
    # x, exec = run command (the rest of the line) using shell
    # d, drop = remove commit

```
[Vec o git rebasu](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)

## Markdown
[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)

## Workflow
![Workflow](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=1427)
