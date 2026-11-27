# Changelog
Tutte le modifiche rilevanti di iSINAPSi™ PCXX1™. Formato ispirato a [Keep a Changelog](https://keepachangelog.com/it-IT/1.1.0/); versioni secondo [Semantic Versioning](https://semver.org/lang/it/).

## [1.4.0-beta12] – 2026-11-28 · non pubblicata

### Licenza e modulo di autorizzazione
- Licenza 3.0: tolta la nota «testo da far rivedere a un avvocato prima della pubblicazione» (in testa e dopo l'approvazione specifica) e, al punto 12.9, l'inciso «da sottoporre a revisione legale» riferito al modulo, dopo la verifica di un professionista sul testo pubblicato con la beta11. Nessun'altra modifica alle clausole: la versione resta 3.0 e chi l'ha già accettata non deve accettarla di nuovo.
- Finestra del primo avvio: tolta la frase «Testo da far rivedere a un avvocato».
- Modulo di autorizzazione all'intervento (PDF, HTML, CSV e modulo vuoto): tolta la dicitura «modello da sottoporre a revisione legale»; restano firma fissa, numero di pagina e contenuti invariati.

### Test
- 327 test automatici su Linux; i test di licenza e modulo verificano ora che le due note non compaiano più.

## [1.4.0-beta11] – 2026-11-27 · non pubblicata

### Modulo di autorizzazione all'intervento (Lite e Pro)
- AUDIT E REPORT › **«Modulo di autorizzazione da far firmare al cliente...»**: modulo compilabile, esportabile in **PDF** (A4, scritto direttamente nel file scelto), **HTML** stampabile e **CSV**, con la notifica «Apri file» / «Apri cartella» della beta10 (nessuna apertura automatica).
- Contenuto: parti (fornitore, tecnico, cliente, referente), **dispositivo con i dati letti dal PC** (produttore, modello, numero di serie, sistema operativo, nome del computer, data e ora; lettura WMI in sola lettura, modificabile, pulsante «Rileggi dal PC»), **operazioni autorizzate** selezionabili (11 voci più «Altro»), **dichiarazione di backup o rinuncia espressa**, responsabilità e manleva **entro l'art. 1229 c.c.** (mai esclusi dolo o colpa grave; fatti salvi i diritti del consumatore, D.Lgs. 206/2005), **informativa GDPR** (art. 13: titolare, finalità e basi giuridiche art. 6, minimizzazione, destinatari, conservazione, diritti artt. 15-22, reclamo al Garante), **Allegato B facoltativo** di nomina a responsabile del trattamento (art. 28, par. 3, lett. a-h) per i clienti organizzazione, **sezione NIS2 facoltativa** (D.Lgs. 138/2024: art. 6 soggetti essenziali/importanti, art. 24 misure e catena di approvvigionamento, art. 25 notifica al CSIRT Italia a carico del cliente, tracciabilità con codice intervento), **Allegato A** con il registro della sessione e la sua impronta SHA-256, riferimento a un report allegato (nome e SHA-256), firme di cliente e tecnico con luogo e data, approvazione specifica delle clausole (artt. 1341-1342 c.c.).
- Campi vuoti stampati come righe da compilare a mano; timbro del tecnico solo se impostato; firma fissa; nota a piè di pagina **«MODELLO DA SOTTOPORRE A REVISIONE LEGALE»**.

### Personalizzazione: Azienda, Tecnico, Cliente
- In Informazioni › Personalizzazione (accanto al timbro) e nella pagina AUDIT E REPORT: tre campi facoltativi **Azienda**, **Tecnico** e **Cliente**, usati nelle intestazioni di tutti gli export (CSV, HTML, PDF) e per precompilare il modulo. Se vuoti non compare nessuna riga né segnaposto (stessa regola del timbro).
- Il Cliente vale per il singolo intervento: pulsante **«Nuovo cliente»** che lo svuota; con «Ricorda al riavvio» spento il cliente non viene salvato.

### EULA 3.0 e doppia accettazione
- Licenza 3.0: AS IS, nessuna garanzia, esclusione per danni diretti e indiretti, perdita di dati, uso improprio o non autorizzato nei limiti dell'art. 1229 c.c.; uso riservato a tecnici qualificati su sistemi propri o autorizzati; obbligo di backup; scopo della distribuzione (test, feedback e critiche migliorative); uso a proprio rischio; manleva per uso illecito (8.7); legge italiana applicabile; nota «da far rivedere a un avvocato».
- Primo avvio: testo completo della licenza nella finestra (niente più file temporaneo né apertura esterna) e **doppia accettazione**: 1) licenza ed esclusione di responsabilità, 2) approvazione specifica delle clausole ai sensi degli artt. 1341-1342 c.c. «Accetto» si attiva solo con entrambe.

