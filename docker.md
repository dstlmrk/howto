# Docker

## Poznamky

* Pokud chci pouzivat databazi z dockeru, tak ji musim nastavit
  v `/etc/mysql/my.cnf` `bind-address = 0.0.0.0` a restartovat sluzbu.
  Nebo pouzivat `--net="host"`.
