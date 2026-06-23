# 🌅 Guida: Configurare Adaptive Lighting con Antigravity 💡

Hai mai desiderato che le luci di casa tua cambiassero colore e intensità automaticamente, imitando la luce del sole (luce fredda ed energizzante di giorno, luce calda e rilassante di notte)? Questo è esattamente ciò che fa la famosa integrazione **Adaptive Lighting**!

Normalmente, configurare questa funzione richiede pazienza, smanettamenti nei menu, aggiunta di repository esterni e qualche nozione tecnica. Ma noi abbiamo **Antigravity**, la nostra Intelligenza Artificiale personale! 🤖✨

In questa guida vedremo come far fare tutto il lavoro pesante all'IA e come creare configurazioni incredibilmente avanzate abbinando le luci ai tuoi sensori di presenza.

---

## 🛑 Prerequisiti: Hai studiato la prima guida?

Prima di iniziare questo "tutorial avanzato", assicurati di aver seguito la nostra [Guida Principale (Clicca qui)](README.md) per avere già:
1. Aperto in Antigravity la cartella `\\homeassistant\config`.
2. Attivato il **Turbo Mode**.
3. Generato il tuo **Token di Sicurezza temporaneo** su Home Assistant.
4. E ovviamente... **FATTO IL BACKUP!** 💾

---

## 🗣️ Passo 1: Far installare il componente all'IA

Adaptive Lighting è un componente aggiuntivo (*Custom Component*). Invece di impazzire con menu complicati o con HACS, chiediamo ad Antigravity di reperirlo da internet per noi in totale autonomia.

Copia-incolla questo esatto Prompt:

> "Ciao Antigravity! Voglio installare l'integrazione 'Adaptive Lighting' sul mio Home Assistant. Vai su internet, cerca la repository ufficiale GitHub dell'autore 'basnijholt/adaptive-lighting', scarica il codice sorgente della cartella `custom_components/adaptive_lighting` e copialo esattamente nella mia cartella `custom_components` qui nel nostro progetto. Quando hai finito l'installazione dei file, avvisami!"

**🔄 Riavvio necessario:** Una volta che l'IA ti confermerà l'operazione, **riavvia Home Assistant** (da *Impostazioni > Sistema > Riavvia*) affinché i nuovi file vengano letti dal sistema.

---

## ⚙️ Passo 2: Far configurare le luci base all'IA

Dopo il riavvio, chiediamo ad Antigravity di scrivere il codice per attivare l'adattamento solare sulle nostre luci del Salotto. 

Prendi questo Prompt, sostituisci il nome della tua luce (es. `light.luce_salotto`) e incollalo in chat:

> "Ora che abbiamo installato Adaptive Lighting, configura le luci del mio Salotto. Il mio Token di sicurezza temporaneo è `[INCOLLA_QUI_IL_TUO_TOKEN]` e l'indirizzo locale è `http://homeassistant.local:8123`.
> Per favore, modifica il mio `configuration.yaml` aggiungendo il setup di Adaptive Lighting per il 'Salotto'. Associalo alla luce `light.luce_salotto`. Impostalo affinché modifichi colore e luminosità solo quando la luce è GIA' accesa (non deve accendersi da sola). Applica le modifiche e riavvia Home Assistant usando il token. A riavvio completato, per la mia sicurezza, elimina il token!"

*Ora le tue luci, se le accendi dall'interruttore o dal telefono, avranno sempre la tonalità perfetta!*

---

## 🚀 Passo 3: Automazioni Avanzate con i Sensori (Il vero potenziale!)

Adaptive Lighting dà il meglio di sé quando è abbinato ai sensori intelligenti. Invece di usare gli interruttori a muro, la luce si accende da sola quando entri, ed essendo governata da Adaptive Lighting, *avrà l'intensità perfetta in base all'orario* (niente flash accecanti di notte!).

Ecco una serie di Prompt dettagliatissimi per chiedere ad Antigravity di creare automazioni mozzafiato per te.

### 🚶‍♂️ Esempio A: Corridoio con Sensore di Movimento (Sonoff SNZB-03)
Il **Sonoff SNZB-03** è un classico sensore a infrarossi che rileva il movimento netto. È perfetto per le zone di passaggio come corridoi o scale, dove stai poco tempo.