### Automazione: descrizioni, rischio e guida
- Ogni ricetta (predefinita o dell'utente) mostra nel pannello di dettaglio la **descrizione**, il **livello di rischio** (sola lettura / modifica / distruttiva) e l'**elenco dei passi eseguiti**. Descrizioni in italiano per le ricette predefinite; per quelle dell'utente descrizione facoltativa e modificabile («Modifica descrizione...»), altrimenti generata dai passi.
- Guida integrata **«? Come creare un'automazione»** in stile Matrix: esempio concreto, ordine dei passi, prova a vuoto, backup prima dei passi distruttivi, esportazione e importazione delle ricette.

### Test
- 327 test automatici su Linux (nuovi: personalizzazione e intestazioni, modulo e riferimenti normativi ammessi, EULA 3.0 e doppia accettazione, rischio e descrizioni delle ricette, guida).

## [1.4.0-beta10] – 2026-11-27 · non pubblicata

### Dopo ogni esportazione: «Apri file» / «Apri cartella» solo su clic
- Dopo ogni export (PDF, HTML, CSV, PNG e zip) compare la notifica **«Esportazione completata»** con il percorso e i pulsanti **«Apri file»** e **«Apri cartella»**. Il file **non viene mai aperto in automatico**: il pulsante predefinito è «Chiudi» (Invio ed Esc non aprono nulla). Durante un'operazione la notifica arriva a operazione finita.
- «Apri file» usa l'associazione di Windows (ShellExecute, `UseShellExecute=true`); «Apri cartella» avvia `explorer.exe /select,"percorso"`. Entrambi solo dal gestore del clic e dopo la validazione del percorso: file esistente, percorso assoluto e normalizzato, nessun carattere speciale o virgolette, estensione ammessa (`.pdf`, `.html`, `.csv`, `.png`, `.zip`). Se il file è stato spostato o eliminato i pulsanti restano disattivati. Nessun argomento costruito da input esterno.
- Applicata a ExportService (tutti i pulsanti «Esporta») e a tutti i moduli: registro (Esporta, Salva PDF), Analisi spazio (PDF/HTML/PNG/CSV e CSV di dettaglio), Duplicati, Stato hardware, Scanner IP/MAC, report di sistema, report batteria, report per il cliente (HTML e PDF), report di disinstallazione, inventario (CSV), preferiti, report delle attività schedulate, report dell'automazione, pacchetto diagnostico (zip), elenco periferiche e backup dei driver (zip).
- **Rimosse le aperture automatiche** che esistevano ancora: report batteria, report per il cliente HTML, report delle attività schedulate, report dell'automazione, cartella dei preferiti esportati e cartella dei risultati del remoting. Ora c'è la notifica (o la riga nel registro).

### Test
- Nuovi test di guardia: nel percorso di esportazione (ExportService, SpaceExport, PdfReport, ClientReport, moduli) nessun avvio di processi né aperture; in `OpenOnClick` esattamente 2 avvii, solo nei metodi del clic e dopo la validazione; i metodi del clic sono chiamati solo dai gestori `Click` della notifica; la notifica non apre nulla da sola (nessun Shown/Load, «Chiudi» predefinito); test della whitelist e della validazione. 293 test automatici su Linux.

## [1.4.0-beta9] – 2026-11-27 · non pubblicata

### ANALISI SPAZIO: esportazione della treemap con l'elenco
- Dopo la scansione, «Esporta (PDF, HTML, PNG, CSV)…»: **PDF** con la treemap (immagine sulla prima pagina) e sotto l'elenco numerato degli spazi rappresentati (percorso, dimensione, %, numero di file, tipo prevalente con il quadratino del colore della legenda) più la legenda dei colori; **PNG** della treemap (1600×1000, numeri delle aree uguali a quelli dell'elenco); **CSV** dell'elenco (con colore `#RRGGBB`) e CSV di dettaglio; **HTML** dell'elenco. File scritti direttamente nel percorso scelto, nessuna apertura automatica (regole beta7). Lite e Pro.

### DISINSTALLA (Pro)
- Due sezioni: **PROGRAMMI** (Win32 dal registro) e **APP DI WINDOWS** (pacchetti Appx/MSIX dell'utente letti con l'API documentata `Windows.Management.Deployment.PackageManager`, senza PowerShell). App di sistema, framework e componenti essenziali (Store, Programma di installazione app, Sicurezza di Windows, VCLibs, UI.Xaml…) elencati ma **protetti**: non selezionabili per la rimozione. Rimozione di un'app solo su clic, con conferma (`RemovePackageAsync`, utente corrente). Rimossi gli script `ElencoAppStore.ps1` e `RimuoviAppStore.ps1`.
- Colonna **«Spazio occupato»** ordinabile: `EstimatedSize` del registro (mostrato con «≈», «stimato (registro)») oppure cartella di installazione misurata in background (senza seguire giunzioni) con cache di 7 giorni in `CacheSpazioProgrammi.json` («misurato (cartella)»); valori sconosciuti sempre in fondo. Ricerca per nome o produttore. Menu DISINSTALLA ▾ invariato.

