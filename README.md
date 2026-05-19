<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/e071c79d-b1fe-409e-9613-cf131b38a5f7" />


# 🏰 CodeCastle


Un RPG dark-fantasy dove il codice è magia: impari Python vero scrivendo incantesimi che muovono un cavaliere dentro un castello.

## Cos'è

È una pagina HTML singola, senza installazioni e senza server. Dentro gira un interprete Python reale (Skulpt) compilato per il browser: quando lanci un "incantesimo" il tuo codice viene eseguito davvero e il cavaliere ripete i gesti, animato, nel dungeon. Non è un corso con la skin di un gioco: qui il gesto stesso di programmare è la meccanica, e l'unico modo per avanzare è scrivere ed eseguire codice.

Ci sono 22 quest divise in 5 biomi, dalla prima istruzione fino a ricorsione, classi, generatori e un boss finale (il Drago dei Cicli Infiniti). Insieme coprono tutta la sintassi base di Python: variabili e operatori, `for` e `while`, `if/elif/else`, booleani, liste, tuple, dizionari, set, comprehension, `break/continue`, `try/except`, funzioni, ricorsione, classi, `lambda`, generatori. Sopra c'è uno strato RPG vero — XP, livelli, ranghi (da Novizio a Signore del Codice), gold, streak giornaliera, combo, bonus "Soluzione Elegante", spellbook e imprese — e tutto resta salvato tra una sessione e l'altra. La grafica è pixel-art procedurale con torce animate, particelle, audio sintetizzato ed errori riscritti come lore senza però nascondere il messaggio tecnico reale.

Esistono due versioni. Quella leggera (`codex-arcanum.html`, ~30 KB) carica Skulpt da CDN e quindi serve connessione. Quella offline (`codex-arcanum-offline.html`, ~610 KB) ha Skulpt incorporato dentro: funziona senza rete, da `file://`, da chiavetta, anche su una macchina isolata.

## Perché esiste

Il modo classico di insegnare a programmare — prima la teoria, poi le slide, e solo alla fine forse un po' di pratica — è l'ordine sbagliato. Qui è ribaltato: agisci subito, il feedback è immediato e visivo, e la teoria emerge da ciò che fai. È una scelta di design con basi reali. La grande meta-analisi di Freeman e colleghi (2014, PNAS, 225 studi) mostra che l'apprendimento attivo alza i punteggi d'esame di circa 0,47 deviazioni standard, cioè circa il 6% in più, e che con la lezione frontale tradizionale si viene bocciati circa 1,5 volte più spesso. Sul lato motivazione, la meta-analisi di Sailer e Homner (2020) trova effetti significativi della gamification su esiti cognitivi, motivazionali e comportamentali. Qui ogni riga eseguita illumina il codice e muove il personaggio, così l'errore si vede invece di leggerlo soltanto, e la progressione a XP e quest serve a far tornare la gente, non è decorazione.

Una nota di onestà che conviene tenere: queste fonti spiegano perché il metodo funziona in generale, non quanto funzioni *questo* prodotto. Quel numero va misurato sul campo, e finché non lo misuri il README non lo rivendica.

## Misurare l'apprendimento sul campo

Invece di scrivere "25 amici hanno imparato più in fretta" senza prove — un claim che ti si ritorce contro alla prima domanda seria — qui c'è il modo per ottenere quel dato davvero e poterlo pubblicare a testa alta.

Il protocollo è semplice e dura una mezz'ora a persona. Prima un quiz di 10 domande sui costrutti base, segnando punteggio e tempo. Poi la sessione di gioco, partendo dal primo bioma fino ad almeno la terza fascia, senza aiuti esterni, annotando quanti minuti servono per il primo `for` e il primo `while` che funzionano davvero. Infine lo stesso quiz con le domande mescolate, più una breve autovalutazione da 1 a 5 su chiarezza, coinvolgimento e voglia di rifarlo. Se vuoi un test più rigoroso, fai studiare a un secondo gruppo lo stesso tempo su un tutorial testuale equivalente e confronta i miglioramenti.

