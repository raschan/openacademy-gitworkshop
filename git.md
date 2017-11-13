Git - easy to nightmare lvl - Szasz Zoltan

#SCM in general
##Source Code Management
regen: ftp-n keresztul kreativ nevezektan (*-final-release-beta-2....)
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

#Git
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

#Git commands

##Basics
###init
repo inditasa
###status
repo valtozasai a legutolso commit ota
###add
file-ok hozzaadasa a `tracked files`-hoz
* vagy . hasznalatval minden file / folder-t hozza tudok addni a repohoz, ami meg nincs hozzaadva
###commit
hozzaadas a `Local Index`-hez, innentol kezdve koveti a verzio kezelo
minden `commit` kap egy sajat hash-et, amivel lehet ra hivatkozni a kesobbiekben. Ez mindig egyedi, es tobbnyire nem valtozik
`--amend`: nem egy ujabb keszul, hanem hozzaadja az elozo `commit`-hoz, a message szerkesztesenek a lehetosegevel
###log
visszanezni az aktualis `history`-t
###rm
file / folder eltavolitasa a `working copy`-bol (rm es git add parancs osszevonva)
###mv
file / folder mozgatasa, elokeszitve `commit`-ra (mv es git add parancs osszevonva)

##Stash
Kituntetett `branch`, ide lehet bepakolni olyan modositasokat, amiket meg nem szeretnenk `commit`-olni
###stash list
megnezhetjuk, hogy mik vannak a `stash`-ben
###stash show <name>
megmutatja, hogy adott `stash`-ben mi van
###stash show <name> -p
megmutatja, hogy mi van az adott `stash`-ben, es azt is, hogy mi valtozott
###stash apply / pop <name>
pop: a legfelso / megnevezett `elem` visszaallitasa a `stash`-bol, majd torlese onnan
apply: a legfelso / megnevezett `elem` visszaallitasa a `stash`-bol, az elem bent marad a `stash`-ben
###stash drop <name>
torli az adott elemet a `stash`-bol

##Seged
###.gitkeep
seged fajl ahhoz, hogy ures konyvtar is belekeruljon (alapbol ures konyvtarakat nem kezel a git)

#Code review tools

#Erdekessegek
- ls -lR - rekurziv konyvtar listaza
- git log --oneline - rovidebb lista a logrol