\# ⚡ Energy Control Center



> La dashboard più completa di \*\*HA Energy Suite\*\* per monitorare il tuo impianto fotovoltaico in tempo reale.



Energy Control Center riunisce in un'unica schermata tutte le informazioni più importanti del tuo impianto, permettendoti di controllare produzione, consumi, batteria, rete, statistiche e convenienza dei carichi senza dover passare da una dashboard all'altra.



È pensata per essere la dashboard principale dell'intera suite.



\---



\# 📸 Screenshot



!\[Energy Control Center](screenshot.png)



\---



\# ✨ Funzionalità



\- ☀️ Produzione fotovoltaica in tempo reale

\- 📈 Confronto tra produzione reale e previsione Solcast

\- 🔋 Stato di carica della batteria

\- 🏠 Consumo istantaneo dell'abitazione

\- ⚡ Import / Export rete

\- 📊 Autosufficienza energetica

\- 💰 Beneficio economico del mese

\- 🌱 Stima del contributo SSP

\- 📅 Analisi mensile dell'impianto

\- 🤖 Suggerimenti operativi intelligenti

\- 📉 Indice di performance dell'impianto

\- ⏱️ Finestra di produzione fotovoltaica utile

\- 🔄 Aggiornamento automatico in tempo reale



\---



\# ✅ Requisiti



Prima di utilizzare questa dashboard è necessario avere installato:



\- Home Assistant

\- custom:button-card

\- Solcast

\- HA Energy Suite SQL Package



\---



\# 🚀 Installazione



\## 1. Installa Solcast



Questa dashboard utilizza le previsioni generate dall'integrazione ufficiale Solcast.



Una volta configurata l'integrazione non sarà necessario modificare alcun sensore relativo alle previsioni.



\---



\## 2. Installa HA Energy Suite SQL Package



La dashboard utilizza i sensori creati dal pacchetto SQL per leggere:



\- dati mensili

\- statistiche storiche

\- benefici economici

\- import/export

\- consumi

\- produzione



Assicurati di aver installato e configurato correttamente il pacchetto SQL prima di utilizzare questa card.



\---



\## 3. Copia la card



Apri il file



```

energy-control-center.yaml

```



e copialo all'interno della tua dashboard Home Assistant.



\---



\# ⚙️ Configurazione



L'unica configurazione richiesta consiste nel sostituire i sensori del proprio inverter.



La logica della card è già completa e non richiede modifiche.



\---



\# 🔍 Come sostituire i sensori



Apri il file



```

energy-control-center.yaml

```



e utilizza la funzione di ricerca del tuo editor.



\## Windows



Ricerca



```

CTRL + F

```



Ricerca e sostituzione



```

CTRL + H

```



\---



\# 📝 Sensori da modificare



Cerca tutti i sensori che iniziano con



```

sensor.inverter\_

```



e sostituiscili con quelli del tuo impianto.



I principali sono:



| Sensore | Descrizione |

|----------|-------------|

| sensor.inverter\_pv\_power | Produzione FV istantanea |

| sensor.inverter\_load\_l1\_power | Consumo della casa |

| sensor.inverter\_internal\_ct1\_power | Import / Export rete |

| sensor.inverter\_battery | Stato di carica batteria |

| sensor.inverter\_today\_production | Produzione giornaliera |

| sensor.inverter\_today\_peak\_power | Picco di produzione |

| sensor.inverter\_today\_energy\_import | Energia acquistata oggi |



Potrebbero essere presenti altri sensori con prefisso



```

sensor.inverter\_

```



che dovranno essere sostituiti con gli Entity ID del proprio impianto.



\---



\# 🌤️ Solcast



La dashboard utilizza esclusivamente i sensori standard dell'integrazione ufficiale Solcast.



Non è necessario modificarli.



\---



\# 📦 Dipendenze



| Componente | Necessario |

|------------|:----------:|

| Solcast | ✅ |

| HA Energy Suite SQL Package | ✅ |

| Configurazione sensori inverter | ✅ |



\---



\# 💡 Suggerimenti



Per ottenere il massimo da questa dashboard si consiglia di installare anche:



\- 📊 Monthly Report

\- 📅 Annual Report



Entrambe le card utilizzano gli stessi sensori SQL e si integrano perfettamente con Energy Control Center.



\---



\# ❤️ Supporta il progetto



Se HA Energy Suite ti è stato utile, lascia una ⭐ al repository GitHub.



È il modo migliore per supportare lo sviluppo di nuove dashboard e funzionalità per la community.



\---



\# 📄 Licenza



Distribuito con la stessa licenza del progetto \*\*HA Energy Suite\*\*.