Le cose da guardare sono quattro: di quanto sale il punteggio dal quiz prima a quello dopo, che è la misura principale; quanti minuti servono per arrivare al primo `for`/`while` corretto; quanti partecipanti completano la terza fascia; e quanto piace mediamente. Quando avrai i numeri reali, il modo difendibile di riportarli è qualcosa come: "In un playtest con 25 persone, singolo gruppo pre/post, il punteggio medio è passato da X a Y, con un tempo mediano di Z minuti per il primo `for` corretto; campione di convenienza, non randomizzato, quindi indicativo e non conclusivo". È proprio quell'ultima frase di cautela a rendere il dato credibile invece che marketing, quindi tienila. Quando li raccogli, te li sistemo io qui dentro.

## Come si gioca

Apri il file `.html` in un browser, doppio clic, niente da installare. Leggi la quest sulla sinistra con obiettivo e lore, scrivi Python nel Grimorio a destra e premi "Lancia l'Incantesimo": il codice gira e il cavaliere si muove. Raggiungi il portale verde per guadagnare XP e gold, e se ti blocchi c'è il pulsante "Visione" per un suggerimento. In gioco hai `up() down() left() right()` con alias italiani, più `break_wall(dir)`, `build_block(dir)`, `can_move(dir)`, `scan()`, `at_exit()` e `print()`, ed è Python completo: `for`, `while`, `def`, `class`, `try` e tutto il resto funzionano.

## Stack tecnico

Tutto è HTML, CSS e JavaScript puro in un unico file, senza framework e senza build. Python gira nel browser grazie a Skulpt, che è un interprete Python scritto in JavaScript: niente WebAssembly, niente download pesante, e con un limite di tempo integrato che ferma da solo i loop infiniti. La grafica è Canvas 2D con sprite pixel-art pre-renderizzati una volta e poi solo "stampati", così resta fluida anche su dispositivi deboli, dentro un loop `requestAnimationFrame`. L'audio è sintetizzato in WebAudio, quindi nessun file esterno. I progressi sono salvati in `localStorage` su file ospitato o locale; in anteprima dentro una sandbox semplicemente non salva, senza dare errori.

## Limiti, detti chiari

Su telefono il gioco gira ma scrivere codice col pollice in una textarea resta scomodo: l'esperienza è pensata per desktop, e un editor mobile dedicato è il prossimo lavoro che conta di più. Skulpt è un sottoinsieme di Python, senza import di librerie esterne e senza f-string negli scaffold: perfetto per i fondamentali, non un sostituto di un REPL completo. L'audio sono effetti sintetizzati, non musica composta per bioma. Il sistema di ricompense con XP, gold, ranghi e imprese c'è davvero, mentre skin, pet e il combattimento col boss sono più cornice narrativa che sistemi completi, perché richiedono asset e un artista.

## Licenza e crediti

Il codice del gioco è tuo: metti il tuo nome, l'anno e una licenza, per esempio MIT. La dipendenza esterna è Skulpt, distribuito sotto licenza MIT/PSFLv2. La build offline incorpora Skulpt minificato, perciò l'avviso di copyright e licenza upstream è riprodotto in testa al file HTML e il testo completo è in `LICENSE-skulpt.txt`: vanno mantenuti entrambi in qualsiasi ridistribuzione.

## Dove può andare

I prossimi passi sensati, in ordine di impatto reale: un editor usabile su mobile, poi l'esecuzione del playtest con la pubblicazione dei dati veri qui sopra, quindi livelli condivisibili via URL così sono i giocatori a creare sfide, la sintassi evidenziata in colore, e infine asset disegnati a mano al posto della grafica procedurale.

## Riferimenti

Freeman, S. et al. (2014). Active learning increases student performance in science, engineering, and mathematics. PNAS, 111(23), 8410–8415. doi:10.1073/pnas.1319030111

Sailer, M., & Homner, L. (2020). The Gamification of Learning: a Meta-analysis. Educational Psychology Review, 32, 77–112. doi:10.1007/s10648-019-09498-w

Huang, R. et al. (2023). Examining the effectiveness of gamification as a tool promoting teaching and learning in educational settings: a meta-analysis. Frontiers in Psychology, 14:1253549.
