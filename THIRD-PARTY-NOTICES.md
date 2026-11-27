# Componenti e servizi di terze parti

iSINAPSi™ PCXX1™ non include librerie di terze parti nell'eseguibile. Usa o richiama:

| Componente / servizio | Uso | Licenza / condizioni |
|---|---|---|
| Microsoft .NET Framework 4.8, Windows PowerShell 5.1 e strumenti di Windows (sfc, DISM, netsh, ipconfig, route, reg, sc, schtasks, cmdlet Storage, ScheduledTasks, Appx, Get-WinEvent, Get-CimInstance) | componenti del sistema operativo, non distribuiti con il programma | termini di licenza di Microsoft |
| NSIS (Nullsoft Scriptable Install System) | programma di installazione (Setup) | zlib/libpng; modulo LZMA: Common Public License 1.0 con eccezione speciale per il collegamento — https://nsis.sourceforge.io/License |
| Registro pubblico IEEE MA-L (OUI) | produttore delle schede di rete nello scanner (Pro), dati pubblici incorporati in forma compressa | dati pubblicati dalla IEEE Registration Authority — https://standards-oui.ieee.org/oui/oui.csv ; IEEE non è affiliato al progetto |
| Speed test di Cloudflare (speed.cloudflare.com) | misura della velocità, solo se avviata dall'utente | condizioni di Cloudflare, Inc. |
| RustDesk | **non incluso**: ManuHelp apre solo la pagina ufficiale delle release | AGPL-3.0, dei rispettivi autori |
| Windows File Recovery | **non incluso**: installato a parte dal Microsoft Store su scelta dell'utente | termini di licenza di Microsoft |
| Windows Package Manager (winget) | **non incluso**: elenco e aggiornamento dei programmi (Pro, 1.4) solo su conferma; i pacchetti scaricati sono software dei rispettivi autori con le loro licenze | termini di licenza di Microsoft; licenze dei singoli pacchetti |
| Windows Update Agent API (`Microsoft.Update.Session`) | elenco in sola lettura degli aggiornamenti disponibili (Pro, 1.4) | componente di Windows, termini di Microsoft |
| Windows PowerShell Remoting / WinRM | esecuzione remota dei profili (Pro, 1.4, **BETA**, opt-in); l'app non modifica la configurazione WinRM | componente di Windows, termini di Microsoft |
| Gestione credenziali di Windows e DPAPI (`CredWrite`/`CredRead`, `ProtectedData`) | conservazione facoltativa delle credenziali del remoting, mai in chiaro | API di Windows / .NET Framework |
| Formato LZ4 a blocchi e contenitore mozLz4 di Firefox | lettura del backup dei preferiti di Firefox (1.4); decodificatore scritto da zero nel Software, **nessun codice di terze parti incluso** | specifica del formato LZ4 pubblicata da Yann Collet (BSD-2-Clause per la documentazione e l'implementazione di riferimento, non usata) |
| Formato ZIP con cifratura WinZip AES (AE-2) | zip AES-256 protetto da password per i preferiti esportati (1.4); scritto da zero con le classi crittografiche di .NET Framework (AES, PBKDF2-HMAC-SHA1, HMAC-SHA1), **nessuna libreria di terze parti** | specifica pubblica di WinZip (Corel); formato ZIP: APPNOTE di PKWARE |
| Formato "NETSCAPE-Bookmark-file-1" | file HTML dei preferiti esportati, importabile da tutti i browser | formato di fatto, nessuna licenza richiesta |

Tutti i marchi citati appartengono ai rispettivi titolari; l'uso dei nomi è solo descrittivo (per indicare compatibilità o il servizio usato).


Note per la 1.4 (beta):
- Le Microsoft Security Baselines sono il riferimento delle verifiche dell'audit; i CIS Benchmarks (licenza CC BY-NC-SA 4.0) **non** sono riprodotti nel Software (vedi `progetto/ROADMAP-1.4-2.0.md`).
- L'esportazione dei preferiti legge solo i file dei segnalibri (Chromium `Bookmarks`, Firefox `bookmarkbackups/*.jsonlz4`): mai password, cookie o cronologia.
