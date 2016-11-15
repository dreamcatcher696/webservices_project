# installeren van php7/laravel op de raspberry pi
##php7.0 installeren
###bronnen toevoegen
om php 7.0 te installeren op de raspberry pi, moeten we eerst andere bronnen downloaden
    sudo nano /etc/apt/sources.list
dit zorgt ervoor dat apt-get ook van hier kan downloaden.
we voegen de volgende lijnen toe:
    deb http://repozytorium.mati75.eu/raspbian jessie-backports main contrib non-free
    #deb-src http://repozytorium.mati75.eu/raspbian jessie-backports main contrib non-free
    
Nu moeten we certificaten toevoegen. bij mij lukt het installeren van de juiste key niet. hierdoor kunnen de paketten
niet geverifieerd worden, maar dit heeft geen invloed op de verdere installatie (bbuiten dat je 1x meer 'y' moet typen)
    sudo gpg --keyserver pgpkeys.mit.edu --recv-key CCD91D6111A06851
    sudo gpg --armor --export CCD91D6111A06851 | sudo apt-key add -
Hierna updaten we het hele systeem:
    sudo apt-get update

###pakketten installeren 
nu gaan we alle php7 pakketen installeren die we nodig hebben, om onze apache server te runnen:
    apt-get install apache2 php7.0 php7.0-curl php7.0-gd php7.0-imap php7.0-json php7.0-mcrypt php7.0-mysql php7.0-opcache php7.0-xmlrpc libapache2-mod-php7.0

om te testen of alles gelukt is, run je het volgende commando:
    php -v
als er hier iets in de aard van 7.0 staat is alles ok.

###testen
Om apache te testen, surf je vanop de raspberry pi naar 127.0.0.1 of via je computer waar je mee ssh't naar het ip van de pi.
