# 🔏 **T06: Infraestructura de Certificats Digitals i Signatura Electrònica**  

**Autor:** Pol Serrano Aromí i Pau Constanseu Ros

**Data:** 16/03/2026  

---
## 1. Índex

1. Índex
2. Preparació de l'entorn
3. Creació de l'Entitat de Certificació
4. Generació de la clau i certificat d'usuari
5. Distribució de Certificats (Servidor - Client)
6. Instal·lació de Certificats al Client
7. Signatura Digital d'un PDF
8. Conclusió

---
## 2. Preparació de l'entorn 🔥

Primer de tot començarem instal·lant els dos equips, on serà en aquests cas un Ubuntu Server per fer totes les configuracións dels certificats i les signatures i un Windows 11 per fer les proves, en les següents captures us mostro les característices dels entorns com els adaptadors.

![foto1](/Tasca06/img/1.png)
![foto2](/Tasca06/img/2.png)

Seguidament un cop tinguem els equips muntats i instal·lats, en el windows pausarem les actualitzacions, ja que al ser una mv totes les actualitzacions del principi que et posa windows solen tardar molt, i sí a més estem fent-ho desde una mv anirà encara més lent.

![foto3](/Tasca06/img/3.png)

Continuarem configurant una IP estàtica al servidor i client amb el següent esquema:

    |    Equip    | IP          |
    |-------------|-------------|
    | Windows     | 192.168.2.4 |
    | Server      | 192.168.2.21|

![foto4](/Tasca06/img/4.png)
![foto6](/Tasca06/img/6.png)

Finalment comprovem que la IP que està correctament modificada:

![foto5](/Tasca06/img/5.png)
![foto7](/Tasca06/img/7.png)

Un cop configurades les IPs de cada equip, haurem de canviar el nom del servidor:

![foto8](/Tasca06/img/8.png)

Seguidament tocarà configurar en el client l'arxiu de hosts per resoldre el nom del servei web (ca.nexus12.test) a la seva IP corresponent.

![foto9](/Tasca06/img/9.png)

Un cop fet aquests pas hem volgut fer un ping de client > servidor per comprovar que tota la configuració (ips, canvi de nom, hosts) esta correctament configurat.

![foto10](/Tasca06/img/10.png)

---
## 3. Creació de l'Entitat de Certificació 🗳️

