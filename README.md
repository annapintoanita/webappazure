passaggi di cui si compone CONTINUOUS INTEGRATION

-CREARE IMMAGINE SU DOCKER (DOCKER FILE)
-TROVARE POSTO DOVE DEPOSITARE L IMMAGINE DAL QUALE ISTANZIARE DAI VARI CONTAINER (DOCKER HUB)-->TRAMITE IL TERMINLE FATTO IL PUSH DELL'IMMAGINE
E RICHIAMARLO.. UTILIZZO DOCKERHUB COME REGISTRY PER DEPOSITARE L'IMMAGINE DEL NOSTRO FILE. IMMAGINE CHE USEREMO PER CREARE ISTANZE DI PRODUZIONE(VARI CONTAINER) QUESTO AVVIENE COME PASSAGGIO DA DOCKER HUB AD AZURE (O NEL MIO CASO aws).
da docker hub rendere pubblica l immagine derivando da essa un container. poteva farsi con docker ma non essendo pubblica il cliente non avrebbe potuto utilizzarla e qyuindi:
-diamo dei collegamenti/ rotte che prendono l immagine da docker hub e aggiornano quando succede o cambia qualcosa
-lanciare i comandi manualmente per creare l'immagine
account github
inserimento dati sottoforma di secrets(github)
(sistemi di storage github secrets, one time password. memorizza i dati che poi una volta inseriti li cancella e li cripta)
noi abbiamo messo user name e password e profile..



 PASSAGGI
-creare webapp
-creare immagine (docker e dockerfile)
usiamo dockerhub come registry
-rendere pubbblica l immagine istanziando un container atraverso cloud (es. azure o aws)
-collegare dockerhub al cloud. se viene aggiornato il registry deve aggiornarsi anche il container pubblico

 COSA BISOGNA AVERE
-account github
-github storage 

-pipeline per automatizzare (push su github, cioè sul main di github)
assicurarsi sempre che sia sincronizzato


NEL DEPLOY 
-FASE DI BUILD 
-FASE DI TEST
-FASE DI DEPLOY

nel deploy PRENDERE DISTRIBUZIONE DI OGGETTI CHE SVOLGONO QUESTE FUNZIONALITà
il deploy fa il pipline che va a serializzare questi passaggi.

per fare la BUILD deve trovare un RUN, fare checkout del nostro repository(aprire il nostro github), loggarsi a dockerhub per prendersi l immagine, fare la build e la push

quindi:
push sul main da github
run e build via runner (per bin/obj) per costruire l'immagine
prendere file da repository 
accedere a dockerhub via dati salvati in github secrets
run e build dell'immagine
caricarla su docker 

fatti i passaggi si attiva sul branch il workflow che abbiamo fatto
il deploy parte solo finita la fase di build 
si deve far partire un altro runner (comando con latest)
uso l azione di azure
completata l immagine su docker hub grazie allo users di azure vado a mettee solo l app name e il blocco di testo 
usare l immagine per generare un container


Aggiunto una fase di test tra build e deploy 

tenere variabili globali (che sono scritte in maiuscolo)

env = variabili di ambiente
creo variabili di ambiente per il fuso orario (perchè portava un'ora indietro e utilizzava il punto invece della virgola)
all'interno dell onget var culture = new CultureInfo("it-IT").
l'ultimo aggiornamento deve esere relativo all'ultimo caricamento, quando è stato istanzaito il container a partire dll'immagine
quindii
nel docker file fare una conversione della data che riceveva per farla andare a scrivere sul file
RUN date + "%d              "

volevamo ci fosse la versione del pacchetto
nel docker file metto la versione specifica oppure passarglielo come argomento dinamicamente
cioè dare nel comando di build un comando aggiuntivo --> docker build --build-arg BUILD_VERSION=2.3.1 -t 

oppure 
andare nel file deploy e istanziare il pacchetto e scriverci la versione dentro
