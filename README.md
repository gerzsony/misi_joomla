# Joomla Misinek
Joomla repo Misinek, Goldenmind

###### Rendszer felélesztésének és a vele való ismerkedés becsült időigénye: 30 perc.


# Előfeltételek 
###### (időigénye: 10 perc)

1) Telepítsd a docker desktopot innét:
https://docs.docker.com/docker-for-windows/install/
Letöltöd, telepíted. Felajánlja, hogy regisztrálj a dockerhub-ra, de erre nincs szükséged.

2) telepítsd a git for windowst, innét
https://git-scm.com/downloads

3) előfordulhat hogy ujra kell indítani a gépedet (amire telepítéskor figyelmeztet) akkor ezt tedd meg.

# Telepítés 
###### (időigénye: 10 perc)

1) nyiss egy parancssori ablakot (az asztalon található keresőbe gépeld be hogy cmd, majd enter)
navigálj abba a könyvtárba ahol szívesen dolgoznál és nyisd meg. 
A "cd könyvtárneve" paranccsal kinyitsz egy könyvtárat a "cd .." -el egyet visszalépsz a root könyvtár felé,  a dir paranccsal megnézed, hogy mik vannak abban a könyvtárban (listázol)
pl.:

```
cd ..
cd ..
cd ..
dir
md misi_docker
cd misi_docker
dir
```

2) amikor már a kívánt könyvtárba navigáltál, akkor huzzuk le a repo -t, azaz csináljunk egy másolatot a gépedre a konfig fájlokból.
Ezek a varázsfájlok, amik a semmiből csinálnak neked konkrét rendszert :)
Ezt gépeld be:

```
git clone https://github.com/gerzsony/misi_joomla.git
```

Ha ez nem menne, a https://github.com/gerzsony/misi_joomla oldalon töltsd le zipben csomagold ki és másold be a kivánt könyvtárba.

3) Ha már ott vannak a varázsfájljaid, akkor leheljük életre a rendszert.
Ellenőrizd, hogy fut-e a docker desktopod (dobozokkal megrakott delfin vagy mi az ikonja)
Aztán még mindig az adott könyvtárban állva (parancssorban) add ki ezt a parancsot:

```
docker-compose up
```

Ekkor ö elkezd buidelni, ez eltarthat pár percig. Csomagokat huz le a netről és telepít. Ha már nem futnak a parancssorban a sorok felfelé, akkor kész a build. Ha hibát írt ki, egyeztessünk.

# Használat 
###### (ismerkedés időigénye: 10 perc)

Build után a következő helyeken már elérhetők a cuccok

Joomla:
http://localhost

PhpMyadmin:
http://localhost:81

Mysql (mysql klienssel):
localhost:3306

mysql user: root
mysql jelszó: 12345678

# Advanced Használat

A build során belerakja a Te adatbázisod dump-ját azaz máris kész (te adataiddal feltöltött) adatbázissal indulsz
A joomla viszont friss telepítésű (bár nem a legfrisebb verziószámú - direkt) így szabadon nyaggatható 
(friss telepítésű lesz, szabadon adhatsz hozzá modulokat, stb)

HA A MOSTANI TELEPÍTETT ÁLLAPOTOT SZERETNÉD MODELLEZNI, akkor töltsd le a www könyvtárat a szerveredről és csapd vele felül a www könyvtárat.
ha az adatbázishoz fájlszinten hozzáférnél ugyanezt megteheted a database könyvtárral is, de a dump ezt már megoldotta magától.

így máris az éles joomla-dat klónoztad az éles adatbázisoddal

arra figyelj, hogy ez esetben újra kell konfigurálni az adatbáziskapcsolatot a joomla -val, hiszen ott más a felhaználó és a jelszó az adatbázishoz.

Ha összeraktál egy elinduló változatot, az adott könyvtár tetszőleges számú másolásával ugyanennyi számú müködő klón készíthető.

Hasznos infó: Ha van több változatod, egyszerre csak egy tud belőle futni hisz ugynazokat a portokat akarja használni a gépeden egy újabb példány is.
ezek a 80, 81, 3306 -os portok.

A docker-compose.yml fájlban ezek modosíthatóak, ez esetben több példány is tud futni egyszerre a gépeden.

# Hasznos parancsok

hasznos docker parancsok 

A futó konténerek listázása (neked 3 futó konténert kell látnod)
```
docker ps
```

konténerek indítása és leállítása(a docker-compose.yml fájlt tartalmazó könyvtárban)
```
docker-compose up
docker-compose down
```

Docker gyorsparancsok:
https://medium.com/the-code-review/top-10-docker-commands-you-cant-live-without-54fb6377f481
