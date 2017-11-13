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
###commit
###rm
###mv

#Code review tools