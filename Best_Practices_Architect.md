# 🏛️ Architettura Domotica: Best Practices (Severamente Consigliate)

Se sei arrivato fin qui, significa che hai superato la fase del "fammi accendere una lampadina" e sei pronto per fare sul serio. 

In questa guida non troverai un tono rassicurante. Sono qui, in veste di **Software Architect**, per dirti che il 90% delle installazioni di Home Assistant là fuori è un disastro inenarrabile di codice non mantenibile, file YAML chilometrici e automazioni duplicate che collasseranno al primo aggiornamento.

Se vuoi che la tua casa intelligente sia **scalabile, affidabile e professionale**, devi smettere di "pasticciare" e iniziare a istruire Antigravity affinché applichi regole architetturali rigorose sin dal primo giorno.

Ecco le istruzioni esatte (Prompt) da impartire all'IA per configurare il tuo sistema come farebbe un ingegnere del software.

---

## 📏 Regola 1: La Nomenclatura (Naming Convention) è Legge

Niente più `light.luce1` o `switch.presa_divano`. In un sistema professionale, se l'ID di un'entità non ti dice *esattamente* dov'è e cosa fa, hai fallito.

**Il tuo primo ordine ad Antigravity deve essere l'applicazione di una Naming Convention rigorosa.**

> **PROMPT DA INVIARE ALL'IA:**
> "Ascolta Antigravity: da questo momento in poi, per ogni entità che creerai o rinominerai nel mio Home Assistant, esigo l'applicazione di questa Nomenclatura Standard Internazionale: `<dominio>.<stanza>_<tipo>_<posizione>`. 
> Ad esempio: `light.salotto_soffitto_principale`, oppure `binary_sensor.bagno_movimento_doccia`. 
> Analizza il mio intero `configuration.yaml` e dimmi se ci sono entità che violano questa regola. In caso affermativo, prepara un piano per rinominarle e sistemare i riferimenti nelle automazioni. Non tollero eccezioni."

---

## 📦 Regola 2: Separazione delle Competenze (Packages)

Inserire centinaia di righe di codice dentro il singolo file `configuration.yaml` è una pratica dilettantistica e inaccettabile. Se un'area del sistema si rompe, deve essere isolata. 

Obbliga l'IA ad attivare l'infrastruttura a **Packages** (Pacchetti).

> **PROMPT DA INVIARE ALL'IA:**
> "Antigravity, il mio `configuration.yaml` sta diventando un monolite inaccettabile. 
> 1. Crea una cartella chiamata `packages` nella directory `config`.
> 2. Nel `configuration.yaml`, inserisci la direttiva `homeassistant: packages: !include_dir_named packages`.
> 3. Da oggi in poi, non aggiungerai MAI PIÙ codice direttamente in `configuration.yaml`. Ogni nuovo sistema (es. sicurezza, riscaldamento, illuminazione) dovrà avere il suo file YAML dedicato all'interno della cartella `packages` (es. `packages/security.yaml`, `packages/climate.yaml`). 
> 4. Esegui subito il refactoring delle mie luci attuali spostandole in `packages/lighting.yaml`. Riavvia il sistema col token `[INCOLLA_TOKEN]`."

---

## 🧬 Regola 3: L'uso Tassativo dei Blueprint (Evitare la duplicazione)

Hai 5 stanze con 5 sensori di movimento? Se fai scrivere all'IA 5 automazioni diverse, stai creando *Debito Tecnico*. Se un giorno vorrai cambiare il tempo di spegnimento, dovrai farle modificare tutte e 5.

I professionisti usano i **Blueprint** (Modelli).

> **PROMPT DA INVIARE ALL'IA:**
> "Antigravity, devo automatizzare l'accensione delle luci con i sensori di movimento in 5 stanze diverse.
> Ti proibisco severamente di creare 5 automazioni YAML separate.
> Voglio che tu cerchi su internet un **Blueprint ufficiale** per l'accensione delle luci su movimento (motion-activated light) o che ne scriva uno tu da zero, salvandolo nella cartella `blueprints/automation/custom/`.
> Dopodiché, nel mio file delle automazioni, limiterai il codice esclusivamente a richiamare quel Blueprint passandogli le variabili diverse per ogni stanza (il sensore e la luce). L'architettura deve essere DRY (Don't Repeat Yourself). Esegui il lavoro e ricarica le automazioni."

---

## 🔒 Regola 4: Gestione dei Segreti (`secrets.yaml`)

Non voglio MAI vedere una password, un token, un indirizzo IP esterno o una chiave API scritta in chiaro nei file di configurazione o nelle automazioni. Se lo fai, stai compromettendo la sicurezza dell'intera infrastruttura.

