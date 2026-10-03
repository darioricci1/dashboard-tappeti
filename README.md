# Dashboard commerciale per Ferreira de Sá

Idea nata dalla chiacchierata del 2 ottobre 2026 con Gabriele Contin, compagno del
master, che segue l'implementazione dei processi commerciali in Ferreira de Sá,
tappeti di design. A che punto è: c'è un
prototipo con dati finti da fargli vedere, online su
https://ferreira-funnel.vercel.app (progetto Vercel `ferreira-funnel`). Lui ha detto che, se
trova il pilota, l'azienda può pagare delle ore di lavoro per farlo insieme.

## Cosa è emerso

- **Come vendono.** Pochi negozi propri, che costano troppo nelle vie visibili delle
  grandi città. Si passa da showroom e cataloghi presso altri, dalla distribuzione
  specializzata (rivenditori di mobili, Rinascente) e soprattutto dai progetti: un
  architetto o un designer mette il tappeto nel suo progetto. C'è anche un canale a
  parte, la produzione per grandi marchi.
- **Il funnel.** Su Dynamics tracciano visite, contatti, lead, opportunità che
  diventano progetti, preventivi e ordini. Ogni contatto può avere più progetti, e un
  progetto non sempre lo compra lo stesso rivenditore. I tempi vanno da tre mesi per i
  progetti piccoli a due anni per quelli grandi all'estero.
- **I KPI di partenza.** Fatturato, numero di visite, numero di progetti e il tasso
  di conversione (da contatti a progetti, da progetti a fatturato), per ora come
  indicatore e non ancora come obiettivo. L'idea: più progetti a parità di
  conversione. Se la conversione scende, vuol dire che si caricano progetti finti
  per fare numero.
- **Cosa manca.** Una vista del funnel per area geografica e per canale (retail,
  progetti, online, produzione per marchi): oggi non ce l'hanno. Un primo tentativo
  di visualizzazione non era venuto bene.

## Le idee aggiunte nella chiacchierata

- **Clienti nuovi o già clienti.** Separare i progetti fatti con chi ha già
  comprato da quelli con contatti nuovi, e guardare la conversione di ciascuno. Chi
  fa cinquanta progetti con lo stesso architetto e ne vince uno va visto subito.
- **Il richiamo dopo il preventivo.** Dynamics oggi manda il promemoria dopo un
  numero di giorni scelto a sensazione. Con i dati si può vedere a quanti giorni dal
  preventivo il richiamo converte di più (per esempio 10% a tre giorni, 7% a una
  settimana) e fissare lì il promemoria. Ai commerciali si dà un consiglio basato
  sui numeri invece di un «devi fare di più», e si sentono meno giudicati.

## Il prototipo

`public/index.html` è tutto il sito: una pagina sola, senza server, che si apre anche
dal disco. Ha i filtri per canale, area,
commerciale e periodo (fino all'ultimo mese), le tessere in alto con il confronto
col migliore commerciale su ciascun KPI (il migliore cambia da KPI a KPI, e su
conversione e valore medio conta solo chi ha almeno 5 progetti), i grafici dei 12
mesi (con la media della squadra tratteggiata quando si guarda un commerciale), il funnel con la percentuale tra un
gradino e l'altro, il confronto clienti nuovi o già clienti, la conversione per
giorni di richiamo e la tabella per commerciale. I dati sono finti e generati nella
pagina, sempre uguali.

## Per farla vera

1. Farsi dare dall'azienda un'estrazione da Dynamics (anche un Excel all'inizio):
   attività di visita, lead, opportunità con canale e area, offerte con data di
   invio, attività di richiamo con data, ordini con importo, e per ogni account se
   aveva già comprato.
2. Sostituire il generatore di dati finti con la lettura di quell'estrazione.
3. Poi collegarsi a Dynamics direttamente (Dataverse Web API), oppure lasciare la
   dashboard dentro Power BI se l'azienda lo usa già.

Da chiarire con Gabriele: se usano Dynamics 365 Sales o un altro modulo, chi
pagherebbe il pilota e quante ore.

Il sito si ricostruisce solo quando cambia questa cartella.