Primer de tot haurem d'editar l'arxiu de configuració de OpenSSL (

bash
sudo nano /etc/ssl/openssl.cnf


Per configurar la CA. Afegir una secció específica per a la CA corporativa:

![foto11](/Tasca06/img/11.png)

Seguidament crearem l'estructura de directoris per a la CA i inicialitzar els fitxers necessaris:

![foto12](/Tasca06/img/12.png)

Continuarem generan la clau privada de la CA i el certificat d'autoritat:

![foto13](/Tasca06/img/13.png)

---
## 4. Generació de la clau i certificat d'usuari 🔑

Primer de tot simularem l'emissió del certificat d'usuari directament des del servidor. Per això, generarem una clau privada per a l'usuari.

![foto14](/Tasca06/img/14.png)

Seguidament haurem de signar la sol·licitud amb la clau privada de la nostre CA acabada de crear.

![foto15](/Tasca06/img/15.png)

Finalment, haurem d'exportar i convertir el certificat a format PKCS#12 (amb extensió .pfx), el format estàndard per a la instal·lació als equips clients.

![foto16](/Tasca06/img/16.png)

---
## 5. Distribució de Certificats (Servidor - Client) 👱

Seguidament continuem amb la part de distribució de Certificats, on l'usuari a de rebre tant el certificat de la CA com el seu certificat personal. En el nostre cas hem volgut realitzar el metòde avançat on haurem de instal·lar apache i posterioment crearem una pàgina HTML senzilla amb els ennllaços per descàrregar els dos fitxers.

Primer de tot copiarem tant el certificat arrel com el del usuari dins de la carpeta de de Apache.

![foto17](/Tasca06/img/17.png)

Seguidament crearem un index.html bàsic, on li hem volgut donar el següent aspecte:

![foto18](/Tasca06/img/18.png)

Després comprovem desde el client que podem accedir a la pàgina i que podem descàrregar els dos certificats:

![foto19](/Tasca06/img/19.png)

Posteriorment descàrragem els fitxers:

![foto20](/Tasca06/img/20.png)

---
## 6. Instal·lació de Certificats al Client 📖

Continuarem instal·lant Adobe en el client mitjançant l'eina winget, on primer de tot farem un search per veure quins Adobe Acrobat és troben disponibles per instal·lar.

![foto21](/Tasca06/img/21.png)

Al cap d'un temps ens apareixarà un pop-up dient que adobe s'estarà instal·lant al equip.

![foto22](/Tasca06/img/22.png)

Seguidament executarem la consola de ejecutables (win+r) i buscarem certmgr.msc amb això ens trobarem dins de la consola de administració de certificats.

Anirem a la branca d'Entitats de confiança arrel i importarem el certificat del servidor (cacert.pem), perquè així el sistema operatiu reconegui la nostre pròpia CA com a una CA segura.

![foto23](/Tasca06/img/23.png)
![foto24](/Tasca06/img/24.png)

Comprovem que està correctament importada:

![foto25](/Tasca06/img/25.png)

Per acabar, anirem a la secció de **"Personal"** i importarem el certficat d'usuari

![foto26](/Tasca06/img/26.png)

Haurem de instroduïr la clau de protecció que vam tenir que establir al servidor durant l'exportació

![foto27](/Tasca06/img/27.png)

Comprovem que el certificat d'usuari està importat:

![foto28](/Tasca06/img/28.png)

---
## 7. Signatura Digital d'un PDF 📄

En el últim apartat, vam tenir que descàrregar algun PDF de prova, per això vam accedir a pàgines com [Documento de prueba. UNI Málaga](https://www.uma.es/ejemplo-grupo-de-investigacion/navegador_de_ficheros/repositorio-grupos-de-investigacion/descargar/documentaci%C3%B3n%20becas%20junta/documento%20de%20prueba.pdf) o [Datos Abierto Colombia](https://herramientas.datos.gov.co/sites/default/files/2021-08/Pruebas_3.pdf) allà ens vam descàrregar un PDF amb imatges per fer les proves.

Vam obrir el PDF de prova amb Adobe Acrobat

![foto29](/Tasca06/img/29.png)

Dins del Adobe, vam accedir a **"Usar Certificat"**, vam tenir que seleccionar la zona d'on voliem signar i un cop seleccionada la zona ens va sortir el següent apartat on habiem de seleccionar la Firma.

![foto31](/Tasca06/img/31.png)

Un cop la seleccionem ens sortirà una mica l'especte de la firma, com és per realitzar una tasca senzilla tampoc li modificarem res, però sí fos per àmbits professional si que la canviàriem.

![foto32](/Tasca06/img/32.png)

Podrem veure com queda la firma nostre en el propi PDF:

![foto33](/Tasca06/img/33.png)

I si finalment, guardem el PDF i l'obrim veurem que la signatura fet és vàlida i no hi ha ningún error.

![foto34](/Tasca06/img/34.png)

---
## 8. Conclusió 💻

Amb la realització d’aquesta activitat s’ha pogut implementar una infraestructura pròpia d’autoritat de certificació (CA) per a l’empresa Projecte Nexus. Mitjançant la creació i emissió de certificats digitals, els treballadors poden signar documents electrònics garantint la integritat, l’autenticitat i el no repudi de la informació. La prova de concepte demostra que és possible gestionar certificats i signatures digitals de manera interna, millorant la seguretat i modernitzant la gestió de documents dins de l’organització.
