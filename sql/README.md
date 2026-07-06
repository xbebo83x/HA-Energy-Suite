# 📊 Sensori SQL

Questa cartella contiene il file:

```text
sql/energy-sql.yaml
```

Questo file crea i sensori SQL usati dalle card che richiedono dati storici della Dashboard Energia di Home Assistant.

Le card restano indipendenti.  
Il file SQL va installato solo se la card che vuoi usare lo richiede.

---

# ❓ A cosa serve questo file?

Home Assistant salva lo storico energetico nel proprio database interno.

I sensori SQL leggono quel database e ricostruiscono dati come:

- produzione fotovoltaica mensile;
- consumo casa mensile;
- energia acquistata dalla rete;
- energia immessa in rete;
- dati utili per report mensili e annuali.

Questi sensori non leggono direttamente inverter, contatori o dispositivi fisici.  
Leggono i dati già registrati dalla Dashboard Energia di Home Assistant.

---

# 📋 Requisiti

Prima di installare questo file devi avere:

- Home Assistant funzionante;
- Dashboard Energia già configurata;
- dati storici presenti nella Dashboard Energia;
- accesso al file `configuration.yaml`;
- accesso a Visual Studio Code Server, File Editor o Terminale.

---

# 📁 Struttura del repository

Nel repository il file si trova qui:

```text
sql/
├── energy-sql.yaml
└── README.md
```

Le card invece si trovano nella cartella:

```text
cards/
├── annual-report/
├── energy-control-center/
└── monthly-report/
```

Le card sono solo interfacce grafiche.  
Non vanno copiate dentro `configuration.yaml`.

---

# 🚀 Installazione SQL

## Passo 1 - Crea la cartella SQL in Home Assistant

In Home Assistant crea questa cartella:

```text
/config/sql/
```

Se esiste già, puoi usare quella.

---

## Passo 2 - Copia il file

Copia il file del repository:

```text
sql/energy-sql.yaml
```

dentro Home Assistant in:

```text
/config/sql/energy-sql.yaml
```

La struttura finale deve essere questa:

```text
/config/
├── configuration.yaml
└── sql/
    └── energy-sql.yaml
```

---

## Passo 3 - Richiama il file in `configuration.yaml`

Apri:

```text
/config/configuration.yaml
```

Aggiungi questa riga:

```yaml
sql: !include sql/energy-sql.yaml
```

La riga deve stare al livello principale del file, senza spazi davanti.

Esempio corretto:

```yaml
default_config:

frontend:
  themes: !include_dir_merge_named themes

automation: !include automations.yaml
script: !include scripts.yaml
scene: !include scenes.yaml

sql: !include sql/energy-sql.yaml
```

Esempio sbagliato:

```yaml
homeassistant:
  sql: !include sql/energy-sql.yaml
```

Esempio sbagliato:

```yaml
sensor:
  sql: !include sql/energy-sql.yaml
```

---

# ⚠️ Importante

Il file `energy-sql.yaml` è pensato per essere richiamato così:

```yaml
sql: !include sql/energy-sql.yaml
```

Per questo motivo dentro `energy-sql.yaml` non deve esserci una seconda voce iniziale:

```yaml
sql:
```

Il file deve contenere direttamente l'elenco dei sensori SQL.

Esempio corretto dentro `energy-sql.yaml`:

```yaml
- name: FV 2026 01 Produzione DB
  unique_id: fv_2026_01_produzione_db
  db_url: sqlite:////config/home-assistant_v2.db
  query: >
    ...
```

---

# ⚠️ Se hai già una sezione `sql:`

Nel file `configuration.yaml` può esserci una sola voce `sql:`.

Questo è corretto:

```yaml
sql: !include sql/energy-sql.yaml
```

Questo è sbagliato:

```yaml
sql: !include sql/energy-sql.yaml
sql: !include altri_sensori.yaml
```

