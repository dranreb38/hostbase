# hostbase
A Ruby GUI based on advanced rogue AP attack




~~~~~~~~~~~~~~~~~~ Hostbase project By Koala @ crack-wifi.com @ wifi-libre.com @ kali-linux.fr ~~~~~~~~~~~~~~~~~~~~

 Bienvenido en hostbase // Bienvenue sur hostbase
 
FR: Ce script marche sous kali-linux, pour l'installation et la mise en marche
de la version française se référer au fichier ALIRIMPORTANT situé dans le dossier de hostbase-1.4FR.

ES: Readme hecho ara los usarios de kali-linux.El script anda bien sobre kali-linux xfce presicamente

PARA TODOS DEPENDENCIAS DEL SCRIPT

apt-get install -y build-essential upgrade-system subversion wget g++ iptables pavucontrol ffmpeg sqlite3 libsqlite3-dev libssl-dev libnl-3-dev libnl-genl-3-dev dsniff hostapd isc-dhcp-server pkg-config xterm freeradius apache2 php libapache2-mod-php php-cli tcpdump python3-scapy vokoscreen wireshark bridge-utils devscripts gengetopt autoconf libtool make

____________________________________________



Saber si mi tarjeta wifi esta compatible con hostapd, commando a entrar:
iw list | grep "Supported interface modes" -A 8

Si esta compatible te saldra eso:

Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * WDS
		 * monitor
		 * mesh point


Si no te sale eso tendras que usar la carpeta airbase que esta con el archivo de hostbase.


Si tienes una version de hostapd antigua suprima lo:
apt-get remove hostapd

Y compila lo asi:

wget https://w1.fi/cgit/hostap/snapshot/hostap_2_9.tar.gz
tar -zxf hostap_2_9.tar.gz
cd /root/hostap_2_9/hostapd
cp defconfig .config
nano .config

Decomentar el # en todas las opciones que siguen:

CONFIG_DRIVER_NL80211=y
CONFIG_LIBNL32=y
CONFIG_EAP_PWD=y
CONFIG_WPS=y
CONFIG_WPS_UPNP=y
CONFIG_WPS_NFC=y
CONFIG_RADIUS_SERVER=y
CONFIG_IEEE80211N=y
CONFIG_IEEE80211AC=y
CONFIG_DEBUG_FILE=y
CONFIG_FULL_DYNAMIC_VLAN=y
CONFIG_TLSV11=y
CONFIG_TAXONOMY=y


Y termina con:

sudo make
sudo make install
hostapd -v

________________________________________________

Servidor web apache2: se copia el fichero 000-default.conf que esta puesto con el archivo de hostbase en /etc/apache2/site-available.
Para terminar se copia el fichero apache2.conf que esta puesto con el archivo de hostbase en /etc/apache2

Se copia todo lo que hay en la carpeta paginasAQUI a dentro el répertorio /etc  (son las falsas paginas de phishing)

________________________________________________


Installar las dependencias de los gems de ruby:


apt-get install ruby
apt-get install ruby-dev
gem install highline
gem install rake
gem install bundler
apt-get install libgtk2.0-dev
apt install gobject-introspection
apt install ruby-gtk2



_________________________________________________
mdk4
apt-get install mdk4

_________________________________________________
berate_ap
apt install berate-ap
_________________________________________________

EN/ES/FR start:

El script se tiene que ejecutar en la carpeta /tmp
Copia y pega la carpeta hostbase-1.3ES a dentro la carpeta /tmp

A dentro /tmp/hostbase-1.3ES click derecho, abrir un terminal aqui

 Inicia lo asi //
ruby hostbase.rb

--> OJO: no olvidas de empezar por el scan de redes para apagar network-manager <-- 


____________________________________________________


Cuando se entra el nombre de la pagina de phishing, debes éligir las paginas con el boton wps, entraras asi y todo en minusculo:
orangewps 
o
movistarwps
o
vodafonewps
o
onowps
o
jazztelwps
o
vodafonewps
etc etc...

La clave esta registrado por defecto en /etc/wpa_supplicant.conf, despuès del attaque para ver si la clave ha sido capturada con el WPS-PBC entra eso en un nuevo terminal:
cat /etc/wpa_supplicant.conf

(Una vez el boton wps apoyado, hay que esperar un poco para que se hace la conexion a travès el wps-pbc)

____________________________________________________

Hostbase tiene un tchat para hacer se pasar por el servicio technico.Una vez que has empezado el ataque, puedes ir en la pagina del tchat (cada url corresponde a una pagina):

Orange : http://127.0.0.1/msftconnecttest/orange/shout/orangechat.php   para Orange
Vodafone : http://127.0.0.1/msftconnecttest/vodafone/shout/vodatchat.php    para Vodafone
Ono : http://127.0.0.1/msftconnecttest/ono/shout/onotchat.php           para Ono
Movistar : http:127.0.0.1/msftconnecttest/movistar/shout/movitchat.php  para movistar
Jazztel : http://127.0.0.1/msftconnecttest/jazztel/shout/jazztchat.php    para Jazztel

Una ves en la pagina del tchat tienes que enviar un mensaje en PRIMERO para que anda:
"Hola soy del servicio technico como puedo ayudar ? "

Despuès si el usario hace "Ayuda en linea" en la pagina de phishing principal, se pondra en el tchat directamente y podras hablar con el.



_____________________________________________________




Para mas potentia este script ANDA con 2 tarjeta wifi porqué automatisa un monton de cosas: el AP encryptado con el WPS, la DoS que sigue el Ap etc... (anda con 3 tarjetas wifi si quieres el ataque en 5GHz)

A CADA PRUEBAS:
--> Se tiene que empezar por el scan de redes para parar network-manager y tener informacion sobre la red que quieres
--> Se sale del script cada vez con ctrl+c, eso es para dejar todo bien limpio despuès un ataque...
--> La DoS que sigue el AP anda con wash, wash tiene que estar installado tambien (pero no tienes que installar lo si tienes kali-linux esta installado por defecto)

--> A la salida del script con ctrl+c se réeiniciara network-manager o sea si quieres hacer otras pruebas sin pasa por el scan de redes cada vez, tendras que apagar network-manager por no tener problemo, si network-manager esta andando mientras haces pruebas tendras problemos.Se para con:

systemctl stop NetworkManager.service
systemctl disable NetworkManager.service

y para poner lo en marcha:

systemctl enable NetworkManager.service
systemctl start NetworkManager.service


Mi consejo es de séguir pasando por el san de redes entre 2 ataque porqué el AP puede mover de canal (channel hopping).

Preguntas y soporte en wifi-libre: http://www.wifi-libre.com/topic-1657-hostbase-14-esta-aqui.html

Buenas :)

