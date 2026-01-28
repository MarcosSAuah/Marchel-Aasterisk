# 📞 Marchel - Central Telefónica IP con Asterisk

<div align="center">

<img src="images/logo-marchel.png" alt="Logo Marchel" width="200"/>

[![Asterisk](https://img.shields.io/badge/Asterisk-v22.2.0-orange.svg?logo=asterisk&logoColor=white)](https://www.asterisk.org/)
[![Protocol](https://img.shields.io/badge/Protocol-PJSIP_(UDP)-blueviolet.svg)](https://wiki.asterisk.org/wiki/display/AST/PJSIP+Configuration+Wizard)
[![Database](https://img.shields.io/badge/Database-MariaDB_CDR-pink?logo=mariadb&logoColor=white)](https://mariadb.org/)
[![Web App](https://img.shields.io/badge/Interface-Python_%2F_Flask-yellow?logo=flask)](https://flask.palletsprojects.com/)
[![TTS](https://img.shields.io/badge/TTS-Festival-green.svg)](http://www.cstr.ed.ac.uk/projects/festival/)
[![VoIP](https://img.shields.io/badge/VoIP-Enabled-red.svg)](https://es.wikipedia.org/wiki/Voz_sobre_protocolo_de_internet)
[![Universidad](https://img.shields.io/badge/Universidad-Alcalá-blue.svg)](https://www.uah.es/)

### 📬 Contacto
<table align="center">
  <tr>
    <td align="center">
      <strong>Marcos Santos Aragón</strong>
    </td>
    <td align="center">
      <strong>Chelsea Fernández Hernández</strong>
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="https://www.linkedin.com/in/marcos-santos-aragón/" target="_blank">
        <img src="images/linkedin-icon.png" alt="LinkedIn" width="40" height="40"/>
      </a>
      &nbsp;&nbsp;
      <a href="mailto:marcos.santos.aragon@gmail.com" target="_blank">
        <img src="images/email-icon.png" alt="Email" width="40" height="40"/>
      </a>
      &nbsp;&nbsp;
      <a href="https://github.com/MarcosSAuah" target="_blank">
        <img src="images/github-icon.png" alt="GitHub" width="70" height="40"/>
      </a>
    </td>
    <td align="center">
      <a href="https://www.linkedin.com/in/chelsea-fernandez-hernandez-64a339189/" target="_blank">
        <img src="images/linkedin-icon.png" alt="LinkedIn" width="40" height="40"/>
      </a>
      &nbsp;&nbsp;
      <a href="mailto:chelseafh2003@gmail.com" target="_blank">
        <img src="images/email-icon.png" alt="Email" width="40" height="40"/>
      </a>
      &nbsp;&nbsp;
      <a href="https://github.com/Chelseafh" target="_blank">
        <img src="images/github-icon.png" alt="GitHub" width="70" height="40"/>
      </a>
    </td>
  </tr>
</table>
</div>

---

**Marchel** es una central telefónica completa (PBX) basada en Asterisk, desarrollada como proyecto académico en la **Universidad Politécnica de Alcalá de Henares** para la asignatura *Laboratorio de Redes, Señales y Sistemas*.

Este proyecto implementa un sistema de telefonía IP (VoIP) completo con funcionalidades avanzadas como menús IVR, colas de llamadas, buzón de voz, conferencias, sistema de tarificación y una interfaz web de gestión.

---

## 📋 Tabla de Contenidos

- [Características](#-características)
- [Requisitos del Sistema](#-requisitos-del-sistema)
- [Instalación](#-instalación)
  - [Instalación de Asterisk](#1-instalación-de-asterisk)
  - [Configuración de Usuarios](#2-configuración-de-usuarios)
  - [Configuración de Idioma](#3-configuración-de-idioma)
- [Funcionalidades](#-funcionalidades)
  - [Buzón de Voz](#buzón-de-voz)
  - [Música en Espera](#música-en-espera)
  - [Transferencias de Llamadas](#transferencias-de-llamadas)
  - [Conferencias](#conferencias)
  - [Text-to-Speech (TTS)](#text-to-speech-tts)
  - [Menú IVR](#menú-ivr)
  - [Colas de Llamadas](#colas-de-llamadas)
  - [Conexión entre PBXs](#conexión-entre-pbxs)
  - [Base de Datos y CDR](#base-de-datos-y-cdr)
  - [Interfaz Web](#interfaz-web)
- [Configuración de Cliente (Zoiper)](#-configuración-de-cliente-zoiper)
- [Arquitectura del Sistema](#-arquitectura-del-sistema)
- [Contribuciones y Sugerencias](#-contribuciones-y-sugerencias)
- [Autores](#-autores)
- [Bibliografía](#-bibliografía)
- [Licencia](#-licencia)

---

## ✨ Características

- **📱 Sistema VoIP completo** basado en Asterisk con protocolo PJSIP
- **👥 Gestión de usuarios** con extensiones personalizadas (2XXX)
- **📧 Buzón de voz** con mensajes personalizados
- **🎵 Música en espera** configurable
- **🔄 Transferencias de llamadas** (ciegas y asistidas)
- **🎤 Conferencias** tipo Discord con control de administrador
- **🗣️ Text-to-Speech** con Festival (voces en español)
- **📞 Menú IVR** para atención al cliente
- **⏰ Colas de llamadas** para soporte técnico
- **🔗 Conexión entre PBXs** mediante troncales PJSIP
- **💾 Base de datos MariaDB** para registro de llamadas (CDR)
- **💰 Sistema de tarificación** automático
- **🌐 Interfaz web** con Flask para estadísticas y gestión
- **🌍 Soporte multiidioma** (español configurado)

---

## 🖥️ Requisitos del Sistema

- **Sistema Operativo**: Ubuntu 24.04 LTS (recomendado)
- **RAM**: Mínimo 2GB (4GB recomendado)
- **Disco**: 20GB libres
- **Asterisk**: Versión 20 o superior (para soporte PJSIP)
- **MariaDB**: Versión 10.x o superior
- **Python**: 3.8 o superior (para scripts de tarificación y web)
- **Festival**: Para síntesis de voz (TTS)

---

## 🚀 Instalación

### 1. Instalación de Asterisk

#### Actualizar el sistema

```bash
sudo apt update && sudo apt upgrade -y
```

#### Instalar dependencias necesarias

```bash
sudo apt install -y build-essential wget libssl-dev libncurses5-dev \
libnewt-dev libxml2-dev linux-headers-$(uname -r) libsqlite3-dev \
uuid-dev libjansson-dev libedit-dev
```

#### Descargar Asterisk

Descarga la versión más reciente desde [https://downloads.asterisk.org/pub/telephony/asterisk/](https://downloads.asterisk.org/pub/telephony/asterisk/)

```bash
cd /usr/src
sudo wget https://downloads.asterisk.org/pub/telephony/asterisk/asterisk-20-current.tar.gz
sudo tar -xvzf asterisk-20-current.tar.gz
cd asterisk-20*/
```

#### Instalar dependencias adicionales

```bash
sudo contrib/scripts/get_mp3_source.sh
sudo contrib/scripts/install_prereq install
```

#### Configurar Asterisk

```bash
sudo ./configure
```

Asegúrate de habilitar los módulos necesarios:

```bash
sudo make menuselect
```

En el menú, verifica que estén habilitados:
- **Add-ons**: `res_config_mysql`, `cdr_mysql`
- **Resource Modules**: `res_odbc`, `res_config_odbc`
- **Applications**: `app_festival`

Guarda y sal con `Save & Exit`.

#### Compilar e instalar

```bash
sudo make -j$(nproc)
sudo make install
sudo make samples
sudo make config
```

#### Crear usuario y grupo Asterisk

```bash
sudo groupadd asterisk
sudo useradd -r -d /var/lib/asterisk -g asterisk asterisk
sudo usermod -aG audio,dialout asterisk
```

#### Configurar permisos

Edita `/etc/default/asterisk` y descomenta:

```bash
AST_USER="asterisk"
AST_GROUP="asterisk"
```

Asigna permisos:

```bash
sudo chown -R asterisk:asterisk /etc/asterisk
sudo chown -R asterisk:asterisk /var/{lib,log,spool}/asterisk
sudo chown -R asterisk:asterisk /usr/lib/asterisk
```

#### Iniciar Asterisk

```bash
sudo systemctl daemon-reload
sudo systemctl enable asterisk
sudo systemctl start asterisk
sudo systemctl status asterisk
```

Accede a la consola de Asterisk:

```bash
sudo asterisk -rvvv
```

### 2. Configuración de Usuarios

#### Editar `/etc/asterisk/pjsip.conf`

Configura el protocolo de transporte UDP:

```ini
[transport-udp]
type=transport
protocol=udp
bind=0.0.0.0
```

#### Crear usuarios (extensiones 2XXX)

Ejemplo para el usuario 2001:

```ini
[2001-softphone]
type=endpoint
context=office-phone
disallow=all
allow=ulaw
auth=2001-auth
aors=2001

[2001-auth]
type=auth
auth_type=userpass
username=2001-softphone
password=Hola123

[2001]
type=aor
max_contacts=1
```

Configura el idioma globalmente:

```ini
[global]
type=global
language=es
```

Recarga la configuración:

```bash
asterisk -rx "pjsip reload"
```

#### Verificar usuarios

```bash
asterisk -rx "pjsip show endpoints"
asterisk -rx "pjsip show aors"
```

#### Editar `/etc/asterisk/extensions.conf`

Configurar llamadas entre usuarios:

```ini
[office-phone]
exten => 2001,1,Answer()
same => n,Dial(PJSIP/2001,20,m)
same => n,Hangup()

exten => 2002,1,Answer()
same => n,Dial(PJSIP/2002,20,m)
same => n,Hangup()
```

Recarga el dialplan:

```bash
asterisk -rx "dialplan reload"
```

### 3. Configuración de Idioma

#### Crear directorio para español

```bash
sudo mkdir -p /var/lib/asterisk/sounds/es
```

#### Descargar paquetes de audio en español

Desde [https://www.sinologic.net/proyectos/vocesbak/](https://www.sinologic.net/proyectos/vocesbak/)

```bash
cd /var/lib/asterisk/sounds/es
sudo wget https://www.sinologic.net/proyectos/vocesbak/asterisk-sounds-core-es-gsm-1.4.27.tar.gz
sudo wget https://www.sinologic.net/proyectos/vocesbak/asterisk-sounds-extra-es-gsm-1.4.27.tar.gz
```

#### Descomprimir archivos

```bash
sudo tar -xvzf asterisk-sounds-core-es-gsm-1.4.27.tar.gz
sudo tar -xvzf asterisk-sounds-extra-es-gsm-1.4.27.tar.gz
```

#### Reorganizar archivos

Los archivos se descomprimen en subcarpetas `es/`. Muévelos al directorio principal:

```bash
sudo mv dictate/es/* dictate/
sudo mv digits/es/* digits/
sudo mv followme/es/* followme/
sudo mv letters/es/* letters/
sudo mv phonetic/es/* phonetic/
sudo mv silence/es/* silence/
```

#### Asignar permisos

```bash
sudo chmod -R 755 /var/lib/asterisk/sounds/es
sudo chown -R asterisk:asterisk /var/lib/asterisk/sounds/es
```

---

## 🎯 Funcionalidades

### Buzón de Voz

#### Editar `/etc/asterisk/voicemail.conf`

```ini
[default]
2001 => 1234,Usuario 2001
2002 => 1234,Usuario 2002
2003 => 1234,Usuario 2003
```

#### Editar `/etc/asterisk/extensions.conf`

Añadir VoiceMail a las extensiones:

```ini
[office-phone]
exten => 2001,1,Answer()
same => n,Dial(PJSIP/2001,20,m)
same => n,VoiceMail(2001@default,u)
same => n,Hangup()
```

Extensión para acceder al buzón:

```ini
exten => 2000,1,Answer()
same => n,VoiceMailMain(@default)
same => n,Hangup()
```

### Música en Espera

#### Crear directorio

```bash
sudo mkdir -p /var/lib/asterisk/sounds/custom
```

#### Copiar archivos de audio (formato WAV)

```bash
sudo cp mi_audio.wav /var/lib/asterisk/sounds/custom/
sudo sox mi_audio.wav -r 8000 -c 1 /var/lib/asterisk/sounds/custom/espera.wav
```

#### Editar `/etc/asterisk/musiconhold.conf`

```ini
[default]
mode=files
directory=/var/lib/asterisk/sounds/custom
random=yes
```

#### Añadir al dialplan

```ini
exten => 2001,n,MusicOnHold(default)
```

### Transferencias de Llamadas

#### Editar `/etc/asterisk/features.conf`

```ini
[featuremap]
blindxfer => *1        ; Transferencia ciega
atxfer => *2           ; Transferencia asistida
automon => *3          ; Grabación automática
```

#### Habilitar en el dialplan

```ini
exten => 2001,n,Dial(PJSIP/2001,20,tTwW)
```

Opciones:
- `t`: Permite transferencias para quien llama
- `T`: Permite transferencias para quien recibe
- `w`: Permite grabación para quien llama
- `W`: Permite grabación para quien recibe

### Conferencias

#### Editar `/etc/asterisk/confbridge.conf`

```ini
[user]
type=user
admin=no
pin=1234
marked=no
wait_marked=no
end_marked=no

[admin]
type=user
admin=yes
pin=5678
marked=yes

[bridge]
type=bridge
language=es
max_members=10
```

#### Añadir al dialplan

```ini
exten => 3000,1,Answer()
same => n,ConfBridge(1,bridge,user)
same => n,Hangup()

exten => 3001,1,Answer()
same => n,ConfBridge(1,bridge,admin)
same => n,Hangup()
```

### Text-to-Speech (TTS)

#### Instalar Festival

```bash
sudo apt install -y festival festvox-ellpc11k
```

#### Configurar Festival

Edita `/usr/share/festival/festival.scm` y añade antes de `(provide 'festival)`:

```scheme
(define (tts_textasterisk string mode)
  (let ((wholeutt (utt.synth (eval (list 'Utterance 'Text string)))))
    (utt.wave.resample wholeutt 8000)
    (utt.wave.rescale wholeutt 5)
    (utt.send.wave.client wholeutt)))
```

#### Crear servicio systemd

Crea `/etc/systemd/system/festival.service`:

```ini
[Unit]
Description=Festival Speech Synthesis Server
After=network.target

[Service]
Type=simple
User=festival
ExecStart=/usr/bin/festival --server
Restart=always

[Install]
WantedBy=multi-user.target
```

#### Instalar voces en español

```bash
cd /tmp
wget https://github.com/franjvasquezg/festival-spanish-voices/releases/download/1.0/es_voices.tar.gz
sudo tar -xvzf es_voices.tar.gz -C /usr/share/festival/voices/spanish/
```

#### Configurar `/etc/festival.scm`

```scheme
(set! voice_default 'voice_JuntaDeAndalucia_es_pa_diphone)
```

#### Configurar `/etc/asterisk/festival.conf`

```ini
[general]
host=localhost
port=1314
```

#### Iniciar Festival

```bash
sudo systemctl daemon-reload
sudo systemctl enable festival
sudo systemctl start festival
```

#### Usar en el dialplan

```ini
exten => 9000,1,Answer()
same => n,Festival("Bienvenido a la central Marchel")
same => n,Hangup()
```

### Menú IVR

El menú IVR (Interactive Voice Response) permite a los usuarios interactuar con el sistema mediante el teclado telefónico.

#### Crear usuario operadora en `pjsip.conf`

```ini
[1010]
type=endpoint
context=operadora-menu
disallow=all
allow=ulaw
auth=1010-auth
aors=1010

[1010-auth]
type=auth
auth_type=userpass
username=1010
password=Pass123

[1010]
type=aor
max_contacts=1
```

#### Configurar menú en `extensions.conf`

```ini
[operadora-menu]
exten => s,1,Answer()
same => n,Set(TIMEOUT(digit)=5)
same => n,Set(TIMEOUT(response)=10)
same => n(menu),Background(custom/bienvenida)
same => n,WaitExten()

; Opción 1: Soporte técnico
exten => 1,1,Goto(soporte-tecnico,s,1)

; Opción 2: Información de tarifas
exten => 2,1,Answer()
same => n,Festival("Las tarifas son de 0.05 euros por minuto")
same => n,Goto(operadora-menu,s,menu)

; Opción 3: Buzón de voz
exten => 3,1,VoiceMailMain(@default)
same => n,Hangup()

; Opción 0: Volver a escuchar el menú
exten => 0,1,Goto(operadora-menu,s,menu)

; Timeout o entrada inválida
exten => i,1,Playback(invalid)
same => n,Goto(operadora-menu,s,menu)

exten => t,1,Playback(vm-goodbye)
same => n,Hangup()
```

### Colas de Llamadas

#### Editar `/etc/asterisk/queues.conf`

```ini
[soporte-tecnico]
strategy=rrmemory
timeout=30
retry=5
maxlen=10
announce-frequency=60
announce-holdtime=yes
music=default
member => PJSIP/2001
member => PJSIP/2002
member => PJSIP/2003
```

Estrategias disponibles:
- `ringall`: Llama a todos los agentes
- `leastrecent`: Llama al que menos recientemente atendió
- `fewestcalls`: Llama al que menos llamadas atendió
- `random`: Llamada aleatoria
- `rrmemory`: Round-robin con memoria

#### Configurar en el dialplan

```ini
[soporte-tecnico]
exten => s,1,Answer()
same => n,Queue(soporte-tecnico,tTwW)
same => n,Hangup()
```

### Conexión entre PBXs

Esta funcionalidad permite conectar dos centrales telefónicas Asterisk diferentes mediante troncales PJSIP, permitiendo que usuarios de diferentes servidores puedan comunicarse entre sí.

#### Arquitectura de la conexión

```
┌─────────────────────┐  Troncal PJSIP   ┌─────────────────────┐
│   Servidor A        │◄────────────────►│   Servidor B        │
│   IP: 192.168.1.10  │   (UDP:5060)     │   IP: 192.168.1.78  │
│   Usuarios: 2XXX    │                  │   Usuarios: 6XXX    │
└─────────────────────┘                  └─────────────────────┘
```

#### Configuración en Servidor A

##### 1. Editar `/etc/asterisk/pjsip.conf` en Servidor A

```ini
; Configuración del endpoint para Servidor B
[servidorB]
type=endpoint
context=office-phone
transport=transport-udp
disallow=all
allow=ulaw,alaw,gsm
aors=servidorB-aor
outbound_auth=servidorB-auth
direct_media=no

; Configuración de autenticación
[servidorB-auth]
type=auth
auth_type=userpass
username=servidorB
password=Hola123
realm=servidorB

; Configuración del AOR (Address of Record)
[servidorB-aor]
type=aor
contact=sip:192.168.1.78

; Configuración de registro
[servidorB-registration]
type=registration
outbound_auth=servidorB-auth
server_uri=sip:192.168.1.78
client_uri=sip:servidorB@192.168.1.78
retry_interval=60

; Identificación del servidor remoto
[servidorB-identify]
type=identify
endpoint=servidorB
match=192.168.1.78
```

##### 2. Editar `/etc/asterisk/extensions.conf` en Servidor A

```ini
[office-phone]
; Llamadas locales (usuarios 2XXX)
exten => _2XXX,1,Answer()
same => n,Dial(PJSIP/${EXTEN},20,m)
same => n,Hangup()

; Llamadas al Servidor B (usuarios 6XXX)
exten => _6XXX,1,Answer()
same => n,Dial(PJSIP/${EXTEN}@servidorB,25)
same => n,Hangup()
```

#### Configuración en Servidor B

##### 1. Editar `/etc/asterisk/pjsip.conf` en Servidor B

```ini
; Configuración del endpoint para Servidor A
[servidorA]
type=endpoint
context=office-phone
transport=transport-udp
disallow=all
allow=ulaw,alaw,gsm
aors=servidorA-aor
outbound_auth=servidorA-auth
direct_media=no

; Configuración de autenticación
[servidorA-auth]
type=auth
auth_type=userpass
username=servidorA
password=Hola123
realm=servidorA

; Configuración del AOR
[servidorA-aor]
type=aor
contact=sip:192.168.1.10

; Configuración de registro
[servidorA-registration]
type=registration
outbound_auth=servidorA-auth
server_uri=sip:192.168.1.10
client_uri=sip:servidorA@192.168.1.10
retry_interval=60

; Identificación del servidor remoto
[servidorA-identify]
type=identify
endpoint=servidorA
match=192.168.1.10
```

##### 2. Editar `/etc/asterisk/extensions.conf` en Servidor B

```ini
[office-phone]
; Llamadas locales (usuarios 6XXX)
exten => _6XXX,1,Answer()
same => n,Dial(PJSIP/${EXTEN},20,m)
same => n,Hangup()

; Llamadas al Servidor A (usuarios 2XXX)
exten => _2XXX,1,Answer()
same => n,Dial(PJSIP/${EXTEN}@servidorA,25)
same => n,Hangup()
```

#### Parámetros importantes

- **direct_media=no**: Desactiva la conexión directa entre endpoints, útil cuando hay NAT
- **outbound_auth**: Define las credenciales para autenticación saliente
- **realm**: Identifica el dominio de autenticación del servidor remoto
- **retry_interval**: Tiempo en segundos entre intentos de registro
- **match**: Dirección IP del servidor remoto para identificación

#### Verificación de la conexión

En ambos servidores, verifica:

```bash
# Ver endpoints configurados
asterisk -rx "pjsip show endpoints"

# Ver registros activos
asterisk -rx "pjsip show registrations"

# Ver identificaciones
asterisk -rx "pjsip show identities"

# Probar conectividad
asterisk -rx "pjsip qualify servidorA"  # En Servidor B
asterisk -rx "pjsip qualify servidorB"  # En Servidor A
```

#### Solución de problemas comunes

**El registro falla**:
- Verifica que las IPs sean correctas y accesibles
- Comprueba que el puerto 5060 esté abierto en ambos firewalls
- Verifica las credenciales (username/password)

**No se pueden realizar llamadas**:
- Verifica el dialplan en ambos servidores
- Comprueba que los contextos coincidan
- Revisa los logs: `tail -f /var/log/asterisk/messages`

**Problemas de audio**:
- Verifica los códecs permitidos (allow/disallow)
- Comprueba la configuración de NAT si aplica
- Revisa que `direct_media=no` esté configurado

#### Ejemplo de uso

Una vez configurado:

1. Usuario 2001 en Servidor A marca `6001`
2. La llamada se enruta a través del troncal hacia Servidor B
3. El usuario 6001 en Servidor B recibe la llamada
4. Viceversa para llamadas de 6XXX hacia 2XXX

### Base de Datos y CDR

#### Instalar MariaDB

```bash
sudo apt install -y mariadb-server mariadb-client
sudo systemctl enable mariadb
sudo systemctl start mariadb
sudo mysql_secure_installation
```

#### Crear base de datos y usuario

```bash
sudo mysql -u root -p
```

```sql
CREATE DATABASE asterisk_cdr;
CREATE USER 'asterisk'@'localhost' IDENTIFIED BY 'password123';
GRANT ALL PRIVILEGES ON asterisk_cdr.* TO 'asterisk'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

#### Crear tabla CDR

```sql
USE asterisk_cdr;

CREATE TABLE cdr (
    calldate DATETIME NOT NULL DEFAULT '0000-00-00 00:00:00',
    clid VARCHAR(80) NOT NULL DEFAULT '',
    src VARCHAR(80) NOT NULL DEFAULT '',
    dst VARCHAR(80) NOT NULL DEFAULT '',
    dcontext VARCHAR(80) NOT NULL DEFAULT '',
    channel VARCHAR(80) NOT NULL DEFAULT '',
    dstchannel VARCHAR(80) NOT NULL DEFAULT '',
    lastapp VARCHAR(80) NOT NULL DEFAULT '',
    lastdata VARCHAR(80) NOT NULL DEFAULT '',
    duration INT(11) NOT NULL DEFAULT 0,
    billsec INT(11) NOT NULL DEFAULT 0,
    disposition VARCHAR(45) NOT NULL DEFAULT '',
    amaflags INT(11) NOT NULL DEFAULT 0,
    accountcode VARCHAR(20) NOT NULL DEFAULT '',
    uniqueid VARCHAR(150) NOT NULL DEFAULT '',
    userfield VARCHAR(255) NOT NULL DEFAULT ''
);
```

#### Instalar ODBC

```bash
sudo apt install -y unixodbc unixodbc-dev libmyodbc
```

#### Configurar ODBC

Edita `/etc/odbcinst.ini`:

```ini
[MySQL]
Description = MySQL driver
Driver = /usr/lib/x86_64-linux-gnu/odbc/libmyodbc8w.so
Setup = /usr/lib/x86_64-linux-gnu/odbc/libodbcmyS.so
FileUsage = 1
```

Edita `/etc/odbc.ini`:

```ini
[asterisk-connector]
Description = MySQL connection to asterisk database
Driver = MySQL
Database = asterisk_cdr
Server = localhost
Port = 3306
Socket = /var/run/mysqld/mysqld.sock
```

#### Configurar Asterisk

Edita `/etc/asterisk/res_odbc.conf`:

```ini
[asterisk]
enabled => yes
dsn => asterisk-connector
username => asterisk
password => password123
pre-connect => yes
```

Edita `/etc/asterisk/cdr_adaptive_odbc.conf`:

```ini
[first]
connection=asterisk
table=cdr
```

#### Verificar conexión

```bash
asterisk -rx "odbc show"
```

### Interfaz Web

La interfaz web está desarrollada con Flask y permite a los usuarios consultar estadísticas, historial de llamadas y tarifas.

#### Instalar dependencias

```bash
sudo apt install -y python3 python3-pip python3-venv
pip3 install flask mysql-connector-python pandas matplotlib
```

#### Estructura del proyecto

```
/var/www/marchel/
├── app.py
├── templates/
│   ├── login.html
│   ├── dashboard.html
│   ├── estadisticas.html
│   ├── historial.html
│   └── tarifas.html
└── static/
    ├── css/
    └── js/
```

#### Script de tarificación

Crea `/usr/local/bin/tarificar.py`:

```python
#!/usr/bin/env python3
import mysql.connector
from datetime import datetime

# Conexión a la base de datos
db = mysql.connector.connect(
    host="localhost",
    user="asterisk",
    password="password123",
    database="asterisk_cdr"
)

cursor = db.cursor()

# Tarifa: 0.05€ por minuto
TARIFA_POR_MINUTO = 0.05

# Obtener llamadas no tarificadas
query = "SELECT uniqueid, billsec FROM cdr WHERE tarificado = 0"
cursor.execute(query)

for (uniqueid, billsec) in cursor:
    minutos = billsec / 60
    coste = minutos * TARIFA_POR_MINUTO
    
    # Actualizar registro
    update = "UPDATE cdr SET coste = %s, tarificado = 1 WHERE uniqueid = %s"
    cursor.execute(update, (coste, uniqueid))

db.commit()
cursor.close()
db.close()
```

#### Automatizar con CRON

```bash
sudo crontab -e
```

Añadir:

```
0 * * * * /usr/bin/python3 /usr/local/bin/tarificar.py
```

---

## 📱 Configuración de Cliente (Zoiper)

Zoiper es una aplicación VoIP gratuita compatible con Asterisk.

### Descargar Zoiper

- **Android/iOS**: Busca "Zoiper" en la tienda de aplicaciones
- **Desktop**: [https://www.zoiper.com/en/voip-softphone/download/current](https://www.zoiper.com/en/voip-softphone/download/current)

### Configurar usuario

1. **Abrir Zoiper** y seleccionar "Continue with Free"
2. **Introducir credenciales**:
   - Usuario: `2001-softphone`
   - Contraseña: `Hola123`
3. **Configurar servidor**:
   - IP: Dirección IP de tu servidor Asterisk (obtenerla con `ip a`)
   - Puerto: `5060` (por defecto)
4. **Verificar conexión**: Debe aparecer "Registered" o "Online"

### Realizar llamadas

- Para llamar a otro usuario, marca su extensión (ej: `2002`)
- Para acceder al buzón de voz, marca `2000`
- Para unirte a la conferencia, marca `3000`
- Para acceder al menú IVR, marca `1010`
- Para llamar a otra PBX, marca extensiones como `6001`, `6002`, etc.

---

## 🏗️ Arquitectura del Sistema

```
┌─────────────────────────────────────────────────────────┐
│                    Usuarios Finales                     │
│              (Zoiper, Softphones, etc.)                 │
└─────────────────────────────┬───────────────────────────┘
                              │
                              │ SIP/PJSIP (UDP:5060)
                              │
┌─────────────────────────────▼──────────────────────────┐
│                  Servidor Asterisk A                   │
│  ┌─────────────────────────────────────────────────┐   │
│  │        Módulos Principales                      │   │
│  │          • PJSIP (Gestión de usuarios)          │   │
│  │          • Dialplan (Lógica de llamadas)        │   │
│  │          • Voicemail (Buzones de voz)           │   │
│  │          • ConfBridge (Conferencias)            │   │
│  │          • Queue (Colas de llamadas)            │   │
│  │          • Festival (Text-to-Speech)            │   │
│  └─────────────────────────────────────────────────┘   │
└─────────────────┬───────────────────────────┬──────────┘
                  │                           │
        ┌─────────┴────────┐                  │ Troncal PJSIP
        │                  │                  │
        ▼                  ▼                  ▼
┌────────────────┐  ┌─────────────┐  ┌──────────────────┐
│   MariaDB      │  │ Interfaz Web│  │  Servidor        │
│   (CDR, etc.)  │  │   (Flask)   │  │  Asterisk B      │
└────────────────┘  └─────────────┘  └──────────────────┘
```

---

## 💡 Contribuciones y Sugerencias

Este proyecto fue desarrollado como parte de un trabajo universitario. Si tienes sugerencias, comentarios o detectas algún error en la documentación, nos encantaría conocer tu opinión.

### 📧 Contacto:

<p align="center">
  <a href="mailto:marcos.santos.aragon@gmail.com" target="_blank">
    <img src="https://img.shields.io/badge/Email-marcos.santos.aragon%40gmail.com-red?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
  <a href="mailto:chelseafh2003@gmail.com" target="_blank">
    <img src="https://img.shields.io/badge/Email-chelseafh2003%40gmail.com-red?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
</p>

Estaremos encantados de recibir tu feedback sobre:
- ✅ Mejoras en la documentación
- ✅ Correcciones de errores
- ✅ Sugerencias de nuevas funcionalidades
- ✅ Experiencias al implementar esta guía

---

## 👥 Autores

Este proyecto fue desarrollado como **Práctica 2** de la asignatura *Laboratorio de Redes, Señales y Sistemas* en la **Universidad Politécnica de Alcalá de Henares**.

**Desarrolladores**:

<table>
  <tr>
    <td align="center">
      <strong>Marcos Santos Aragón</strong><br>
      <a href="https://www.linkedin.com/in/marcos-santos-aragón/" target="_blank">
        <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
      </a>
      <a href="https://github.com/MarcosSAuah" target="_blank">
        <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
      </a>
    </td>
    <td align="center">
      <strong>Chelsea Fernández Hernández</strong><br>
      <a href="https://www.linkedin.com/in/chelsea-fernandez-hernandez-64a339189/" target="_blank">
        <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
      </a>
      <a href="https://github.com/Chelseafh" target="_blank">
        <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
      </a>
    </td>
  </tr>
</table>

**Universidad**: Universidad Politécnica de Alcalá de Henares  
**Asignatura**: Laboratorio de Redes, Señales y Sistemas  
**Curso**: 2024-2025

---

## 📚 Bibliografía

- [Documentación oficial de Asterisk](https://wiki.asterisk.org/)
- [Guía PJSIP de Zadarma](https://zadarma.com/es/support/instructions/asteriskpjsip/)
- [Tutorial de Asterisk de Javier Ortiz](https://github.com/javierorp/Asterisk_Tutorial)
- [Laboratorio de contextos especiales VoIPdo](https://www.voipdo.com/wp-content/uploads/2017/04/Laboratorio-de-contextos-especiales.pdf)
- [Troncal PJSIP entre servidores Asterisk](https://medium.com/asterisk-tips-101/troncal-pjsip-entre-servidores-asterisk-48e6468ecc8e)
- [Instalar Asterisk con ODBC y MariaDB](https://blackhold.nusepas.com/2020/07/23/instalar-asterisk-con-odbc-configurar-odbc-mariadb/)
- [Festival Spanish Voices](https://github.com/franjvasquezg/festival-spanish-voices)
- [Voces Festival en español](https://www.voztovoice.org/?q=comment/484#comment-484)

---

## 📝 Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para más detalles.

---

## 🙏 Agradecimientos

- A la **Universidad Politécnica de Alcalá de Henares** por el apoyo académico
- A los profesores de *Laboratorio de Redes, Señales y Sistemas*
- A la comunidad de Asterisk por la documentación y recursos
- A todos los que contribuyeron con código, ideas y feedback

---

## 📝 Notas Adicionales

### Comandos útiles de Asterisk

```bash
# Acceder a la CLI de Asterisk
sudo asterisk -rvvv

# Recargar módulos
asterisk -rx "pjsip reload"
asterisk -rx "dialplan reload"
asterisk -rx "module reload"

# Ver usuarios registrados
asterisk -rx "pjsip show endpoints"
asterisk -rx "pjsip show registrations"

# Ver llamadas activas
asterisk -rx "core show channels"

# Ver colas
asterisk -rx "queue show"

# Ver conferencias
asterisk -rx "confbridge list"

# Depuración
asterisk -rx "pjsip set logger on"
asterisk -rx "core set verbose 5"
```

### Solución de problemas comunes

**No se registran los usuarios en Zoiper**:
- Verifica que Asterisk esté corriendo: `sudo systemctl status asterisk`
- Comprueba la IP del servidor: `ip a`
- Verifica que el puerto 5060 esté abierto: `sudo ufw allow 5060/udp`
- Revisa los logs: `sudo tail -f /var/log/asterisk/messages`

**No funciona el buzón de voz**:
- Verifica que los permisos estén correctos: `sudo chown -R asterisk:asterisk /var/spool/asterisk/voicemail`
- Comprueba la configuración: `asterisk -rx "voicemail show users"`

**Festival no funciona**:
- Verifica que el servicio esté activo: `sudo systemctl status festival`
- Comprueba la conexión: `asterisk -rx "festival test"`
- Revisa los logs: `sudo journalctl -u festival -f`

**Problemas con la conexión entre PBXs**:
- Verifica la conectividad de red entre servidores: `ping IP_SERVIDOR_REMOTO`
- Comprueba los registros PJSIP: `asterisk -rx "pjsip show registrations"`
- Revisa los endpoints: `asterisk -rx "pjsip show endpoints"`
- Verifica que los puertos estén abiertos en ambos firewalls
- Revisa los logs de ambos servidores para errores de autenticación

---

**¿Tienes preguntas o sugerencias?** No dudes en contactarnos por correo electrónico o a través de nuestros perfiles de GitHub. 😊

---

⭐ Si este proyecto te ha sido útil, considera darle una estrella en GitHub. ¡Gracias!