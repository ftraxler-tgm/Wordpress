# Aufsetzen der Arbeitsumgebung

Setzen  Sie entsprechend der mündlichen Vorgaben eine entsprechende  Arbeitsumgebung basierend auf einem Webserver (beliebig) einem  Datenbankmanagementssystem (mySQL) sowie der Scriptsprache PHP auf.

Installieren Sie im Folgenden die beiden CMS Joomla und Wordpress.

Richten  Sie die beiden Systeme grundlegend ein (Benutzer, einige Testbeiträge,  usw.) und machen Sie sich mit den jeweiligen Interfaces vertraut.

Dokumentieren Sie ihre Fortschritte in Form eines PDF und geben sie es hier ab.



## Installation von Wordpress:
```bash
docker pull wordpress
docker pull mysql
```
Damit man jetzt den Docker Wordpress-Container mit dem Mysql-Container verbindet muss man folgenden Befehl ausführen

```bash
docker run -ti -d --name=some-mysql -P -e MYSQL_ROOT_PASSWORD="password" -e MYSQL_ALLOW_EMPTY_PASSWORD=yes mysql --default-authentication-plugin=mysql_native_password; docker run --name some-wordpress -v /home/Dokumente/Wordpress/:/var/www/html --link some-mysql:mysql -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD="password" -p 8080:80 -d wordpress
```

Mit diesem Befehl erstellt man die Container und verbindet sie mit einander.

Um die Container zu starten einfach:

```bash
docker start some-mysql
docker start some-wordpress
```

Dann geht man auf http://localhost:8080/ und folgt dort einfach den Installationsschritten

## Installation von Joomla

```bash
docker pull joomla
docker pull mysql
```

Damit man jetzt den Docker Joomla-Container mit dem Mysql-Container verbindet muss man folgenden Befehl ausführen

```bash
docker run -ti -d --name=some-mysqlJoomla -P -e MYSQL_ROOT_PASSWORD="password" -e MYSQL_ALLOW_EMPTY_PASSWORD=yes mysql --default-authentication-plugin=mysql_native_password; docker run --name some-joomla --link some-mysqlJoomla:mysql -e JOOMLA_DB_USER=root -e JOOMLA_DB_PASSWORD="password" -p 8080:80 -d joomla
```

Mit diesem Befehl erstellt man die Container und verbindet sie mit einander.

Um die Container zu starten einfach:

```bash	
docker start some-mysqlJoomla
docker start some-joomla
```

Dann geht man auf http://localhost:8080/ und folgt dort einfach den Installationsschritten

Bei der Einrichtung der Datenbank ist folgendes einzutragen

* Docker-ContainerName
* User(root)
* Passwort(password)
* Datenbank(joomla)

Danach folgt man erneut einfach den Installationsschritten