> **PROMPT DA INVIARE ALL'IA:**
> "Antigravity, verifica tutti i miei file YAML. Se trovi password, coordinate GPS, token API o webhook in chiaro, spostali immediatamente all'interno del file `secrets.yaml`. 
> Nei file di configurazione dovrai utilizzare esclusivamente il richiamo `!secret nome_del_segreto`. Fai un audit di sicurezza adesso e correggi qualsiasi violazione di questa policy, poi riavvia Home Assistant usando il token temporaneo `[INCOLLA_TOKEN]`."

---

## 📢 Regola 5: Notifiche Centralizzate (Wrapper)

Quando imposti degli avvisi sul tuo cellulare (es. "Allarme scattato", "Lavatrice finita"), non far scrivere all'IA il comando diretto `notify.mobile_app_tuo_telefono` in ogni singola automazione. Se domani cambi telefono, dovrai riscrivere metà del sistema.

Costruisci un singolo Script che funge da "smistatore" (Wrapper).

> **PROMPT DA INVIARE ALL'IA:**
> "Antigravity, crea un nuovo script chiamato `script.notifica_globale`. Questo script dovrà accettare due variabili: `titolo` e `messaggio`. 
> All'interno dello script, indirizza la notifica a `notify.mobile_app_il_mio_iphone` (o al dispositivo che ti indico).
> Da questo momento in poi, in tutte le future automazioni che creerai per me, non chiamerai mai direttamente il mio telefono. Chiamerai ESCLUSIVAMENTE `script.notifica_globale` passandogli il testo. Questo garantirà la massima astrazione hardware. Ricarica gli script col token `[INCOLLA_TOKEN]`."

---

## 📡 Regola 6: Osservabilità, Telemetria e Health Checks

Un professionista non si accorge che il sistema è rotto perché la luce non si accende; se ne accorge *prima*. Un sistema non monitorato è un sistema abbandonato.

> **PROMPT DA INVIARE ALL'IA:**
> "Antigravity, esigo la creazione di un pacchetto di telemetria. Crea il file `packages/health_check.yaml`.
> 1. Inserisci i sensori di sistema (System Monitor) per monitorare l'uso di RAM, CPU e lo spazio su disco del mio server Home Assistant.
> 2. Crea un'automazione che mi invii un allarme critico (usando `script.notifica_globale`) se lo spazio su disco scende sotto il 10% o se l'uso della RAM supera il 95% per più di 10 minuti.
> 3. Crea una seconda automazione che faccia la scansione di tutti i miei sensori a batteria (es. Zigbee) ogni giorno alle 12:00 e mi notifichi se c'è un dispositivo con batteria inferiore al 15% o che risulta 'Indisponibile' (Unavailable) da più di 2 ore.
> Attiva questi monitoraggi e riavvia usando il token `[INCOLLA_TOKEN]`."

---

## ⚡ Regola 7: Idempotenza e Disaster Recovery (Gestione Blackout)

Le automazioni dilettantesche partono da un trigger (es. "Se si fa buio, accendi"). Ma cosa succede se salta la corrente esattamente al tramonto e torna in piena notte? Il trigger viene perso, il sistema non sa cosa fare, e la casa resta al buio.
Il codice professionale deve essere **Idempotente** e saper gestire il ripristino post-avvio.

> **PROMPT DA INVIARE ALL'IA:**
> "Antigravity, da oggi in poi ogni automazione basata su orari o sul sole deve includere logiche di Disaster Recovery.
> Aggiungi sempre un trigger secondario basato su `homeassistant.start` (riavvio del sistema).
> Nelle condizioni (Conditions) dell'automazione, assicurati che lo stato venga ricalcolato in modo idempotente. Esempio: se il sistema si accende dopo un blackout, e l'orario attuale è successivo al tramonto ma precedente all'alba, l'automazione deve scattare e riaccendere le luci esterne che si sarebbero dovute accendere mentre mancava la corrente. 
> Analizza le mie automazioni attuali e applica il paradigma di Disaster Recovery ovunque manchi. Al termine, ricarica le automazioni."

---

## ⚖️ Conclusione dell'Architetto

Se impartirai questi ordini fin dal primo giorno, Antigravity non solo scriverà il codice per te, ma lo farà creando un'infrastruttura **Enterprise-grade**. 

La tua domotica sarà robusta, pulita, sicura e, soprattutto, a prova di manutenzione. Non accontentarti di un sistema che "semplicemente funziona". Esigi un sistema ingegnerizzato.
