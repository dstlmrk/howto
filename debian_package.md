# Tvorba a instalace debian balicku

## Priprava baliku

Vyvorit v projektu slozku `debian` a tam nasledujici soubory:

* `changelog`
* `compat` - verze debhelperu
* `control` - doplnime vsechny zavislosti
* `install` - jake soubory mame kam nakopirovat do systemu (odinstalace je smaze)
* `postinst` - co se ma zavolat po instalaci, napr. zavolani sh skriptu
* `rules` - muzeme "tunit" balicek, napr. s jakyma flagama se bude kompilovat atd.

## Ubaleni baliku

Tvorba baliku a smazani nepotrebnych souboru:

```bash
dpkg-buildpackage -us -uc -d
debian/rules clean
```

## Otestovani

Spustim potrebny image pro nasledny test:

```bash
docker run -it --name="ubuntu_test" --net="host" ubuntu
```

Pokud potrebuju muzu si na nem nainstalovat zakladni programy:

```bash
apt-get update
apt-get install iputils-ping wget nano
```

Ze sveho pocitace zkopiruju debiani balicek do kontejneru:

```bash
docker cp performax-proxysql_0.0.1_all.deb ubuntu_test:/
```

V kontejneru se pokusim nainstalovat balicek:

```bash
dpkg -i performax-proxysql_0.0.1_all.deb
```

A pokud vyzaduje nektere zavislosti (zkontrolovat, ze mam v `/etc/apt/sources.list.d`
vsechny repozitare), tak instalaci dokoncim pomoci:

```bash
apt-get install -f
```

## Nasazeni do repa

Pouziva se program deb2rep.
