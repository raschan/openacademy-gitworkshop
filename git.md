Git - easy to nightmare lvl - Szasz Zoltan

# SCM in general
## Source Code Management
regen: ftp-n keresztul kreativ nevezektan (*-final-release-beta-2....).
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
10 eve irta meg Linus Torvalds, Linux kernel tarolasara jott letre.
Elosztott verzio-kezelo rendszer
  nalunk is verzio kezelt a kod (megvan a history)
  Working copy - ezen dolgozunk
  Local index
  Remote-ok

  a kod egy bizonyos allapota mindenkinel meglesz
Branch-ek - elagazasok adott kod allapotbol, pl uj feature-ok, vagy bug-fix-ek
Az egyes branchek egyes allapotai tag-elhetok (kiemelt, konnyen celozhato commit-ok)
elosegiti a review-t
conflict feloldasok
atirhato a tortenelem

# Git commands

## Basics
### init
repo inditasa
### status
repo valtozasai a legutolso commit ota
### add
file-ok hozzaadasa a `tracked files`-hoz
* vagy . hasznalatval minden file / folder-t hozza tudok addni a repohoz, ami meg nincs hozzaadva
### commit
hozzaadas a `Local Index`-hez, innentol kezdve koveti a verzio kezelo
minden `commit` kap egy sajat hash-et, amivel lehet ra hivatkozni a kesobbiekben. Ez mindig egyedi, es tobbnyire nem valtozik
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
pop: a legfelso / megnevezett `elem` visszaallitasa a `stash`-bol, majd torlese onnan
apply: a legfelso / megnevezett `elem` visszaallitasa a `stash`-bol, az elem bent marad a `stash`-ben
### stash drop <name>
torli az adott elemet a `stash`-bol

## Branching
### branch
uj `branch` letrehozasa az aktuallis allasbol
a nev tetszoleges lehet, konvecio szerint csak alphanumerikus ([a-zA-Z0-9])
lehet konyvtarszerkezet szeruen is
### checkout
valtas az egyes branch-ek kozott
git checkout -B <name> - uj `branch` letrehozasa, es valtas ra
### reset
a `HEAD` pointert rakosgatjuk a gitfa egyik pontjabol a masikba (a valtoztatasok megmaradnak)
`git reset --hard` eldobja a valtozasokat

## Merge vs Rebase
gyakori `merge`-eles eseten kisebbek lesznek a `conflict`-jaim, amiket konnyebb lesz megoldani
### merge
strategia fuggo, hogy fog tortenni az agak osszefuzese, tobbnyire idorendben osszefuzi oket a tool
hatrany: osszevissza lesz sok ag osszefesulese utan, hogy mi merre hogyan
--fast-forward: idobelyeg szerinti osszefesules
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

## Seged
### .gitkeep
seged fajl ahhoz, hogy ures konyvtar is belekeruljon (alapbol ures konyvtarakat nem kezel a git)
### .gitignore
ami itt van, azt a git figyelmen kivul fogja hagyni

# Code review tools

# Erdekessegek
- ls -lR - rekurziv konyvtar listaza
- git log --oneline - rovidebb, atlathatobb lista a logrol