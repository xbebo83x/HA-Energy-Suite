<p align="center">
  <img src="assets/ha-energy-suite-banner.png" alt="HA Energy Suite">
</p>

<p align="center">

![Version](https://img.shields.io/badge/version-v0.1.0--alpha-34C759)
![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Compatible-41BDF5?logo=homeassistant&logoColor=white)
![License](https://img.shields.io/github/license/xbebo83x/HA-Energy-Suite)
![Stars](https://img.shields.io/github/stars/xbebo83x/HA-Energy-Suite?style=social)

</p>

---

# ☀️ HA Energy Suite

**HA Energy Suite** è un progetto **Open Source** dedicato a **Home Assistant** che raccoglie dashboard, card e strumenti per il monitoraggio energetico degli impianti fotovoltaici.

Nasce dall'esperienza maturata sul mio impianto reale con un obiettivo molto semplice:

> **Realizzare dashboard moderne, modulari e facili da installare, permettendo a chiunque di ottenere un sistema professionale in pochi minuti.**

Ogni componente è progettato per essere semplice da configurare, facilmente personalizzabile e completamente indipendente dagli altri moduli.

---

# ✨ Caratteristiche

- 📊 Dashboard moderne e curate
- ⚡ Sensori SQL condivisi
- 🏠 Basato sulla Dashboard Energia di Home Assistant
- 🧩 Architettura completamente modulare
- 🔧 Installazione guidata
- 📚 Documentazione dettagliata
- ❤️ Completamente Open Source

---

# 🚧 Stato del progetto

## Versione attuale

> **v0.1.0 Alpha**

HA Energy Suite è ancora nelle prime fasi di sviluppo, ma è già perfettamente utilizzabile.

Ogni nuova versione introdurrà nuovi moduli mantenendo sempre gli stessi principi:

- semplicità;
- modularità;
- configurazione minima;
- documentazione completa.

---

# 📦 Requisiti

A seconda del modulo scelto potrebbero essere necessari:

- Home Assistant;
- Dashboard Energia configurata;
- `custom:button-card`;
- Sensori SQL di HA Energy Suite.

Ogni modulo include un proprio README con tutte le istruzioni necessarie.

---

# 🚀 Prima installazione

Se è la prima volta che utilizzi **HA Energy Suite**, ti consigliamo di seguire questo ordine.

## 1️⃣ Configura i sensori SQL

Apri la cartella:

```text
sql/
```

e segui la guida contenuta nel relativo `README.md`.

Questa operazione va eseguita **una sola volta**.

---

## 2️⃣ Riavvia Home Assistant

Dopo aver completato la configurazione dei sensori SQL, riavvia Home Assistant.

---

## 3️⃣ Scegli il modulo che desideri installare

Ogni dashboard è completamente indipendente dalle altre.

Puoi installare soltanto quelle che ti interessano.

---

## 4️⃣ Segui il README del modulo

Ogni cartella contiene una guida dettagliata con tutti i passaggi necessari.

In pochi minuti avrai la tua dashboard completamente funzionante.

---

# 📂 Struttura del progetto

```text
HA-Energy-Suite
│
├── .github/
├── assets/
├── cards/
│
├── docs/
├── screenshots/
├── sql/
│
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── ROADMAP.md
├── BRAND.md
└── LICENSE
```

---

# 📦 Moduli disponibili

| Modulo | Stato | Descrizione |
|---------|:----:|-------------|
| 📊 Annual Report | ✅ Disponibile | Report annuale con statistiche energetiche mese per mese |
| 📈 Monthly Report | ✅ Disponibile | Analisi completa del mese corrente con produzione, consumi, autosufficienza, costi e risparmio |
| 🔋 Battery Card | 🚧 In sviluppo | Dashboard dedicata al monitoraggio della batteria di accumulo |

Nuovi moduli verranno aggiunti progressivamente mantenendo la stessa filosofia del progetto.

---

# 💡 Filosofia del progetto

HA Energy Suite nasce con un'idea molto semplice.

> **Installa solo ciò che ti serve.**

Ogni modulo è completamente indipendente dagli altri e può essere installato senza modificare il resto della dashboard.

I sensori SQL rappresentano il motore dati condiviso del progetto e vengono installati una sola volta.

Successivamente potrai scegliere liberamente quali dashboard utilizzare.

Nessun framework.

Nessuna installazione complicata.

Solo strumenti modulari progettati per Home Assistant.

---

# 🗺️ Roadmap

Il progetto è in continua evoluzione.

Tra le funzionalità previste nelle prossime versioni:

- 🔋 Battery Dashboard
- ☀️ Solar Overview
- 📈 Energy Statistics
- 💰 Dashboard economica
- 📊 Confronti annuali
- 📱 Dashboard ottimizzate per smartphone e tablet
- ⚙️ Installazione sempre più automatizzata

Per conoscere tutti gli sviluppi previsti consulta il file **ROADMAP.md**.

---

# ❤️ Come contribuire

HA Energy Suite è un progetto Open Source sviluppato nel tempo libero.

Puoi contribuire in molti modi:

- ⭐ Lasciando una stella al repository
- 🐞 Segnalando bug
- 💡 Proponendo nuove idee
- 🔧 Inviando una Pull Request
- ❤️ Supportando il progetto tramite GitHub Sponsors

Ogni contributo, piccolo o grande, aiuta il progetto a crescere.

---

# ❤️ Supporta il progetto

Se HA Energy Suite ti è stato utile e desideri supportarne lo sviluppo, puoi farlo tramite **GitHub Sponsors**.

Il tuo supporto mi permette di dedicare più tempo allo sviluppo di nuove dashboard, al miglioramento della documentazione e al supporto della community.

Anche lasciare una ⭐ al repository è un gesto semplice ma molto importante.

Grazie per il tuo supporto! ☀️

---

# 📄 Licenza

Questo progetto è distribuito con licenza **MIT**.