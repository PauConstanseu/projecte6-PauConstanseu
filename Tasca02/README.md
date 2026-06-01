# 🌐 T02: Desplegament d’Infraestructura Web amb Apache

**Autor:** Pau Constanseu

**Data:** 6 de març de 2026  

---

### 📝 Introducció i Objectius del Projecte

En aquesta activitat s’ha dut a terme el desplegament i la configuració d’una infraestructura web corporativa utilitzant el servidor **Apache** sobre el sistema operatiu **Ubuntu Server**. Aquesta tasca respon de manera directa a un encàrrec real del client **Projecte Nexus**, una nova organització de formació ubicada a Mataró que requereix establir uns fonaments sòlids i estables per als seus serveis web abans de fer la migració definitiva de tota la seva infraestructura cap a entorns al núvol ☁️.

L’objectiu estratègic ha estat la configuració d'un únic servidor capaç d’allotjar múltiples portals web en paral·lel, maximitzant i optimitzant l'ús dels recursos de maquinari disponibles.

---

### 📂 Arquitectura de Multi-allotjament (VirtualHosts)

Per donar resposta als requeriments del client, s’han desplegat dos llocs web totalment independents mitjançant la tecnologia de **VirtualHosts**, associats als següents dominis de proves:
* `projectenexus.test`
* `academia.test`

Tot el desplegament s'ha executat mantenint una estructura de directoris estrictament clara, aïllada i organitzada dins del sistema de fitxers del servidor per facilitar posteriors tasques d'administració.

---

### 🔐 Securització de l'Entorn i HTTPS

Un dels pilars de l'activitat ha estat la seguretat en la capa de comunicacions. Per blindar el trànsit de dades, s'han implementat les següents mesures:
* **Certificats SSL/TLS:** Generació i lligam de certificats autosignats per a cadascun dels dominis.
* **Connexió segura:** Configuració de l'accés natiu a través del protocol xifrat **HTTPS**.
* **Redirecció automàtica:** Implementació de regles de reescriptura per forçar el salt de HTTP a HTTPS, garantint que cap interacció viatgi en text pla pel canal de xarxa.

---

### ⚡ Optimització del Rendiment i Experiència d'Usuari

Amb la finalitat de lliurar un entorn eficient i d'alta velocitat, s’han aplicat tècniques d’optimització avançades en el servidor web:
1. **Habilitació d'HTTP/2:** Activació d'aquest protocol de xarxa modern per permetre la multiplexació de peticions, fet que redueix dràsticament la latència i accelera la velocitat de càrrega dels portals de formació.
2. **Gestió d'errors personalitzada:** Disseny i integració d'una **pàgina d'error 404 corporativa**, evitant les respostes genèriques del servidor i oferint una imatge molt més professional i integrada de cara a l'usuari final.

---

### ⚙️ Conclusió i Memòria Executiva

La realització d'aquest laboratori ha permès consolidar coneixements pràctics avançats en la instal·lació, manteniment i blindatge d’un servidor web de producció. Tot el procediment tècnic, ordres i configuracions han quedat degudament recollits en una **memòria tècnica executiva**. Aquest document s'ha redactat utilitzant un llenguatge clar i accessible per a perfils de client no tècnics, acompanyat de les evidències que certifiquen el correcte funcionament de la solució proposada.
