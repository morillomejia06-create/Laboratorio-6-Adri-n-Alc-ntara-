# Laboratorio-6-Adri-n-Alc-ntara-
Comandos utilizados en las practicas de Linux
Practica 1 – Cifrado con GPG2

Actualizar repositorios

sudo apt update

Instalar GPG2

sudo apt install gnupg2

Verificar instalacion

gpg –version

Crear directorio

mkdir cifrado

Entrar al directorio

cd cifrado

Crear archivo

nano secreto.txt

Cifrar archivo

gpg -c secreto.txt

Ver archivo cifrado

cat secreto.txt.gpg

Descifrar archivo

gpg secreto.txt.gpg

Mostrar contenido

cat secreto.txt

Practica 2 – Firewall con IPTables y UFW

Instalar servidor web HTTP

sudo apt install apache2

Verificar servicio

sudo systemctl status apache2

Instalar FTP

sudo apt install vsftpd

Verificar servicio FTP

sudo systemctl status vsftpd

Instalar SSH

sudo apt install openssh-server

Verificar servicio SSH

sudo systemctl status ssh

Bloquear puertos con IPTables

sudo iptables -A INPUT -p tcp –dport 80 -j DROP sudo iptables -A INPUT
-p tcp –dport 21 -j DROP sudo iptables -A INPUT -p tcp –dport 22 -j DROP

Ver reglas

sudo iptables -L

Eliminar reglas

sudo iptables -D INPUT -p tcp –dport 80 -j DROP sudo iptables -D INPUT
-p tcp –dport 21 -j DROP sudo iptables -D INPUT -p tcp –dport 22 -j DROP

Activar UFW

sudo ufw enable

Ver estado

sudo ufw status

Bloquear puertos

sudo ufw deny 80 sudo ufw deny 21 sudo ufw deny 22

Permitir nuevamente

sudo ufw allow 80 sudo ufw allow 21 sudo ufw allow 22

Practica 3 – IDS Snort

Instalar Snort

sudo apt update sudo apt install snort

Ver version

snort -V

Ver interfaces de red

ip a

Editar reglas locales

sudo nano /etc/snort/rules/local.rules

Probar configuracion

sudo snort -T -c /etc/snort/snort.conf

Ejecutar Snort

sudo snort -A console -q -c /etc/snort/snort.conf -i eth0

Pruebas desde la maquina host

ping IP_DE_LA_VM ssh usuario@IP_DE_LA_VM ftp IP_DE_LA_VM

Acceso web

http://IP_DE_LA_VM

Practica 4 – 2FA con Google Authenticator para SSH

Instalar Google Authenticator PAM

sudo apt update sudo apt install libpam-google-authenticator

Configurar autenticador

google-authenticator

Configurar PAM

sudo nano /etc/pam.d/sshd

Configurar SSH

sudo nano /etc/ssh/sshd_config

Reiniciar SSH

sudo systemctl restart ssh

Probar acceso desde host

ssh usuario@IP_DE_LA_VM
