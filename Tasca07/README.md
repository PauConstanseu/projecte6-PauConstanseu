# 🏢 T07: Millores de Seguretat i Gestió en Active Directory

**Autor:** Pau Constanseu 
**Data:** 6 de març de 2026 

---

### 📝 Introducció i Context del Client

Malgrat que el desplegament per al *Projecte Nexus* concentra gran part dels recursos actuals, és imprescindible continuar donant suport als clients existents de l'empresa[cite: 2]. En aquest cas, **TransLògic S.A.**, que ja havia confiat prèviament en nosaltres per implementar una infraestructura basada en **Active Directory**, necessita ara completar el projecte amb una sèrie de millores clau en seguretat, gestió d’usuaris i administració del sistema[cite: 2].

La direcció de l’empresa ha expressat preocupació per diversos aspectes de la seva infraestructura:
* La seguretat i robustesa de les contrasenyes corporatives.
* La mobilitat dels treballadors en iniciar sessió entre diferents equips físics[cite: 2].
* La gestió eficient i distribució del programari corporatiu.
* La voluntat de començar a delegar certes tasques tècniques bàsiques a personal de suport sense haver de concedir privilegis complets d’administrador, mantenint així un model de seguretat més controlat[cite: 2].

---

### 🔐 Implementacions Avançades amb GPOs

Durant aquesta activitat s’han implementat diverses configuracions avançades mitjançant **Group Policy Objects (GPO)** i eines d’administració del domini[cite: 2]. Entre les accions realitzades destaquen[cite: 2]:

* **Enduriment de les polítiques de contrasenya:** Configurat per obligar l'ús de claus més complexes i segures, minimitzant els riscos d'intrusió[cite: 2].
* **Desplegament automatitzat de programari:** Dissenyat per instal·lar aplicacions de forma desatesa i automatitzada segons el departament corresponent[cite: 2].
* **Configuració de perfils mòbils (*Roaming Profiles*):** Implementat per garantir i millorar la mobilitat dels usuaris quan canvien de terminal de treball[cite: 2].
* **Redirecció de carpetes:** Establert de forma centralitzada al servidor per garantir la seguretat i integritat de les dades dels usuaris[cite: 2].

---

### ⚙️ Delegació d'Administració i Documentació

Finalment, també s’ha treballat la **delegació de tasques administratives**[cite: 2]. Això permet que un usuari del perfil de suport tècnic pugui realitzar accions concretes i de l'operativa diària —com el reinici de contrasenyes o la gestió de grups— sense tenir accés ni privilegis complets de control sobre tot el sistema[cite: 2].

Tot el procés s’ha documentat detalladament en una **memòria tècnica**[cite: 2]. Aquest lliurable està pensat exclusivament perquè el client pugui comprendre de manera senzilla les configuracions implementades i els beneficis directes que aporten a la seva infraestructura corporativa[cite: 2].
