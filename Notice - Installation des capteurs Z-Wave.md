# Notice - Installation des capteurs Z-Wave

## 1. Introduction

Avant de commencer, il est à noter qu'une clé Z-Wave est nécessaire pour utiliser les capteurs. Si les capteurs ont déjà été appairés précédemment, il faudra les désapairer avant de les réapairer.

Pour cela, la documentation à suivre est disponible. [ici](https://aeotec.freshdesk.com/support/solutions/articles/6000056439-z-stick-gen-5-user-manual)

Au cas où la documentation n'est plus disponible, voici ce que dit la documentation :

    Inclusion-Mode: Adding/Including Z-Wave Devices into the Z-Wave Network.


    1. To initiate Inclusion-Mode, unplug Z-Stick from the USB connector and then tap the Action Button. (The blue LED will blink slowly.)


    2. To include a new Z-Wave device into the network, simply go to the device with  Z-Stick and press the button on the device you wish to include. (The blue LED on Z-Stick will blink fast during a network neighbour discovery and stay solid for 2 seconds to indicate successful inclusion of the device into the network.)


    3. The blue LED will then return to blinking slowly, indicating readiness for further device inclusions. Repeat step 2 for each device you wish to include.


    4. Tap Z-Stick’s Action Button to turn it off or it will automatically exit the removal mode after 30 seconds of inactivity.


    Removal-Mode: Deleting/ Removing/Excluding Z-Wave Devices from the Z-Wave Network.


    1. To initiate Removal-Mode, unplug  Z-Stick from the USB connector. Then press and hold down the Action Button for approximately 2 seconds. (The orange LED will blink fast.)


    2. To remove a Z-Wave device from the network, simply go to the device with Z-Stick and press the button on the device you wish to remove. (The blue LED on Z-Stick will immediately stay solid for 2 seconds to indicate successful removal from the network.)


    3. The orange LED will then return to blink fast, indicating readiness for further device exclusions. Repeat step 2 for each device you wish to exclude.


    4. Tap Z-Stick’s Action Button to turn it off or it will automatically exit the removal mode after 30 seconds of inactivity.

Pour l'appairage des objets connectés, il faut suivre la documentation des objets, celle des objets que nous avons utilisés est disponible dans la section **Documentation**.

## 2. Initialisation

On considère maintenant un capteur non appairé qu'il faut rajouter au réseau.

Il faut que l'antenne USB soit débranchée, il faut ensuite appuyer sur le bouton central pour que l'antenne USB commence à clignoter en bleu.

Ensuite, il faut aller dans la documentation de l'objet à ajouter pour savoir quelles manipulations effectuer pour signifier à l'objet à ajouter qu'il faut s'appairer.

Lorsque la manipulation a été faite, il faut attendre que l'antenne USB clignote rapidement plusieurs fois en bleu pour signifier que l'objet a été rajouté.

Lorsque tous les objets ont été rajoutés, brancher l'antenne USB au serveur OpenHab.

Se connecter au serveur OpenHab:

## 3. Installation de Z-Wave bindings sur OpenHab

- Cliquer sur "Paramètres"

- Dans la catégorie "Add-ons", cliquer sur "Bindings"

- Dans la liste "openHab Distributions", chercher "Z-Wave Binding" (dans l'ordre alphabétique, donc chercher dans les bindings supplémentaires)

- Installer le bindings

## 4. Ajout de l'antenne USB par fichier .things

- Récupérer le fichier correspondant au Z-Wave serial controller [ici](https://github.com/Projet-INFO-S10/Domus-docs/blob/main/Things/ZWave-Stick.things)

Le mettre dans le dossier correspondant à la sortie de la commande

```
$OPENHAB_CONF/things
```

- Une fois que le fichier a été mis dans le dossier, il faut brancher la clé.

- Pour que la clé usb soit reconnu par le serveur OpenHab, des manipulations peuvent êtres nécessaires. Dans notre cas, le fichier .thing contient une attribution pour le port qui correspond au port utilisé pour la connexion de la clé sur l'ordinateur courant sur Ubuntu. Il faudra peut-être être amené à le modifier pour que cette valeur corresponde au serveur OpenHab. 

- En suivant la documentation de l'objet Z-Wave, il faut maintenir le capteur "éveillé" le temps que la découverte des capteurs proposés par l'objet soit fini. Pour cela en général, il faut appuyer sur un bouton de l'objet pour éviter qu'il ne se mette en veille.

Pour avoir la documentation des objets que nous avons testés, voir la partie **documentation**

- Ensuite dans **paramètres**, **things** un bouton **inbox** rouge apparait en bas, cliquer dessus. Cela devrait proposer les capteurs appairés et trouvables par la clé. Pour chacun d'entre eux, il faut cliquer dessus et faire : **add as a thing**. 

*NB. le bouton "inbox" peut ne pas apparaitre tout de suite, il faut parfois attendre un peu*

- Quand tous les capteurs sont ajoutés, retourner dans **things** cliquer sur le capteur voulu, en haut cliquer sur **Channels** et pour chaque channel, cliquer dessus et enfin cliquer sur **add link to item**, puis **create a new item** puis sur le bouton bleu en bas **link**.

Répéter l'opération pour chaque channel.

## Documentation

- [Aeotec Z-Stick Gen5.](https://aeotec.freshdesk.com/support/solutions/articles/6000056439-z-stick-gen5-user-guide-)
- [Fibaro Flood Sensor](https://manuals.fibaro.com/content/manuals/en/FGFS-101/FGFS-101-EN-T-v2.1.pdf)
- [Fibaro Wall Plug](https://manuals.fibaro.com/content/manuals/en/FGWPEF-102/FGWPEF-102-EN-A-v2.1.pdf)
- [Fibaro Motion Sensor](https://manuals.fibaro.com/content/manuals/en/FGMS-001/FGMS-001-EN-T-v2.1.pdf)
- [Aeotec WallMote Quad](https://aeotec.freshdesk.com/support/solutions/articles/6000162392-wallmote-quad-user-guide-)



## Sources
- https://www.openhab.org/addons/bindings/zwave/
