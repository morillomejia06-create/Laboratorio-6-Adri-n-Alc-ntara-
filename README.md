# Laboratorio-6-Adri-n-Alc-ntara-
Comandos utilizados en las practicas de Linux

===================================
PRACTICA 1 - Cifrado con GPG2
===================================

# Actualizar repositorios e instalar repositorios 
sudo apt update && sudo apt upgrade -y

# Instalar GPG2
sudo apt install gnupg2

# Verificar instalacion
gpg –version

# Crear directorio
sudo mkdir cifrado

# Entrar al directorio
cd cifrado

# Crear archivo
sudo nano secreto.txt

# Cifrar archivo
gpg -c secreto.txt

# Ver archivo cifrado
cat secreto.txt.gpg

# Borrar el archivo original
sudo rm secreto.txt

# Descifrar archivo
gpg secreto.txt.gpg

# Mostrar contenido
cat secreto.txt

=========================================
PRACTICA 2 - Firewall con IPTables y ufw
=========================================

# Actualizar repositorios e instalar repositorios 
sudo apt update && sudo apt upgrade -y

# Instalar servidor web HTTP
sudo apt install apache2

# Verificar servicio
sudo systemctl status apache2

# Instalar FTP
sudo apt install vsftpd

# Verificar servicio FTP
sudo systemctl status vsftpd

# Instalar SSH
sudo apt install openssh-server

# Verificar servicio SSH
sudo systemctl status ssh

# Bloquear puertos con IPTables
sudo iptables -A INPUT -p tcp –dport 80 -j DROP 
sudo iptables -A INPUT -p tcp –dport 21 -j DROP 
sudo iptables -A INPUT -p tcp –dport 22 -j DROP

# Ver reglas
sudo iptables -L

# Eliminar reglas
sudo iptables -D INPUT -p tcp –dport 80 -j DROP 
sudo iptables -D INPUT -p tcp –dport 21 -j DROP 
sudo iptables -D INPUT -p tcp –dport 22 -j DROP

**------UFW------**

# Activar UFW
sudo ufw enable

# Ver estado
sudo ufw status

# Bloquear puertos
sudo ufw deny 80 
sudo ufw deny 21 
sudo ufw deny 22

# Permitir nuevamente
sudo ufw allow 80 
sudo ufw allow 21 
sudo ufw allow 22

========================
PRACTICA 3 - IDS Snort
========================

# Actualizar repositorios e instalar repositorios 
sudo apt update && sudo apt upgrade -y

# Instalar Snort
sudo apt install snort

# Editar reglas locales
sudo nano /etc/snort/rules/local.rules

# Probar configuracion
sudo snort -T -c /etc/snort/snort.conf

# Ejecutar Snort
sudo snort -A console -q -c /etc/snort/snort.conf -i ens33

# Pruebas desde la maquina host
ping IP_DE_LA_VM 
ssh usuario@IP_DE_LA_VM 
ftp IP_DE_LA_VM
http://IP_DE_LA_VM

====================================================
PRACTICA 4 - 2FA con Google Authenticator para SSH
====================================================

# Actualizar repositorios e instalar repositorios 
sudo apt update && sudo apt upgrade -y

# Instalar Google Authenticator PAM
sudo apt install libpam-google-authenticator

# Configurar autenticador
google-authenticator

# Configurar PAM
sudo nano /etc/pam.d/sshd

# Configurar SSH
sudo nano /etc/ssh/sshd_config

# Reiniciar SSH
sudo systemctl restart ssh

# Probar acceso desde host
ssh usuario@IP_DE_LA_VM
