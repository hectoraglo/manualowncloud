# Instal·lació i configuració d'aplicacions web


## Instal·lació d'apache2, mysql i algunes llibreries al contenidor

1. Actualització de la màquina.
```console
sudo apt update
```
```console
sudo apt upgrade
```

2. Instal·lació del servidor web `apache2`.
```console
sudo apt install -y apache2
```

3. Instal·lació del servidor de bases de dades `mysql-server`.
```console
sudo apt install -y mysql-server
```

4. Instal·lació d'algunes llibreries de `php`, el llenguatge principal que utilitzen les aplicacions.
```console
sudo apt install -y php libapache2-mod-php
```
```console
sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
```

5. Reiniciem el servidor apache2
```console
sudo systemctl restart apache2
```

## Configuració de MySQL
### Accedim a la consola de MySQL
Des d'un terminal on siguem `root` hem d'executar la següent comanda:
```console
sudo mysql
```
![consola mysql](https://github.com/user-attachments/assets/084d38d7-090e-46d1-9c62-b89125da621f)

### Creació de la base de dades:
Un cop dins la consola de MySQL executem les comandes per a crear la base de dades. En aquest cas estem creant una base de dades amb el nom `bbdd`.

```console
CREATE DATABASE bbdd;
```
![base de datos bbdd](https://github.com/user-attachments/assets/5d308613-ad61-43d0-aa86-aeb70b8c8474)

### Creació d'un usuari
Tingueu en compte que s'haurà d'identificar la IP des de la qual s'accedirà a la base de dades, en aquest cas, `localhost`.

```console
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
![usuario mysql](https://github.com/user-attachments/assets/d3207619-7eb9-4718-924d-68dc08b23e92)

### Donem privilegis a l'usuari:
```console
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
```
![privilegios usuario mysql](https://github.com/user-attachments/assets/1dab9066-02f9-42ca-aaed-803de7a163c1)

### Sortim de la base de dades
```console
exit
```

### Probem la connexió a la base de dades
Des d'un terminal amb un usuari sense privilegis hem de ser capaços de connectar introduïnt la nostra contrassenya.

```console
mysql -u usuario -p
```


## Accedim al navegador per veure que tot funciona
Poseu la direcció http://localhost al navegador web i configureu la cloud.

Si tot ha anat bé i heu seguit el manual us apareixerà l'instal·lador de l'aplicació web que heu baixat i us demanarà crear un usuario admin i la informació de la base de dades.

La informació que heu de posar (si no heu modificat la informació del manual) és la següent:

* **usuari:** usuario
* **contrasenya:** password
* **base de dades:** bbdd
* **domini:** localhost

## Enllaços a les diferents clouds
* ***OwnCloud***: http://www.owncloud.org
* ***Nextcloud***: http://www.nextcloud.com

## Heu de baixar el .zip de Nextcloud Server
https://download.nextcloud.com/server/releases/latest.zip

## Heu de baixar el .zip de ownCloud Server
https://download.owncloud.com/server/stable/owncloud-complete-20240724.zip

### Instal·lar la versió 7.4 de PHP a Ubuntu 24.04

Per a poder instal·lar ownCloud necessitarem la versió 7.4 de PHP, per a instal·lar-la al nostre sistema haurem de fer les següents comandes:

Actualitza les llistes de paquets i actualitza tots els paquets existents al vostre sistema. 

Instal·leu els requisits previs de PPA:
```bash
sudo apt install software-properties-common -y
```

Instal·la les eines necessàries per treballar amb els arxius de paquets personals (PPA).
```bash
LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y
```

Actualitza ara els repositoris:
```bash
sudo apt update
```

Instal·la les llibreries de PHP de la versió 7.4
```bash
sudo apt install php7.4 -y
```
```bash
sudo apt install -y php libapache2-mod-php7.4
```

```bash
sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl
```

Seleccioneu la versió de PHP que voleu:
```bash
sudo update-alternatives --config php
```

Activa els mòduls d'apache2 necessaris:
```bash
sudo a2enmod proxy_fcgi setenvif
```

```bash
sudo a2enconf php7.4-fpm
```

Reinicieu l'apache2:
```bash
sudo service apache2 restart
```
# Configuracio d'ownCLoud
## Creació d'usuaris
<p>Per crear usuaris anem a la part dreta on surt el nostre usuari i cliquem.
<p>Per crear el usuari tenim que posar el nom de l'usuari, i un e-mail, que pot ser inventat.
<p>Aixo es fa en l'espai de dalt del teu usuari que posa el que he dit abans.
<p>Ara creem 3 o 4 usuaris.
## Assignem rols i permisos
<p> Ara assignarem rols al nostres usuaris creats.
<p> Per crear un rol li tenim que clicar on posa "Add group", i tindras ja dos rols creats predeterminats, "Everyone" i "Admin".
  <p>I creem dos rols nous, els que vulguis.
<p>Per assignar els rols en un usuari li donem a "Group" en el mateix usuari i l'assignem el rol que acabem de crear.
<p>Ara assignem permisos al nostres usuaris.
<p>Li donem a "users" que posa d'alt del tot, i aqui donem a "Archivos"
<p>Aqui seleccionem la carpeta a que volem donar permisos als nostres usuaris.
<p> I li donem a "sharing", posem el nom dels rols que volem donar permisos a aquesta carpeta, o el nom de l'usuari al que volem donar permisos en aquesta carpeta.
<p>I si li donem al engranatge al costat del usuari o rol, podem posar que pot fer aquest grup o persona. 
<p>I amb aixo ja ahuriem d'haver acabat de configurar rols i permisos als rols.
# Administració d'arxius.
<p>Per crear arxius, carpetes o pujar fitxers, em de donarle al "+" que posa dalt de les carpetes predeterminades.
<p>I creem una carpeta amb qualsevol nom.
<p> Ara creem un arxiu dins de la carpeta 
<p>I aquest arxiu serveix com un document, pots escriure el que vulguis dins.
<p>També pots pujar un arxiu desde la teva propia maquina.
<p>I dins de l'arxiu com en les carpetes, també pots donar permisos a usuaris d'editar els arxius o pujar mes arxius.
