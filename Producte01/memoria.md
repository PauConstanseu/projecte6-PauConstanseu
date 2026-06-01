# 📘 Memòria Tècnica Final

## 🎯 Projecte Nexus e-Learning

**Consultors:** Pol Serrano i Pau Constanseu 

**Data:** 27 de març de 2026

---

### 📑 Índex

1. [🧩 Introducció](#-1-introducció)
2. [🌍 Context i necessitats del client](#-2-context-i-necessitats-del-client)
3. [⚔️ Comparativa tecnològica: Apache vs Nginx](#-3-comparativa-tecnològica-apache-vs-nginx)
4. [🎓 Comparativa LMS: Moodle vs Canvas](#-4-comparativa-lms-moodle-vs-canvas)
5. [🔗 Proposta de solució i integració](#-5-proposta-de-solució-i-integració)
6. [💰 Estimació econòmica (VPS)](#-6-estimació-econòmica-vps)
7. [🔧 Manteniment del sistema](#-7-manteniment-del-sistema)
8. [🌱 Qualitat i sostenibilitat (Green IT)](#-8-qualitat-i-sostenibilitat)
9. [🏁 Conclusions](#-9-conclusions)

---

### 🧩 1. Introducció

Aquest document recull la **proposta tècnica i estratègica** final desenvolupada per a l’empresa **Nexus e-learning**, amb l'objectiu de dissenyar i desplegar una infraestructura de xarxa i sistemes robusta que doni suport a la seva nova plataforma d’aprenentatge en línia[cite: 1]. 

El projecte s'ha abordat des d'una perspectiva global de consultoria IT: no es limita a la mera configuració tècnica de serveis, sinó que inclou la prospecció de les necessitats reals de l’organització, la comparativa analítica de les tecnologies de l'estat de l'art i la justificació d'una arquitectura viable i optimitzada[cite: 1]. Aquesta memòria s'ha estructurat seguint els estàndards d'un **lliurament professional de consultoria** per a un entorn de producció real[cite: 1].

---

### 🌍 2. Context i necessitats del client

Nexus e-learning requereix la implantació d'un entorn virtual d'aprenentatge optimitzat per a la gestió eficient de cursos, usuaris, matriculacions i continguts interactius. Per garantir l'èxit del desplegament, l'arquitectura de sistemes dissenyada ha de respondre de manera estricta als següents vectors i requisits clau:

* **⚡ Alt rendiment i disponibilitat:** Garantir l'accés continu i fluid als recursos educatius.
* **👥 Concurrència d'usuaris:** Capacitat de suportar múltiples peticions i usuaris simultanis en hores punta.
* **💰 Eficiència financera:** Mantenir un cost d'infraestructura indexat i totalment controlat.
* **🔧 Operativitat:** Facilitat de manteniment, administració i resolució d'incidències per a l'equip tècnic.
* **🌱 Sostenibilitat corporativa:** Implementació de polítiques de **Green IT** per minimitzar l'impacte ambiental.
* **📈 Escalabilitat:** Disseny modular preparat per créixer orgànicament en funció de la demanda del mercat.

---

### ⚔️ 3. Comparativa tecnològica: Apache vs Nginx

#### 🔍 Anàlisi general
S'ha dut a terme un estudi comparatiu entre els dos servidors web líders del mercat, avaluant el seu comportament en entorns de producció sota criteris de rendiment brut, arquitectura de configuració i consum de recursos del sistema.

#### 🧑‍💻 Experiència pràctica de laboratori
* **Apache HTTP Server:** Va demostrar un procés d'instal·lació molt ràpid i una corba d'aprenentatge suau gràcia a una configuració modular intuïtiva, tot i que l'estructura de directoris i fitxers `.htaccess` pot resultar atomitzada en projectes complexos.
* **Nginx:** Presenta una configuració inicial més exigent i centralitzada a través d'un únic bloc de fitxers. En entorns de concurrència genèrica ofereix un comportament excel·lent, tot i que requereix un ajust fi (*fine-tuning*) per optimitzar el consum en aplicacions d'alt processament dinàmic PHP.

#### 📊 Conclusions de rendiment
* **Apache** destaca per la seva flexibilitat, maduresa i facilitat d'administració de manera nativa.
* **Nginx** ofereix una gestió d'esdeveniments asíncrona ideal per a contingut estàtic i grans volums de trànsit.

#### ✅ Decisió final i justificació
Es selecciona **Apache** com el motor web del projecte. Aquesta decisió es fonamenta en la seva **simplicitat de configuració**, la reducció de la complexitat per a l'equip de sistemes i una major facilitat de manteniment ordinari, alineant-se perfectament amb el dimensionament actual de Nexus e-learning.

---

### 🎓 4. Comparativa LMS: Moodle vs Canvas

#### 🔍 Anàlisi general
S'han analitzat les dues plataformes de gestió de l'aprenentatge (LMS) amb major penetració en el sector acadèmic i corporatiu: Moodle i Canvas LMS.

#### 🧑‍💻 Experiència pràctica de laboratori
* **Moodle:** Destaca pel seu potent ecosistema de codi obert i una capacitat de personalització i administració de permisos gairebé il·limitada. Tot i que la seva corba d'instal·lació inicial i posta a punt és més exigent, ofereix un gran avantatge en permetre actualitzacions automàtiques de mòduls i seguretat.
* **Canvas LMS:** Ofereix una interfície d'usuari (UI) altament intuïtiva de fàbrica, però és molt més rígida a l'hora d'aplicar modificacions de codi core i requereix processos d'actualització totalment manuals. 
  * *Incidències detectades:* Durant les proves d'estrés i configuració intensiva de cursos de 5 a 10 minuts, la plataforma va llançar de manera reiterada errors d'inestabilitat en l'entorn local. Així mateix, el seu model complet sovint resta lligat a llicències o subscripcions comercials que n'eleven el cost.

#### 📊 Conclusions
* **Moodle** atorga un control absolut de les dades, auditoria i funcionalitats pedagògiques de la plataforma.
* **Canvas** prioritza el disseny visual en detriment de la flexibilitat de codi i l'autonomia d'infraestructura.

#### ✅ Decisió final i justificació
Es selecciona **Moodle** com l'LMS oficial. La tria es justifica per la seva naturalesa **Open Source** (sense costos de llicència), la seva robustesa en entorns autoallotjats i la capacitat d'adaptació modular a llarg termini sense dependències de tercers.

---

### 🔗 5. Proposta de solució i integració

#### 🏗️ Arquitectura del sistema
S'ha dissenyat un model d'arquitectura clàssic i altament desacoblat en tres capes per garantir l'estabilitat i la seguretat dels fluxos de dades:

#### 🔄 Funcionament del flux de peticions
1. L'estudiant realitza una petició HTTP/HTTPS mitjançant el navegador web.
2. El servidor **Apache** rep i processa la petició de xarxa de manera segura.
3. Apache redirigeix l'execució del codi dinàmic al motor de **Moodle**.
4. Moodle interactua amb la **base de dades** per extreure o actualitzar la informació acadèmica (notes, usuaris, recursos).
5. Es renderitza la resposta i el servidor web la retorna de forma xifrada a l'usuari final.

#### 🎯 Resultat obtingut
S'assoleix un entorn de producció net, amb una topologia de xarxa clarament delimitada, fàcil de monitorar i completament preparada per a processos d'escalabilitat vertical o horitzontal.

---

### 💰 6. Estimació econòmica (VPS)

#### 🖥️ Requisits de l'entorn dimensionat
Per donar suport al binomi Apache-Moodle amb suficients garanties de concurrència, s'ha definit la següent plantilla de maquinari virtual:
* **Processament:** 8 vCPU
* **Memòria RAM:** Entre 16 GB i 32 GB RAM (depenent de la càrrega simultània de l'LMS)
* **Emmagatzematge:** 400 GB - 500 GB en discs d'estat sòlid (SSD) per assegurar taxes d'I/O elevades
* **Ubicació jurídica i física:** Nodes allotjats estrictament dins la **Unió Europea** per garantir el compliment normatiu del RGPD[cite: 1].

#### 🔍 Proveïdor seleccionat i costos
Després d'avaluar les diferents alternatives del mercat basant-nos en criteris de ràtio rendiment/preu i latència de xarxa, s'ha triat la infraestructura de **IONOS**[cite: 1]:

| Paràmetre de Facturació | Rang de Cost Estimats |
| :--- | :--- |
| **Cost Mensual** | 15,00 € – 16,00 € |
| **Cost Anual (Acumulat)** | 190,00 € – 200,00 € |

---

### 🔧 7. Manteniment del sistema

Per garantir que la solució romangui segura, operativa i lliure d'incidències, s'estableix un pla de manteniment preventiu i proactiu basat en quatre pilars:

* **🛡️ Seguretat Activa:** Aplicació periòdica de pegats del sistema operatiu base, actualitzacions del core de Moodle i revisions de regles de tallafocs.
* **📊 Monitoratge:** Monitoratge de mètriques de CPU, RAM, emmagatzematge i cabal de xarxa per anticipar col·lapses.
* **💾 Còpies de Seguretat:** Automatització de *backups* diaris dels fitxers de Moodle i de la base de dades, seguint polítiques de retenció segures.
* **⚙️ Resolució d'incidències:** Protocols d'actuació ràpida davant de possibles caigudes de servei.

#### 👨‍💻 Recursos humans requerits
L'arquitectura està tan optimitzada que l'administració general pot ser assumida perfectament per **un sol tècnic de sistemes**, minimitzant els costos de personal i mantenint un control total de l'entorn de producció.

---

### 🌱 8. Qualitat i sostenibilitat

#### ✅ Assegurament de la qualitat
La plataforma incorpora mètriques de validació contínua del sistema. El cicle d'actualitzacions regulars del programari garanteix l'absència de codi obsolet, incrementant de manera directa la seguretat de les dades de Nexus e-learning.

#### ⚡ Optimització de recursos i eficiència energètica
Mitjançant la implementació d'Apache i l'ajust estricte dels paràmetres de memòria cau, s'ha minimitzat el consum innecessari de cicles de CPU i blocs de memòria RAM. Evitant la sobrecàrrega dels servidors, s'aconsegueix un rendiment òptim sense requerir sobreprovisionament de maquinari.

#### 🌍 Green IT
El disseny de la infraestructura s'ha realitzat sota principis de tecnologia sostenible[cite: 1]:
* **Reducció de la petjada de carboni:** En triar un VPS altament optimitzat, es maximitza l'eficiència de la computació utilitzada[cite: 1].
* **Menys recursos = Menor impacte ambiental:** Una arquitectura de programari eficient requereix menys consum elèctric i dissipació tèrmica en els centres de dades[cite: 1].
* **Escalabilitat conscient:** La infraestructura només s'ampliarà mitjançant maquetació sota demanda, evitant el malbaratament d'energia en hores de baixa activitat.

---

### 🏁 9. Conclusions

La solució dissenyada per a **Nexus e-learning** demostra que és possible conjugar un alt rendiment amb un model econòmicament viable i sostenible[cite: 1]. La simbiosi de l'arquitectura d'**Apache** amb la flexibilitat pedagògica de **Moodle** ofereix un entorn que respon amb excel·lència a les demandes actuals del mercat: un sistema altament **estable, econòmic, fàcil de mantenir i escalable**.

El desplegament basat en servidors virtuals (VPS) garanteix un equilibri ideal entre inversió i rendiment, complint amb el marc legal europeu[cite: 1]. En definitiva, es consolida una **proposta de consultoria IT madura, professional, robusta** i totalment preparada per operar amb èxit en un entorn de producció real.