Se hai già una configurazione SQL, devi unire i sensori in un unico file oppure copiare il contenuto di `energy-sql.yaml` nel file SQL che stai già usando.

---

# 🔎 Trovare i tuoi `metadata_id`

Ogni impianto Home Assistant ha numeri diversi.

Nel file `energy-sql.yaml` devi sostituire i `metadata_id` con quelli del tuo impianto.

## Metodo con Terminale

Apri il Terminale di Home Assistant e digita:

```bash
sqlite3 /config/home-assistant_v2.db
```

Poi esegui questa query:

```sql
SELECT id, statistic_id
FROM statistics_meta
ORDER BY statistic_id;
```

Vedrai un elenco simile a questo:

```text
265|sensor.inverter_total_production
269|sensor.inverter_total_energy_import
270|sensor.inverter_total_energy_export
274|sensor.inverter_total_load_consumption
```

Il numero a sinistra è il `metadata_id`.

Per uscire dal database scrivi:

```text
.quit
```

---

# 🧩 Quali sensori devi trovare

Nel file devi individuare i `metadata_id` relativi a:

```text
Produzione FV
Consumo Casa
Import Rete
Export Rete
```

Di solito corrispondono ai sensori usati nella Dashboard Energia di Home Assistant.

---

# 🤖 Aiuto con ChatGPT

Se non vuoi modificare il file a mano, puoi fare così:

1. esegui la query sul database;
2. copia tutto l'elenco dei risultati;
3. copia anche il contenuto di `energy-sql.yaml`;
4. chiedi a ChatGPT:

```text
Questo è l'elenco dei miei sensori Home Assistant e questo è il file energy-sql.yaml.
Sostituisci i metadata_id con quelli corretti per Produzione FV, Consumo Casa, Import Rete ed Export Rete.
Non modificare altro.
```

Poi incolla il file corretto in:

```text
/config/sql/energy-sql.yaml
```

---

# ✅ Controllo configurazione

Prima di riavviare Home Assistant vai in:

```text
Impostazioni → Sistema → Controlla configurazione
```

Se non ci sono errori, puoi riavviare.

---

# 🔄 Riavvio

Riavvia Home Assistant.

Dopo il riavvio, i sensori SQL verranno creati automaticamente.

---

# ✅ Verifica finale

Vai in:

```text
Impostazioni → Dispositivi e servizi → Entità
```

Cerca i sensori SQL creati dal file.

Se i sensori esistono e mostrano un valore, la configurazione è corretta.

---

# ❌ Problemi comuni

## I sensori non compaiono

Controlla che:

- il file sia davvero in `/config/sql/energy-sql.yaml`;
- in `configuration.yaml` ci sia questa riga:

```yaml
sql: !include sql/energy-sql.yaml
```

- la riga `sql:` sia senza spazi davanti;
- Home Assistant sia stato riavviato.

---

## Home Assistant segnala errore YAML

Controlla che:

- non esistano due sezioni `sql:` in `configuration.yaml`;
- il file `energy-sql.yaml` non inizi con `sql:`;
- l'indentazione del file non sia stata modificata.

---

## I sensori sono `unavailable`

Di solito significa che i `metadata_id` non sono corretti.

Ripeti la query:

```sql
SELECT id, statistic_id
FROM statistics_meta
ORDER BY statistic_id;
```

e controlla di aver scelto i sensori giusti.

---

# 💡 Consiglio

Prima di modificare i file di configurazione fai sempre un backup di Home Assistant.

---

# 📌 Riassunto rapido

```text
1. Copia sql/energy-sql.yaml in /config/sql/energy-sql.yaml
2. Aggiungi in configuration.yaml:
   sql: !include sql/energy-sql.yaml
3. Sostituisci i metadata_id con quelli del tuo impianto
4. Controlla la configurazione
5. Riavvia Home Assistant
6. Installa la card che richiede questi sensori SQL
```
