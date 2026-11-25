# Changelog
Tutte le modifiche rilevanti di iSINAPSi™ PCXX1™. Formato ispirato a [Keep a Changelog](https://keepachangelog.com/it-IT/1.1.0/); versioni secondo [Semantic Versioning](https://semver.org/lang/it/).

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
