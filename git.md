# Git - easy to nightmare lvl - Szasz Zoltan
https://devopsoktatas.hu

# SCM in general
## Source Code Management
regen: ftp-n keresztul kreativ nevezektan (*-final-release-beta-2....)<br>
mit adnak a verzio kezelok?
  - ha hibaztunk, konnyu visszavonhatosag
  - nem veszik el a forraskod, backup (nem csak nalunk van meg, hanem egy tavoli repoban is)
  - tobb verziot tudunk fenntartani (pl bugjavitas es feature fejlesztes)
  - csapatban munkat megkonnyiti (lehetove teszi)
  - nyomonkovetheto, hogy ki mit csinalt es mikor
mit tartsunk repoban?
  - tesztek
  - configok
  - build kornyezet
  - kulso library-k listaja
  - asset-eket

# Git
10 eve irta meg Linus Torvalds, Linux kernel tarolasara jott letre.<br>
Elosztott verzio-kezelo rendszer
  - nalunk is verzio kezelt a kod (megvan a history)
  - Working copy - ezen dolgozunk
  - Local index
  - Remote-ok
  - a kod egy bizonyos allapota mindenkinel meglesz

Branch-ek - elagazasok adott kod allapotbol, pl uj feature-ok, vagy bug-fix-ek<br>
Az egyes branchek egyes allapotai tag-elhetok (kiemelt, konnyen celozhato commit-ok)<br>
elosegiti a review-t<br>
conflict feloldasok<br>
atirhato a tortenelem<br>

# Git commands

## Basics
### init
repo inditasa
### status
repo valtozasai a legutolso commit ota
### add
file-ok hozzaadasa a `tracked files`-hoz<br>
* vagy . hasznalatval minden file / folder-t hozza tudok addni a repohoz, ami meg nincs hozzaadva
### commit
hozzaadas a `Local Index`-hez, innentol kezdve koveti a verzio kezelo<br>
minden `commit` kap egy sajat hash-et, amivel lehet ra hivatkozni a kesobbiekben. Ez mindig egyedi, es tobbnyire nem valtozik<br>
`--amend`: nem egy ujabb keszul, hanem hozzaadja az elozo `commit`-hoz, a message szerkesztesenek a lehetosegevel
### log
visszanezni az aktualis `history`-t
### rm
file / folder eltavolitasa a `working copy`-bol (rm es git add parancs osszevonva)
### mv
file / folder mozgatasa, elokeszitve `commit`-ra (mv es git add parancs osszevonva)

## Stash
Kituntetett `branch`, ide lehet bepakolni olyan modositasokat, amiket meg nem szeretnenk `commit`-olni
### stash list
megnezhetjuk, hogy mik vannak a `stash`-ben
### stash show <name>
megmutatja, hogy adott `stash`-ben mi van
### stash show <name> -p
megmutatja, hogy mi van az adott `stash`-ben, es azt is, hogy mi valtozott
### stash apply / pop <name>
pop: a legfelso / megnevezett `elem` visszaallitasa a `stash`-bol, majd torlese onnan<br>
apply: a legfelso / megnevezett `elem` visszaallitasa a `stash`-bol, az elem bent marad a `stash`-ben
### stash drop <name>
torli az adott elemet a `stash`-bol

## Branching
### branch
uj `branch` letrehozasa az aktuallis allasbol<br>
a nev tetszoleges lehet, konvecio szerint csak alphanumerikus ([a-zA-Z0-9])<br>
lehet konyvtarszerkezet szeruen is
### checkout
valtas az egyes branch-ek kozott<br>
git checkout -B <name> - uj `branch` letrehozasa, es valtas ra
### reset
a `HEAD` pointert rakosgatjuk a gitfa egyik pontjabol a masikba (a valtoztatasok megmaradnak)<br>
`git reset --hard` eldobja a valtozasokat

## Merge vs Rebase
gyakori `merge`-eles eseten kisebbek lesznek a `conflict`-jaim, amiket konnyebb lesz megoldani
### merge
strategia fuggo, hogy fog tortenni az agak osszefuzese, tobbnyire idorendben osszefuzi oket a tool<br>
hatrany: osszevissza lesz sok ag osszefesulese utan, hogy mi merre hogyan<br>
--fast-forward: idobelyeg szerinti osszefesules<br>
--no-ff: az eredeti elagazas utan viszi vissza a kulonbozo branch-eket. Erosen ajanlot egy rebase a merge elott. megmarad a history-ban, hogy ez egy kulon feature volt
### mergetool
### rebase
a `feature` agat leveszi az eredeti helyerol, majd a cel ag vegere fuzi azokat
### cherry-pick

## Remote
### Szolgaltatasok
git-annex: ugyes kezelese a nagy meretu binaris file-oknak (nem lassit feleslegesen)

### clone
remote repository masolasa uj localba
### remote
remote server hozzaadasa meglevo local repohoz
### push / pull
valtozasok feltolasa / leszedese remote-rol<br>
`git push origin master:master` - sajat master:remote master
### fetch
a Local es a Remote indexet szinkronba hozza, anelkul, hogy `merge`-et probalna vegrehajtani.<br>
pull helyett:
```
git fetch
git reset --hard origin/master
```

### bisect
binaris keresessel megkeresi, hogy hol van az a `commit`, amely eltori a tesztjeimet
### interactive rebase
history changing<br>
`git rebase -i <patch_hash>`<br>
- r: rewording, commit message megvaltoztatasa
  megvaltozik a fa, ezert ilyenkor `--force`-olni kell a push-t
- tobb commitbol egy commit
- egy commitbol tobb commit

## Hook-ok
eleg sok van, 3 lenyegesebbet kiemelunk
### pre-commit
commit elott van (pl testek futasa)
### commit-msg
commit message mentese utan fut le, de meg mindig a commit elott (formai kovetelmenyek ellenorzese)
### post-receive
Local Indexbol felment a Remote Indexbe, ha minden lefutott, akkor fut ez le (pl Jenkins futasanak inditasa)

## Git tools
### gitk
### git gui
sor szinten megadhato, hogy mi keruljon be a `commit`-ba
### tig

## Seged
### .gitkeep
seged fajl ahhoz, hogy ures konyvtar is belekeruljon (alapbol ures konyvtarakat nem kezel a git)
### .gitignore
ami itt van, azt a git figyelmen kivul fogja hagyni

# Code review tools
## GitHub (Saas)
## GitLab (Saas/self-hosted)
## Gerrit (self-hosted)
## Phabricator (self-hosted)
## Crucible (Saas/self-hosted)

# Erdekessegek
- ls -lR - rekurziv konyvtar listaza
- git log --oneline - rovidebb, atlathatobb lista a logrol