# 📊 Annual Report

<p align="center">
  <img src="screenshot.png" alt="Annual Report">
</p>

## Panoramica

**Annual Report** è una card per Home Assistant che mostra il riepilogo annuale del tuo impianto fotovoltaico in un'unica tabella.

Utilizzando i dati storici della Dashboard Energia, consente di confrontare rapidamente l'andamento dell'anno mese per mese, visualizzando produzione, consumi, autosufficienza, costi, risparmio e ricavi da Scambio sul Posto.

La card utilizza i sensori SQL presenti nella cartella **`/sql`** del repository.

---

# ✨ Funzionalità

Per ogni mese vengono visualizzati:

- ☀️ Produzione fotovoltaica (kWh)
- 🏠 Consumo dell'abitazione (kWh)
- 📊 Autosufficienza (%)
- 💸 Costo stimato della bolletta senza fotovoltaico (€)
- 💰 Costo stimato della bolletta con fotovoltaico (€)
- 💚 Risparmio stimato (€)
- 🔵 Ricavo stimato da Scambio sul Posto (SSP) (€)

Inoltre la card include:

- Evidenziazione automatica del mese corrente
- Totali annuali
- Autosufficienza media annuale
- Aggiornamento automatico dei dati
- Grafica ottimizzata anche per smartphone e tablet

---

# 📋 Requisiti

Prima dell'installazione assicurati di avere:

- Home Assistant
- Dashboard Energia configurata
- `custom:button-card`
- Sensori SQL installati seguendo la guida presente nella cartella:

```text
/sql/
```

---

# 🚀 Installazione

## 1. Installa i sensori SQL

Prima di utilizzare questa card è necessario installare i sensori SQL.

Apri la cartella:

```text
/sql/
```

e segui il relativo **README.md**.

Questa operazione va eseguita una sola volta.

---

## 2. Riavvia Home Assistant

Dopo aver installato i sensori SQL, riavvia Home Assistant.

---

## 3. Aggiungi la card

Apri la dashboard nella quale desideri inserire la tabella.

Seleziona:

**Modifica Dashboard → Aggiungi Card → Manuale**

Copia e incolla il contenuto del file:

```text
annual-report.yaml
```

---

## 4. Personalizza i valori economici

Prima di salvare la card individua queste righe all'inizio del file:

```javascript
const costoKwh = 0.25;
const quotaFissaMese = 18.00;
const sspKwh = 0.15;
```

Sono gli unici valori che dovrai modificare.

### `const costoKwh = 0.25;`

Inserisci il **costo finale di 1 kWh acquistato**, comprensivo di tutte le componenti della bolletta.

Esempio:

```javascript
const costoKwh = 0.31;
```

---

### `const quotaFissaMese = 18.00;`

Inserisci la **quota fissa media mensile** della bolletta.

Puoi includere anche l'eventuale canone TV.

Esempio:

```javascript
const quotaFissaMese = 22.50;
```

---

### `const sspKwh = 0.15;`

Inserisci il **valore medio riconosciuto per ogni kWh immesso in rete** tramite Scambio sul Posto.

Esempio:

```javascript
const sspKwh = 0.12;
```

Una volta modificati questi tre valori, salva la card.

Tutti i calcoli economici verranno eseguiti automaticamente utilizzando i valori che hai impostato.

---

# 📝 Note

- Il mese corrente viene evidenziato automaticamente.
- Tutti i dati energetici vengono letti dalle Long-Term Statistics della Dashboard Energia.
- Il risparmio mostrato nella tabella **non include** il ricavo derivante dallo Scambio sul Posto (SSP).
- I valori economici vengono calcolati utilizzando i tre parametri configurati all'inizio della card.
- I dati dipendono dai sensori SQL installati nella cartella `/sql`.

---

# ❤️ Supporto

Hai trovato un bug o desideri proporre un miglioramento?

Puoi:

- Aprire una **GitHub Issue**
- Inviare una **Pull Request**

Se questa card ti è stata utile, lascia una ⭐ al repository.

Ogni contributo aiuta il progetto a crescere.

---

# 📄 Licenza

Distribuito con licenza **MIT**.