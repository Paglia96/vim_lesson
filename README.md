# VIM, the vi imporoved text editor

## Introduzione
- [Richard Stallman: Emacs vs Vim](https://www.youtube.com/watch?v=1jPmnDZ6ab8)
- [Storia di Vim](https://en.wikipedia.org/wiki/Vim_%28text_editor%29)

```bash
vimtutor
```
Online si trovano webgame che aiutano ad apprendere vim

## Entrare in Vim
```bash
vim
vim new_project_name
vim existent_project
vim -S Session.vim
```

## Modalità
**Normal mode**: si entra in questa modalità, ci si torna premendo ctrl+[ (non ESC!)
**Command mode**: ':' + comando vim o si fa precedere '!' a un comando bash
**Inser mode**:
- 'i' sul carattere evidenziato dal cursore
- 'I' a inizio riga
- 'a' sul carattere successivo a quello evidenziato dal cursore
- 'A' a fine riga
- 'o' manda a capo e si entra in insert mode sulla riga successiva
- 'O' same ma reversed
**Visual mode**:
- 'v': visual (selezione per singoli caratteri)
- 'V': visual line
- ctrl + 'v': visual block
**Replace mode**: 'R'. 'r' consente invece la modifica del carattere su cui sta il cursore

## Uscire da Vim (meme)
:q # uscita
:q! # uscita forzata
:wq / :x # salva ed esci
:wqa # salva tutti i buffer aperti ed esci

## RTFM
- :help argument
- :help user-manual
- Ctrl + ] Su una parola evidenziata ne apre la voce
- Ctrl + t: torna indietro
- :q esci

## Undo, redo
- 'u': undo
- ctrl + 'r': redo
- '.': ripeti il comando appena eseguito
- 'x': cancellare il carattere su cui sta il cursore
- 'X': cancellare il carattere precedente 

## Muoversi
### Sulla stessa riga
- 'w' inizio parola successiva
- 'e': end. Fine parola.
- 'b': backword. Parola precedente.
- '0' inizio riga
- '$' fine riga
- '%' sposta alla parentesi di chiusura
### Nel file
- :15 sposta il cursore a riga 15
- 15G same
- 'H' high
- 'M' middle
- 'L' low
- 'G': ground. Vai a fine file
- 'gg': vai a inizio file
- ctrl + f: forward
- ctrl + b: backward
- ctrl + G: mostra la posizione in % nel file

## Tagliare, copiare, incollare 
- 'y' yank (copy)
- 'd' delete (cut)
- 'c' delete ed entra in Insert Mode
- 'p' paste dopo il cursore
- 'P' paste prima del cursore
### Copiare l'intero file sulla clipboard
- :w !cat | xsel -b # x11
- :w !cat | xclip -selection clipboard # x11
- :w !cat | wl-copy # wayland: non sui pc della 42 che usano x11
### Registri di vim
Vim salva sui propri registri, non sulla clipboard di sistema.

## Inserimento file esterni
:r filename: inserisce il contenuto del file a capo dopo il cursore
:r !command: inserisce l'output del comando a capo dopo il cursore


## autocompletion (Insert mode)
ctrl + n: come il tab del terminale, prima istanza
ctrl + p: ultima istanza
Si scorre premendo di nuovo la combinazione
Si seleziona continuando a scrivere (non con invio)
I suggerimenti sono legati ai buffer, non al singolo file

## Incremento/decremento di un int (Normal mode)
- ctrl + a: mentre il cursore si trova sopra una cifra

## Combinazioni: \[operator\]\[count\]\[motion\]
- dw: delete word
- cw: delete word and enter in insert mode
- yw: yank word
- d2w: delete two words
- d$: delete from the cursor to end of line
- d0: delete from the cursor to the start of the line
- dd: delete current line
### Combinazioni visual mode
- viw: seleziona parola corrente
- vaw: seleziona parola corrente e i suoi confini
- vi", vi), vi], vi}: seleziona tutto il contenuto dentro "", (), {}
- va", va), va], va}: seleziona tutto il contenuto dentro "", (), {} incluse le brackets
Una volta selezionato il testo è possibile usarvi gli operatori: d, y, c, U (rendi uppercase), u (rendi lowercase), ...

## Cercare parole
- /word: cerca 'word' in avanti (selezione anche negli altri buffer)
- ?word: cerca 'word' indietro
- /word\c: ricerca case-insensitive
- '#': cerca in avanti le istanze della parola su cui stava il cursore
- '*': same ma indietro
Premendo invio ci si muove tra le istanze della ricerca con 'n' e 'N', come su less, il pager di default del man

## Indentare più linee di codice
Sottolineare in visual mgit commit --amend --reset-author --no-eode, poi:
- \> indenta a destra di un tab
- < indenta a sinistra di un tab
- n> indenta di n tab (2>)

## Gestire più file contemporaneamente, l'incubo dei neofiti
### Buffers
:e path
:b
:ls
### Sessioni vim
- mksession
- mksession!
### Jobs del terminale
Utilissimi per muoversi tra vim e il terminale. Si può aprire un terminale come buffer di vim con ':term' ma lo trovo estremamente scomodo

## File di configurazione
```bash
vim ~/.vimrc
```
rc: run commands. Standard per i vecchi file di configurazione
Qui sono inseribili git commands che vengono eseguiti ad ogni apertura di vim
" questo è un commento
Vim può essere personalizzato con tantissimi plug-in mantenuti dalla community di utilizzatori. Ne sconsiglio però l'uso finché non si sono padroneggiate le funzioni principali del programma. Vim è installato o installabile sostanzialmente ovunque e essere in grado di usarne fluidamente la versione non estesa è importante. 
### Alcuni comandi utili da inserire nel rc o da usare dentro Vim:
:set nu
:noh : no highlight
- ...

## Programmi che utilizzano sintassi vim
- tiling window manager: spesso già impostati o impostabili con comandi simil-vim
- zathura: lettore pdf
- cutebrowser
- ...
