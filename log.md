# Websites bouwen voor gevorderden
## Met behulp van Laravel, Bootstrap, Apache
### Laravel
#### Laravel installeren
Om Laravel te installeren moeten we eerst composer installeren.  
Dit kan met een excecutable maar kan ook via de terminal worden geinstalleerd.  
het install script verandert met elke versie, best is dus om de laatste versie van volgende site te halen:  
<https://getcomposer.org/download/>



```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === 'e115a8dc7871f15d853148a7fbac7da27d6c0030b848d9b3dc09e2a0388afed865e6a3d6b3c0fad45c48e2b5fc1196ae') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

Om hierna de installatie global te maken op het systeem moet deze al da niet met sudo naar een andere map verplaatst worden.

```
mv composer.phar /usr/local/bin/composer
```