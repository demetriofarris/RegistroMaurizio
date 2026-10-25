# Guida al setup — Registro Maurizio

L'app ha **due parti**:
- **Client** (la PWA che si usa dal telefono) — già pubblicata da Demetrio su GitHub Pages. Non contiene dati né chiavi.
- **Backend** (Apps Script + foglio Google) — sta **sull'account Google di Damiana** (`damianapaolucci@gmail.com`): qui vivono i dati di Maurizio e la chiave API.

> Nota: le schermate di Apps Script cambiano spesso; qui sono indicati i **percorsi dei menu**. Sono passi da fare una volta sola.

---

## A — Backend sull'account di Damiana

**Prima di iniziare**, tieni a portata:
- l'accesso a Google con l'account **damianapaolucci@gmail.com**;
- la **chiave API Anthropic** (la fornisce Demetrio);
- un **token** segreto a piacere (una parola/frase; servirà anche nell'app).

### 1. Crea il progetto Apps Script
- Vai su **https://script.google.com** (loggata come Damiana) → **Nuovo progetto**.
- Rinomina il progetto in alto a sinistra: **Registro Maurizio**.

### 2. Incolla il codice
- Nell'editor centrale (file `Codice.gs`): seleziona tutto e **cancella**, poi **incolla** il contenuto di
  `backend/registro.js` → link diretto:
  **https://raw.githubusercontent.com/demetriofarris/RegistroMaurizio/main/backend/registro.js**
- **Salva** (dischetto o Ctrl+S).

### 3. Imposta le "Proprietà script" (chiavi e configurazione)
- A sinistra: **Impostazioni progetto** (icona ⚙️).
- Scorri fino a **Proprietà script** → **Aggiungi proprietà script**. Aggiungi:

| Proprietà | Valore | Obbligatoria |
|---|---|---|
| `ANTHROPIC_API_KEY` | la chiave API Anthropic (da Demetrio) | ✅ |
| `API_TOKEN` | una parola/frase segreta a scelta | ✅ |
| `INTESTATARIO` | `Maurizio Paolucci` | facolt. (è già il default) |
| `AMMINISTRATORE` | `Damiana Paolucci` | facolt. (compare in firma) |
| `TRIBUNALE` | es. `Roma` | facolt. (testata rendiconto) |
| `RG` | es. `1234/2025 V.G.` | facolt. |
| `GIUDICE` | nome del Giudice Tutelare | facolt. |
| `LUOGO` | es. `Roma` | facolt. (riga della firma) |

- **Salva**.

### 4. Crea foglio e cartelle (una volta sola)
- Torna all'editor. Nella barra in alto, nel menù a tendina delle funzioni, scegli **`setupNuovoAmbiente`** → **Esegui**.
- Alla prima esecuzione Google chiede le **autorizzazioni**: **Rivedi autorizzazioni** → scegli l'account **Damiana** → **Avanzate** → **Vai a Registro Maurizio (non sicuro)** → **Consenti**. *(È normale: è uno script vostro, non pubblicato sullo store.)*
- A fine esecuzione, nel **Registro di esecuzione** compare il link al foglio **"Registro spese Maurizio"** (creato nel Drive di Damiana, nella cartella **Registro Maurizio**).

### 5. Pubblica la Web App
- In alto a destra: **Distribuisci** → **Nuova distribuzione**.
- Clicca l'ingranaggio accanto a "Tipo" → **App web**.
- **Esegui come**: *Me* (damianapaolucci@gmail.com).
- **Chi ha accesso**: **Chiunque**.
- **Distribuisci** → autorizza se richiesto → **copia l'URL della Web App** (finisce con `/exec`).

---

## B — Collega l'app (sul telefono di Damiana)

1. Apri il client: **https://demetriofarris.github.io/RegistroMaurizio/**
   *(per installarla: menu del browser → "Aggiungi a schermata Home")*.
2. Tocca **⚙️ Impostazioni**.
3. Incolla:
   - **URL Web App** = l'URL `/exec` copiato al punto A.5;
   - **Token API** = lo stesso `API_TOKEN` impostato al punto A.3.
4. **Salva e verifica** → deve apparire **"✅ Connesso (backend v1.0.0)"**.

Fatto. Da qui:
- **Spesa da foto / Spesa da PDF** → uscite (l'AI compila data, importo, descrizione, categoria; si rivede e si salva);
- **Aggiungi entrata** → entrate (manuale, con giustificativo facoltativo);
- **Movimenti del mese** → elenco con saldo;
- **Rendiconto** → PDF mensile o annuale (entrate, uscite, saldo, giustificativi, firma).

---

## Aggiornare il backend in futuro
Quando il codice cambia: ricopia `backend/registro.js` nell'editor Apps Script, **Salva**, poi
**Distribuisci → Gestisci distribuzioni → ✏️ (modifica) → Versione: Nuova versione → Distribuisci**.
