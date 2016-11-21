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

bij het installeren van php7.0-gd waren er een aantal dependencies die niet up to date waren (libdg3). volgens raspian waren deze volledig in orde. om dus toch te upgraden voeren we het volgende commando uit: 

	sudo apt-get -t jessie-backports install libgd3


om te testen of alles gelukt is, run je het volgende commando:

    php -v

als er hier iets in de aard van 7.0 staat is alles ok.

###testen
Om apache te testen, surf je vanop de raspberry pi naar 127.0.0.1 of via je computer waar je mee ssh't naar het ip van de pi.

Dan krijg je de standaardpagina van apache te zien. als je een uitgebreide infopagina van je php nodig hebt, dan moeten we eerst een phpinfo-pagina maken.

	sudo echo "<php phpinfo();" >> /var/www/html/phpinfo.php

het kan zijn dat je hier geen rechten hebt, dus om te kunnen schrijven moet je ofwel de map rechten geven voor de pi user, of inloggen via

	sudo su 

als je hierna naar het IP van de pi gaat, krijg je hopelijk alle info van php te zien

##Laravel installeren
###Hiervoor volgen we de guide die opde pagina "laravel installeren" ook staat.

Ik had een paar problemen, aangezien composer laravel niet installeerde op de juiste locatie.
Als we volgend commando invoeren, kunnen we zien waar laravel geinstalleerd is:

	whereis laravel

hieruit kon ik afleiden, dat hij inplaats van in de .composer map te installeren, in de .config map alles had aangemaakt. hierna was het een kwestie van de juiste locatie toe te voegen aan de $PATH en werktte ales.