### PULIZIA: ELIMINAZIONE SICURA (Pro)
- File e cartelle (con sottocartelle). Livelli: **Rapido** (1 passaggio di zeri), **Standard** (1 passaggio casuale, NIST SP 800-88 «Clear»), **Rafforzato** (3 passaggi: zeri, uni, casuale), **Estremo** (7 passaggi casuali con verifica di lettura, rinomina casuale ripetuta, troncamento a 0, date portate al 01/01/1980 prima dell'eliminazione, sovrascrittura facoltativa dello spazio libero con margine di sicurezza).
- Tipo di disco rilevato (WMI `MSFT_Partition` → `MSFT_PhysicalDisk` MediaType/BusType; unità rimovibili e di rete da DriveInfo). Su **SSD, USB e schede** avviso chiaro: la sovrascrittura **non garantisce** l'irrecuperabilità (wear leveling, TRIM, aree di riserva); consigliati BitLocker o il Secure Erase / Sanitize del produttore. Anche su rete l'irrecuperabilità non è garantita.
- Sicurezza: doppia conferma con riepilogo (numero di file e dimensione) e, per Estremo, digitazione di «ELIMINA»; bloccati radici delle unità, Windows, Program Files, ProgramData, profilo utente e sue cartelle standard, cartelle di sistema dell'utente e dati dell'app; collegamenti e giunzioni mai seguiti (si rimuove solo il collegamento); file in uso non toccati e segnalati; sola lettura gestita; barra con tempo, registro, annullabile, esportazione. Tutto nel codice: nessuno strumento esterno.

### Regola generale: avanzamento ed esportazione comuni
- Nuovo componente **ProgressPanel** (percentuale reale e monotona, al 100% solo a fine operazione, oppure «totale non stimabile» dichiarato; tempo mm:ss che resta fermo sull'esito «Completato in» / «Annullato dopo» / «Errore dopo»). Usato dalla finestra principale (tutte le operazioni), Analisi spazio, Duplicati, Cartella Download, Backup driver, Stato hardware, misura dello spazio dei programmi ed Eliminazione sicura. Le barre a scorrimento continuo sono state eliminate.
- Nuovo **ExportService**: CSV, HTML e PDF con firma fissa e timbro del tecnico, scrittura diretta nel file scelto, nessuna apertura. Pulsante **«Esporta»** nel registro (risultato dell'ultima operazione, Lite e Pro) e «Esporta (PDF, HTML, CSV)…» in Duplicati, Download, Programmi/App, Residui, Avvio, Servizi, Attività schedulate, Scanner IP/MAC ed Eliminazione sicura; HTML aggiunto in Stato hardware e Analisi spazio.
- **Timbro facoltativo**: se il tecnico non lo imposta (o lo disattiva) gli export mantengono l'intestazione del software, senza righe vuote, segnaposto o «Tecnico: -».

### Altro
- Regole anti-Defender e test di guardia invariati; nessun nuovo processo esterno (le app di Windows ora usano l'API invece di PowerShell). 282 test automatici su Linux.

## [1.4.0-beta8] – 2026-11-27 · non pubblicata

### HARDWARE (Lite e Pro) – sensori senza driver
- «Stato hardware (sensori senza driver)…»: CPU (carico, frequenza), RAM, moduli, GPU, tempo di accensione, temperature ACPI, salute dei dischi e contatori SMART di Windows (temperatura, usura SSD, ore, errori non corretti), batteria (carica, usura, cicli). Solo WMI, nessun driver kernel, nessun processo; aggiornamento ogni 5 s solo a finestra aperta; esportazione PDF e CSV.
- Ventole e tensioni: **non incluse** (richiedono un driver kernel di terze parti). Verificato che LibreHardwareMonitor è passato da WinRing0 a **PawnIO** (PR #1857 del 16/09/2025, release v0.9.5 del 07/01/2026): modulo in attesa del via libera. Dettagli: `progetto/HARDWARE-SENSORI-1.4.0-beta8.md`.

### BACKUP DRIVER (Pro, nuova voce nella colonna sinistra)
- Cartella di destinazione scelta dal tecnico (Sfoglia: locale, USB, disco esterno o UNC) e ricordata nelle impostazioni (`Impostazioni.json`), con spazio libero mostrato (GetDiskFreeSpaceEx) e stima prudente dello spazio necessario.
- Prima di partire: controllo del percorso, dello spazio libero e dei permessi di scrittura (la sottocartella e gli elenchi vengono scritti prima dell'esportazione, nessun file di prova).
- «Backup di tutti i driver»: sottocartella `Driver_<PC>_<aaaammgg_hhmm>` con `pnputil /export-driver *`, `periferiche.csv` e `periferiche.html` (Win32_PnPSignedDriver), `LEGGIMI-RIPRISTINO.txt`; zip facoltativo (sostituisce la cartella dopo la verifica). Barra di avanzamento reale (pacchetti esportati su `%SystemRoot%\INF\oem*.inf`, poi byte compressi) e tempo «Completato in mm:ss» come in Analisi spazio; «Apri la cartella del backup» solo su clic.
- «Ripristina driver da backup…»: zip (estratto accanto, con protezione dai percorsi esterni) o cartella; conferma, punto di ripristino, `pnputil /add-driver *.inf /subdirs /install`. Mai rimozione di driver né opzioni forzate.
- «Elenco periferiche e driver (CSV)» in sola lettura.

### ANALISI SPAZIO: avanzamento reale
- Barra con percentuale vera: byte letti sullo spazio occupato del volume (dischi interi e unità mappate, DriveInfo); per cartelle e percorsi UNC pre-conteggio veloce (massimo 2 s), altrimenti barra indeterminata dichiarata («avanzamento non stimabile in anticipo»).
- File e cartelle letti, byte, cartella corrente e tempo mm:ss dal vivo (aggiornamento dell'interfaccia a circa 10 volte al secondo); a fine scansione il tempo si fissa: «Completato in mm:ss», «Annullato dopo mm:ss» o «Interrotto per errore dopo mm:ss». La barra non torna mai indietro e arriva al 100% solo a scansione finita.

### BSOD e controllo di sicurezza
- «Analizza BSOD e minidump» (Pro, sola lettura): codice di arresto e parametri dall'intestazione dei dump (32/64 bit), spiegazione in italiano di oltre 30 codici, driver non di base presenti nel minidump (indizio), eventi BugCheck 1001 e Kernel-Power 41 degli ultimi 90 giorni (EventLogReader). Per il modulo certo: WinDbg.
- Controllo di sicurezza: nuove voci «aggiornamenti» (ultimo hotfix: avviso oltre 45 giorni, critico oltre 90) e «integrità della memoria» (HVCI, Win32_DeviceGuard). Sola lettura, nessuna correzione automatica nuova.

### Timbro del tecnico ed easter egg
- Informazioni: pannello «Timbro del tecnico» (nome o nickname, gruppo, attivo/disattivo, anteprima), salvato in `Timbro.json` nella cartella dati. Il timbro compare in alto a destra nei PDF e nel piè di pagina del report per il cliente; la firma fissa «iSINAPSi · powered by Manuele overnext» resta sempre.
- Codice Konami (↑ ↑ ↓ ↓ ← → ← → B A) nella finestra Informazioni: sblocca il badge del gruppo «overnext».

### Altro
- Regole anti-Defender invariate: nessuna azione all'avvio, manifest asInvoker (Lite), nessun nuovo `Process.Start`; i comandi esterni nuovi sono solo `pnputil` (System32) su clic.
- 227 test automatici (60 nuovi). Licenza invariata (2.9).
- Mockup: `mockup/iSINAPSi-PCXX1-1.4.0-beta8-informazioni-timbro-overnext.png`, `-stato-hardware.png`, `-analisi-spazio-avanzamento.png`, `-analisi-spazio-completato.png`, `-backup-driver-avanzamento.png`, `-backup-driver-completato.png`, `-esempio-pdf-hardware-timbro.pdf`.

## [1.4.0-beta7] – 2026-11-27 · non pubblicata

### Rilevamento Defender all'esportazione PDF (beta5)
- Il PDF era già creato dall'app (`PdfReport`, nessun programma esterno). Rimossi però i comportamenti a rischio intorno all'esportazione: file `.tmp` eliminato e rinominato, apertura automatica del PDF con `Process.Start`. Ora la scrittura è diretta nel file scelto e il PDF non viene aperto automaticamente. Analisi: `progetto/DEFENDER-PDF-1.4.0-beta7.md`.
- Nuovo «Esporta il report per il cliente in PDF» (Lite e Pro): PDF interno con testo ricercabile, senza browser; l'HTML resta disponibile.
- Test di guardia: nessun `Process.Start`, `OpenTarget`, script, browser, stampante, TEMP o `.tmp` nel percorso di esportazione.
- Altri percorsi: la chiave OEM si legge solo su richiesta esplicita; la password Wi-Fi non viene più estratta (eliminato `netsh … key=clear`, si apre la pagina di Windows); «Interrompi» senza `taskkill`; lettura delle schede di rete senza PowerShell (`SchedeRete.ps1` rimosso).

### Interfaccia
- Disinstalla: pulsante **DISINSTALLA ▾** con menu a tendina: Disinstalla (normale), Disinstallazione forzata (avvio diretto, stesse conferme, backup e quarantena), Solo ricerca residui. Resta la proposta automatica della rimozione forzata se il disinstallatore fallisce.
- «Attività fissate» rinominata **ATTIVITÀ SCHEDULATE** ovunque (interfaccia, report, comandi, documenti).
- Colonna sinistra: tutte le voci in **MAIUSCOLO**; colonna portata da 196 a 254 px (pulsanti da 174 a 232 px). Nessun troncamento in grassetto a 100%, 125% e 150%, verificato da un test con misura del testo e da un'immagine di controllo. Titolo del registro abbreviato in «Registro», pulsanti del registro da 96 a 88 px.

### RETE (come in networKING)
- Elenco delle schede con stato evidente: ● Attiva, ○ Disattivata (riga attenuata e in corsivo, icona barrata in rosso), ⚠ Cavo scollegato, ⚠ Nessun IP / APIPA 169.254.x.x; «in uso» per la scheda attiva con gateway.
- Pulsante **Riattiva** (verde, compare per le schede disattivate); «Disattiva...» con avviso severo se la scheda è in uso o è l'unica attiva (sessioni remote). Comandi: `Win32_NetworkAdapter.Enable()/Disable()`.
- Aggiornamento in tempo reale: eventi `NetworkChange` più un controllo ogni 5 s, solo mentre la scheda RETE è aperta (nessuna lettura all'avvio). Nella Lite l'elenco c'è, in sola lettura.

### Altro
- Licenza 2.9 (punto 12.2: PDF interni, password Wi-Fi non lette, chiave OEM solo su richiesta): l'accettazione viene richiesta di nuovo.
- PDF: a capo sulle parole; simboli fuori WinAnsi (√ → ● ○ ⚠ ▲ ▸) resi leggibili.
- Mockup: `mockup/iSINAPSi-PCXX1-1.4.0-beta7-colonna-maiuscolo-menu-disinstalla.png`, `-colonna-100-125-150.png`, `-rete-stato-schede.png`, `-rete-riattiva.png`, `-esempio-report-cliente.pdf`.

## [1.4.0-beta6] – 2026-11-27 · non pubblicata

### Analisi spazio (nuova scheda)
- Lite e Pro: scansione di dischi locali, unità di rete mappate, percorsi UNC e cartelle, con opzioni sottocartelle, file nascosti, file di sistema ed esclusioni (nomi con * e ?, percorsi). Giunzioni e collegamenti simbolici non seguiti (niente cicli), cartelle senza accesso segnalate, scansione in background con avanzamento e «Interrompi». Avvio solo su clic.
- Albero ordinato per dimensione (caricamento progressivo) e treemap squarified con effetto a cuscino, implementazione propria; colori per estensione (tavolozza Okabe-Ito estesa), legenda per estensione e statistiche per categoria; selezione multipla con le caselle dell'albero o Ctrl+clic sulla treemap; esportazione CSV (punto e virgola, UTF-8, protezione dalle formule).
- Solo Pro: copia, sposta (copia completa poi eliminazione; conflitti: rinomina o salta), Cestino, eliminazione definitiva con doppia conferma. Blacklist della rimozione forzata più Programmi, file e cartelle di sistema in radice. Operazioni nel report per il cliente.

### Duplicati (Pro)
- Stessa dimensione › SHA-256 dei primi e ultimi 64 KB › SHA-256 completo; gruppi con spazio recuperabile; selezione automatica (mantieni il più recente, il più vecchio o quello nel percorso preferito); in ogni gruppo almeno una copia resta sempre (controllo sulla casella e prima di ogni azione); Cestino, eliminazione definitiva, sposta, CSV.

### Cartella Download (Pulizia, Lite e Pro)
- Voce mai preselezionata: elenco con anteprima, filtro per età (predefinito 30 giorni), nessun file preselezionato, conferma esplicita, Cestino predefinito; altri profili solo nella Pro; solo elementi davvero dentro le cartelle Download.

### Altro
- Licenza 2.8 (nuove funzioni descritte al punto 8.1): l'accettazione viene richiesta di nuovo. Regole anti-Defender della beta5 invariate e verificate dai test (142 su Linux).
- Mockup: `mockup/iSINAPSi-PCXX1-1.4.0-beta6-analisi-spazio-treemap.png`, `-duplicati.png`, `-attivita-schedulate.png`.

## [1.4.0-beta5] – 2026-11-27 · non pubblicata

### Microsoft Defender (falso positivo Behavior:Win32/DefenseEvasion.A!ml sulla beta4)
- Nessuna modifica alle impostazioni di Microsoft Defender: la correzione «protezione in tempo reale» ora apre Sicurezza di Windows (prima conteneva `Set-MpPreference -DisableRealtimeMonitoring $false`).
- PowerShell sempre in chiaro: `-ExecutionPolicy RemoteSigned` al posto di `Bypass` (app, attività BloccoWU, installer), nessun `-WindowStyle Hidden` (BloccoWU, Remoting), nessun PowerShell nello script di emergenza delle attività.
- Manifest della Pro `asInvoker`: all'avvio chiede «Riaprire come amministratore?» e solo dopo Sì mostra la richiesta UAC. Nessuna eliminazione di file all'avvio (pulizia residui ManuHelp spostata in Strumenti).
- Regole del firewall dei programmi rimossi con l'API COM di Windows Firewall invece di `netsh`.
- Metadati completi dell'exe (Company, Product, FileDescription, Copyright «© 2026 iSINAPSi · powered by Manuele overnext», Trademark, versione).
- Portable distribuita **solo come ZIP** (exe .NET normale non compresso, nessun SFX, con LICENZA.txt, SISTEMI.txt e il nuovo LEGGIMI.txt); l'exe sciolto non è più un file di release. Setup NSIS secondario.
- Audit e istruzioni per il falso positivo: `progetto/DEFENDER-AUDIT-1.4.0-beta5.md`.

### Esclusione di responsabilità
- Finestra al primo avvio con accettazione obbligatoria (testo grande: «così com'è», responsabilità dell'utente, backup, uso su sistemi propri o autorizzati, art. 1229 c.c.), richiesta di nuovo a ogni nuova versione della licenza; ripresa in Informazioni, README, LEGGIMI e licenza (versione 2.7, nuova sezione «AVVERTENZA IMPORTANTE»). Avviso aggiuntivo in tutte le conferme delle azioni distruttive. Testo non rivisto da un avvocato.

### Attività schedulate (Pro)
- Attività dell'Utilità di pianificazione in `\iSINAPSi\PCXX1\` (COM, autore e marcatore `iSINAPSi-PCXX1-managed`), scheda «Attività schedulate», comandi `--attivita-elenco`, `--attivita-rimuovi`, `--attivita-rimuovi-tutte`, script di emergenza, proposta di rimozione nella disinstallazione e nel report per il cliente.

## [1.4.0-beta4] – non pubblicata (in preparazione)
### Cambiato
- Voce attiva della colonna di sinistra in **grassetto** (Segoe UI Bold 10,5 pt), testo #082F49 su verde logo #B0FF00 (11,33:1) con «▸». Verificato che l'etichetta più lunga («▸ Windows Update», circa 136 px su 158 px utili) non venga troncata: larghezza della colonna invariata.

## [1.4.0-beta3] – non pubblicata (in preparazione)
### Cambiato
- **Scheda attiva della colonna di sinistra con i colori del logo**: sfondo verde acido del logo #B0FF00 e testo blu scuro #082F49 (contrasto 11,33:1, AAA), indicatore «▸» mantenuto. Prima (beta2): bianco su #0369A1, 5,93:1. Variante con testo #0369A1 (4,85:1) valutata in `mockup/iSINAPSi-PCXX1-1.4.0-beta2-prova-navigazione-B-invertita.png`.

## [1.4.0-beta2] – non pubblicata (in preparazione)
Seconda beta. Prove su Windows ancora da fare: vedi `progetto/TEST-1.4-WINDOWS.md` (sezioni 11 e 12).

### Aggiunto (Pro)
- **Rimozione forzata** nella disinstallazione completa: prima il disinstallatore ufficiale (`UninstallString`/`QuietUninstallString`, MSI con `msiexec /x`); se manca, termina con errore o il programma resta registrato (esiti MSI 0/1605 ok, 1641/3010 riavvio, 1602 annullato), l'app propone la rimozione forzata.
- Ricerca estesa: AppData **LocalLow** (anche degli altri profili), Common Files, voci di **avvio automatico** (`Run`/`RunOnce` in HKLM a 64/32 bit e HKCU), **regole di Windows Firewall** con l'eseguibile nella cartella del programma, **driver** (solo la registrazione del servizio, mai il file), collegamenti sul Desktop e nel menu Start di tutti i profili.
- Classificazione **«sicuro»** (solo di questo programma, preselezionato) / **«condiviso o incerto»** (mai preselezionato, sempre con il motivo): cartella del produttore con altri prodotti, DLL registrate in `SharedDLLs` con conteggio > 1, Common Files, runtime, cartelle che contengono l'installazione di un altro programma. Selezionarli richiede una conferma esplicita che li elenca.
- Prima di eliminare: punto di ripristino (casella, attiva di default), `reg export` delle chiavi e dei valori, copia in quarantena con lettura condivisa (anche file in uso), chiusura dei processi avviati dalle cartelle da rimuovere (con conferma), presa di possesso con `icacls /setowner *S-1-5-32-544` se l'accesso è negato, eliminazione al riavvio dei file bloccati (`MoveFileEx` con `MOVEFILE_DELAY_UNTIL_REBOOT`). Regole del firewall rimosse con `netsh advfirewall firewall delete rule` (nome + programma).
- **Report per il cliente** della disinstallazione (esito del disinstallatore, elementi con valutazione ed esito, elementi in attesa di riavvio, quarantena) firmato «iSINAPSi · powered by Manuele overnext»; voce nel registro interventi.

### Cambiato
- Elenco nero rigido centralizzato (`src/RemovalPolicy.cs`): oltre a Windows/WinSxS/DriverStore, anche Common Files, `ProgramData\Microsoft`, cartella Users, profili interi (Public, Default) e le loro cartelle di sistema (AppData, Roaming, Local, LocalLow, Desktop…), condivisioni di rete senza sottocartella.
- **Contrasto (WCAG 2.x AA)**: i browser non installati non sono più caselle disattivate di sistema (testo quasi nero): nuova casella disegnata dal tema con testo #8A99AD (6,2:1) e dicitura «○ Nome - non installato». Scheda attiva su #0369A1 (bianco 5,9:1, prima #0EA5E9 2,8:1) con indicatore «▸». Accento dei titoli #38BDF8 (8,3:1). Simboli √ ▲ × davanti alle righe di esito del registro. Report: testo secondario #5F6368 (6,1:1). Tabella completa in `progetto/CONTRASTO-1.4.0-beta2.md`.
- Licenza 2.6: clausola 10.3 aggiornata (rimozione forzata, «condiviso o incerto», punto di ripristino facoltativo).

## [1.4.0-beta] – non pubblicata (in preparazione)
Prima beta dell'automazione per tecnici. Prove su Windows ancora da fare: vedi `progetto/TEST-1.4-WINDOWS.md`.

### Aggiunto (Pro)
- **Automazione** (nuova scheda): profili JSON `isinapsi-pcxx1-profilo/1` con passi, condizioni `se` (admin, winget, spazio libero, dominio, portatile, build minima, esito del passo precedente), **prova a vuoto** (attiva di default), `fermaSuErrore`/`continuaSuErrore`, punto di ripristino automatico prima del primo passo che modifica il sistema, una sola conferma che elenca le modifiche. Catalogo chiuso di azioni (sola lettura: inventario, audit, SMART, eventi, Windows Update, winget, DISM CheckHealth, preferiti; con modifiche: pulizie, DISM RestoreHealth, SFC, flush DNS, reset di rete, correzioni dell'audit, aggiornamenti winget, punto di ripristino).
- **4 ricette incorporate**: *PC nuovo cliente*, *Pulizia periodica*, *Controllo pre-migrazione* (con copia dei preferiti), *Riparazione di Windows*; esportabili come base per profili propri.
- **Riga di comando** estesa: `--profilo` con `--prova`, `--si`, `--json`, `--output`, `--silenzioso`, `--cliente`, `--report-cartella`; `--ricette`, `--azioni`, `--valida-profilo`, `--esporta-ricetta`, `--audit-correggi`, `--wu-elenco`, `--winget-elenco`, `--winget-aggiorna`, `--test-remoto`, `--remoto`; alias inglesi (`--profile`, `--dry-run`/`--whatif`, `--yes`, `--quiet`…). Codici di uscita: 0, 1, 2, 3 (conferma mancante), 4 (avvisi), 5, 6 (profilo non valido), 3010 (riavvio).
- **Correzioni dell'audit** da un elenco chiuso (firme e protezione in tempo reale di Defender, firewall, SMBv1, NLA per Desktop remoto, UAC), solo selezionate a mano, con punto di ripristino e nuovo audit.
- **Windows Update**: elenco in sola lettura degli aggiornamenti disponibili (Windows Update Agent API). **winget**: elenco dei programmi aggiornabili e aggiornamento dei soli scelti, con conferma.
- **Reset di rete** anche nella scheda Riparazione.
- **Remoting (BETA, opt-in)**: esegue un profilo su più PC via PowerShell Remoting (WinRM/HTTPS facoltativo), copia temporanea dell'exe verificata con SHA-256, raccolta di report e risultati in `Report\Remoto\<data>\<PC>`, riepilogo JSON. Credenziali mai in chiaro: Gestione credenziali di Windows/DPAPI.

### Aggiunto (Lite e Pro)
- **Inventario del PC** (sola lettura): hardware, programmi (chiavi Uninstall, non Win32_Product), hotfix, driver (Pro), stato della licenza di Windows, presenza della chiave OEM **sempre mascherata**; chiave completa solo su richiesta esplicita, a schermo, mai in log/report/JSON. Esportazione TXT, CSV dei programmi e JSON.
- **Audit di sicurezza** in sola lettura: Defender, firewall, BitLocker, Secure Boot, TPM, amministratori locali, account Administrator e Guest, condivisioni scrivibili da Everyone, SMBv1, Desktop remoto/NLA, UAC.
- **Report per il cliente** in HTML autonomo stampabile in PDF (A4), firmato **iSINAPSi** · *powered by Manuele overnext* (firma fissa) con logo iSINAPSi: hardware, SMART, azioni, spazio recuperato prima/dopo, sicurezza, aggiornamenti; opzione per oscurare il nome del PC. **Registro interventi** per cliente.
- **Esportazione dei preferiti** dei browser (Chrome, Edge, Brave, Opera, Opera GX, Firefox) in HTML standard: **solo segnalibri, mai password**, cookie o cronologia. Opzione **zip AES-256 protetto da password** (formato WinZip AES, implementazione propria senza librerie di terze parti; nessun file in chiaro su disco; da riga di comando `--zip` con la password nella variabile `PCXX1_ZIP_PASSWORD`).
- Riga di comando Lite: `--inventario`, `--audit`, `--report-html`, `--esporta-preferiti`.

### Modificato
- Versione 1.4.0 (etichetta 1.4.0-beta); licenza d'uso 2.5 con nuove clausole (remoting e autorizzazioni, credenziali, automazione, audit non certificazione, winget, preferiti, report e registro interventi).

## [1.3.0] – 2026-11-25 · prima beta pubblica
Prima versione pubblicata su GitHub. Due edizioni **completamente gratuite** dallo stesso codice: **iSINAPSi PCXX1 Lite** e **iSINAPSi PCXX1 Pro**. Nessuna chiave di licenza, nessuna attivazione, nessuna pubblicità, nessuna telemetria. File non firmati digitalmente.

### Aggiunto (Pro)
- **Programmi all'avvio** (scheda *Avvio e servizi*): elenco di chiavi Run `HKCU`/`HKLM` (anche `WOW6432Node`), cartelle Esecuzione automatica dell'utente e di tutti gli utenti, attività pianificate con trigger all'accesso o all'avvio (`Get-ScheduledTask`). Disattivazione reversibile come in Gestione attività (valori `StartupApproved\Run`, `Run32`, `StartupFolder`; meccanismo non documentato ufficialmente da Microsoft, la voce originale non viene toccata) e `schtasks /change /disable|/enable` per le attività. Backup dello stato precedente prima di ogni modifica e ripristino da file. Attività di Windows evidenziate con conferma in più.
- **Servizi**: elenco con ricerca e filtro "solo non di Windows", stato e tipo di avvio (`ServiceController`, `DelayedAutostart`), avvio e arresto, tipo di avvio con `sc.exe config … start= auto|delayed-auto|demand|disabled`. Servizi essenziali di Windows protetti; avviso in più per gli altri servizi di Windows; backup del tipo di avvio di tutti i servizi prima della prima modifica e ripristino.
- **Salute dei dischi (SMART)**: `Get-PhysicalDisk`, `Get-StorageReliabilityCounter` (temperatura, usura, errori non corretti, ore di accensione) e `MSStorageDriver_FailurePredictStatus` (previsione di guasto), con avvisi evidenziati e soglie prudenziali.
- **Pacchetto diagnostico** .zip nella posizione scelta dall'utente: sistema, rete (`ipconfig /all`, `route print`, `netsh interface ip show config`), dischi, eventi critici ed errori degli ultimi 7 giorni (`Get-WinEvent`), avvio, servizi, programmi installati, log dell'app, con un file LEGGIMI che spiega cosa contiene.
- **Riga di comando** per tecnici: `--aiuto`, `--versione`, `--pulizia-rapida [--si]`, `--report [cartella]` (entrambe le edizioni); `--smart`, `--diagnostica <file.zip>`, `--elenco-avvio` (Pro). Uscita sulla console del processo padre e in un file di log; codici di uscita documentati.

### Già presenti
- Lite: pulizia rapida, pulizia dei browser, rete, ping, speed test, informazioni sul PC, ManuHelp, feedback; senza privilegi di amministratore.
- Pro: pulizia di sistema, rete e scanner di rete IP/MAC con PDF, sistema e report, riparazione (SFC, DISM, chkdsk), Windows Update, recupero file, disinstallazione completa con quarantena, editor hosts, scorciatoie.

### Modificato
- Nuovo nome **iSINAPSi PCXX1** e nuove icone: grande "iS" verde `#B0FF00` su viola `#6D28D9`, sotto "PCXX1 Lite" o "PCXX1 Pro" (targhetta oro). Le installazioni delle versioni precedenti (fino alla 1.2.0, con un nome diverso) vengono aggiornate: l'installer rimuove la vecchia installazione, i collegamenti e la voce di disinstallazione; al primo avvio l'app sposta i dati nella nuova cartella.
- Pulsante e-mail del Feedback attivo: isinapsicloud@gmail.com (nessun invio automatico: si apre il programma di posta).
- Licenza d'uso 2.4: nuove clausole su programmi all'avvio, servizi, salute dei dischi, pacchetto diagnostico e riga di comando.
