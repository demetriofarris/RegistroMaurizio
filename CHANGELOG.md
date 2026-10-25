# Changelog — Registro Maurizio

App per il rendiconto di un'amministrazione di sostegno (entrate + uscite).
Fork adattato di ClaudeScontrini. Date in formato GG/MM/AAAA.

## v1.1.0 — 25/10/2026
- In **Impostazioni** due link rapidi: **📖 Manuale d'uso** e **🔧 Guida setup**.
- **Spesa manuale**: nuovo tasto per inserire un'uscita completamente a mano (senza scansione), con giustificativo facoltativo.
- **Forma di pagamento**: nuovo campo (Contanti, Bancomat/Carta, Bonifico, Assegno, Addebito diretto, Altro) su entrate, uscite e in modifica; per gli scontrini scansionati viene dedotta dall'AI. Compare nel dettaglio del rendiconto.

## v1.0.0 — 25/10/2026
- Prima versione. Registro unico **entrate/uscite** su Google Sheet "Registro spese Maurizio".
- **Uscite**: foto o PDF dello scontrino → l'AI (Claude) compila data, importo, descrizione e categoria; si rivede e si salva.
- **Entrate**: inserimento manuale (data, importo, fonte, categoria) con giustificativo facoltativo.
- **Movimenti del mese**: elenco con importi colorati (verde entrate / rosso uscite) e **saldo del mese**.
- **Rendiconto PDF** mensile e annuale: tabella movimenti con colonne Entrate/Uscite, **saldo iniziale → finale**, riepilogo per categoria, giustificativi, riferimenti del procedimento e blocco firma dell'amministratore di sostegno.
- **Statistiche**: entrate, uscite, saldo e uscite per categoria, per mese o anno.
- Categorie dedicate ADS (sanitarie, alimentari, casa/utenze, assistenza/badante, ecc.).
- PWA installabile; resilienza su rete debole (retry letture, recupero rendiconto su timeout).
