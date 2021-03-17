# fffmpeg batch encoding
Description and command line instruction to make a batch encoding of videos from mp4/mov to hap mov.

<h1><b>Istruzioni in italiano</b></h1>


<b> Intro </b>

-Se stai usando il software VVVV puoi scaricare il plugin di vvvv da qui https://vvvv.org/contribution/demolition-media-hap-player; questo ti permetterà di encodare singolarmente i file, ma non di fare una esportazione in serie. Per fare questo seguire le istruzioni che seguono utilizzando terminale.

-Preparare video encoding Hap con quicktime o ffmpeg https://www.dropbox.com/s/u2wiccg9ru1tx41/Hap%20Encoding%20Tips.pdf?dl=1

<b> Importante!! </b>
Alcuni caratteri (come spazio o punti) nel nome di un file potrebbero impedire di eseguire il comando da prompt! Usare terminale o altro per rinominare/sostituire questi caratteri dal nome dei file.

_______________________________________________________________________
<b>Per velocizzare ricerca di ffmpeg:</b>

Modifica le variabili di ambiente relative al sistema 
<br>Proprietà di sistema > Avanzato > Variabili d'ambiente > Variabili di sistema : Path: Modifica > aggiungere il percorso per bin che si trova dentro cartella ffmpeg


<h2><b>1. Scaricare build FFMPEG </b></h2>

https://www.ffmpeg.org/download.html

<h2><b>2.a Per conversione da .mp4 a _hap.mov:</b></h2>

Entrare in prompt

```ffmpeg```
<br>```cd Desktop``` (o ovunque tu abbia cartella video)
<br>```cd cartella_video```
<br>se non era in C, per cambiare directory: ```cd /d d:```
<br>poi per entrare nelle cartelle: ```cd nomecartella\nomecartella\nomecartella...```
<br>inserire così com'è:

```for /f "tokens=1 delims=." %a in ('dir /B *.mp4') do ffmpeg -i "%a.mp4" -c:v hap "%a.mov"```

(dove a = variabile qualsiasi)

<h2><b>2.c Per conversione da .mov a _hap.mov:</b></h2>

```for /f "tokens=1 delims=." %a in ('dir /B *.mov') do ffmpeg -i "%a.mov" -c:v hap "%a_hap.mov"```

il nome di destinazione va cambiato in _hap.mov perchè se no sovrascrive il file stesso e non riesce a fare la codifica.


<h2><b>2.b Per conversione da .mov a sequenza di .png:</b></h2>

```for /f "tokens=1 delims=." %a in ('dir /B *.mov') do (if not exist "%a\" mkdir "%a" && ffmpeg -i "%a.mov" -vsync 0 -vf "scale=480:480" "%a/out%d.png")```


_______________________________________________________________________

altro link utile:

https://gist.github.com/dlublin/e4585b872dd136ae88b2aa51a6a89aac
