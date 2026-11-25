# Sicurezza

## Versioni supportate
| Versione | Supportata |
|---|---|
| 1.3.x (Lite e Pro) | ✅ |
| precedenti | ❌ |

## Segnalare una vulnerabilità
**Non aprire una issue pubblica.** Usa la segnalazione privata di GitHub (scheda *Security* › *Report a vulnerability*) oppure scrivi a: **isinapsicloud@gmail.com**.
Indica versione, edizione (Lite/Pro, installata/portable), passi per riprodurre il problema ed effetto. Rispondiamo appena possibile; è un progetto gratuito senza tempi di risposta garantiti.

## Superfici rilevanti
- La **Pro** gira con privilegi di amministratore. Gli script PowerShell incorporati vengono estratti in `%ProgramData%\iSINAPSi-PCXX1-Pro\bin`, una cartella con ACL riservata ad Administrators e SYSTEM, controllata prima di ogni esecuzione (anche contro junction e collegamenti); lo script estratto viene confrontato byte per byte con quello incorporato.
- La quarantena della disinstallazione completa (`%ProgramData%\iSINAPSi-PCXX1-Pro\Quarantena`) ha la stessa protezione.
- I backup di programmi all'avvio e servizi stanno in `Backup` nella cartella dati; il ripristino accetta solo righe valide (sottochiavi `Run`, `Run32`, `StartupFolder`; nomi di servizio validati; tipi di avvio ammessi).
- La **Lite** gira senza privilegi: dati per utente in `%LOCALAPPDATA%\iSINAPSi-PCXX1-Lite`.
- ManuHelp apre soltanto una pagina web: non scarica né avvia programmi.
- I file pubblicati **non sono firmati digitalmente**: verifica sempre le impronte in `SHA256SUMS-<versione>.txt`.
