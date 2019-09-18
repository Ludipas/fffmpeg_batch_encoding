# fffmpeg batch encoding
Description and command line instruction to make a batch encoding of videos from mp4/mov to hap mov.
Available in italian and english.

<h1><b>Istruzioni in italiano</b></h1>

<b>Per velocizzare ricerca di ffmpeg:</b>

Modifica le variabili di ambiente relative al sistema > Variabili d'ambiente > Variabili di sistema : Path: Modifica > aggiungere il percorso per bin dentro ffmpeg
Per conversione da mp4 a hap mov:

<h2><b>2. Per conversione da .mp4 a hap .mov:</b></h2>

Entrare in prompt

ffmpeg
cd Desktop (o ovunque tu abbia cartella video)
cd cartella_video
se non era in C, per cambiare directory: cd /d d:
poi per entrare nelle cartelle: cd nomecartella\nomecartella\nomecartella...
inserire così com'è:
for /f "tokens=1 delims=." %a in ('dir /B *.mp4') do ffmpeg -i "%a.mp4" -c:v hap "%a.mov"

(dove a = variabile qualsiasi)

<h2><b>2. Per conversione da .mov a _hap.mov:</b></h2>

Entrare in prompt

ffmpeg
cd Desktop (o ovunque tu abbia cartella video)
cd cartella_video
se non era in C, per cambiare directory: cd /d d:
poi per entrare nelle cartelle: cd nomecartella\nomecartella\nomecartella...
inserire così com'è:
for /f "tokens=1 delims=." %a in ('dir /B *.mov') do ffmpeg -i "%a.mov" -c:v hap "%a_hap.mov"

il nome di destinazione va cambiato in _hap.mov perchè se no sovrascrive il file stesso e non riesce a fare la codifica.

altro link utile:

https://gist.github.com/dlublin/e4585b872dd136ae88b2aa51a6a89aac