> "Antigravity, voglio creare un'automazione per il mio corridoio. Ho un sensore di movimento (Sonoff SNZB-03) che in Home Assistant si chiama `binary_sensor.movimento_corridoio` e una luce chiamata `light.luce_corridoio` (che hai già agganciato ad Adaptive Lighting).
> Crea un'automazione nel mio file `automations.yaml` che faccia questo:
> 1. Quando il sensore rileva un movimento, accendi la luce del corridoio (Adaptive Lighting regolerà subito il colore giusto in base al sole).
> 2. Quando il sensore smette di rilevare movimento da almeno 2 minuti continui, spegni la luce.
> Usa il mio token `[INCOLLA_TOKEN]` all'indirizzo `http://homeassistant.local:8123` per ricaricare le automazioni in tempo reale senza riavviare tutto il sistema."

### 🧍‍♂️ Esempio B: Studio/Salotto con Sensore di Presenza (Sonoff SNZB-06P)
A differenza del movimento, il **Sonoff SNZB-06P** è un sensore radar a microonde che rileva la *presenza* umana. Capisce se sei nella stanza anche se sei perfettamente immobile sul divano a leggere o guardare la TV.

> "Antigravity, voglio configurare un'automazione ultra-avanzata per il mio Salotto usando un sensore di presenza radar (Sonoff SNZB-06P). In Home Assistant il sensore si chiama `binary_sensor.presenza_salotto` e la luce principale è `light.luce_salotto` (già gestita dal tuo Adaptive Lighting).
> Crea o modifica il file `automations.yaml` con questa esatta logica:
> 1. Appena entro nel Salotto (presenza rilevata), accendi la luce.
> 2. Mantieni la luce accesa finché rileva la mia presenza (anche se sono fermo immobile per ore).
> 3. Quando esco dalla stanza e il sensore indica 'Non Rilevato' per più di 1 minuto continuo (per evitare falsi allarmi), spegni la luce.
> Al termine, ricarica le automazioni con il mio token `[INCOLLA_TOKEN]` all'indirizzo `http://homeassistant.local:8123`."

### 😴 Esempio C: Attivare la Modalità Sonno (Sleep Mode)
Adaptive Lighting ha una funzione pazzesca chiamata "Sleep Mode". Quando è attiva, le luci si accendono a una luminosità bassissima (es. 2%) e con una tonalità caldissima (rossastra) per non svegliarti o darti fastidio agli occhi quando vai in bagno di notte.

> "Antigravity, ho già Adaptive Lighting configurato per la luce del bagno (`light.luce_bagno`). Voglio sfruttare la sua fantastica funzione 'Sleep Mode'. 
> Modifica la mia configurazione per attivare la 'Sleep Mode' in modo automatico su quell'entità dalle 23:30 alle 07:00 del mattino. Durante queste ore notturne, se entro in bagno (tramite sensore o interruttore), la luce deve accendersi al massimo al 5% di luminosità e con una tonalità caldissima. Alle 07:01, deve tornare alla gestione normale del sole.
> Applica il codice e ricarica il sistema con il mio token `[INCOLLA_TOKEN]` all'indirizzo `http://homeassistant.local:8123`."

### ✋ Esempio D: Ignorare Adaptive Lighting temporaneamente (Takeover)
Cosa succede se di notte (quando la luce è impostata per essere fioca e calda) hai bisogno di cercare un oggetto perso e vuoi sparare la luce bianca al 100%? Se provi ad alzarla manualmente, Adaptive Lighting te la riabbasserà subito sotto il naso! Per evitarlo, c'è la funzione "Take Over" (Prendi il Controllo).

> "Antigravity, voglio attivare la funzione 'Take Over' di Adaptive Lighting per il Salotto.
> Modifica il mio file di configurazione YAML per abilitare il parametro 'take_over_control'. Fai in modo che se io modifico manualmente la luminosità o il colore di `light.luce_salotto` (dal telefono o con un telecomando fisico), Adaptive Lighting deve 'arrendersi', capire che ho preso io il comando manuale, e smettere di modificarla in automatico per il resto della serata, finché non spengo e riaccendo la luce.
> Fai le modifiche e ricarica il tutto con il mio token `[INCOLLA_TOKEN]` all'indirizzo `http://homeassistant.local:8123`."

---

## 🎯 Conclusioni

Con Antigravity e Adaptive Lighting non stai semplicemente accendendo e spegnendo delle lampadine: stai creando un vero e proprio ecosistema vivo e intelligente!
La tua casa ora reagisce non solo alla tua presenza (che tu stia correndo nel corridoio o sia fermo a leggere sul divano), ma anche all'ora del giorno e all'angolazione del sole, garantendoti sempre il massimo del comfort visivo senza mai farti toccare un interruttore!
