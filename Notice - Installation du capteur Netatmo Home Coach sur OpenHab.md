## Notice d'installation Netatmo Home Coach sur OpenHab 
----------
**Informations disponibles :**

- Fréquence d’enregistrement: toutes les 5 minutes

- **Température** :
Plage de mesure : 0°C à 50°C
Précision : ± 0,3°C

- **Humidité** :
Plage de mesure : 0 à 100%
Précision : ± 3%

- **Capteur de CO2** :
Plage de mesure : 0 à 5 000 ppm
Précision : ± 50 ppm (de 0 à 1 000 ppm) ou ± 5 % (de 1 000 à 5 000 ppm)

- **Sonomètre** :
Plage de mesure : 35 dB à 120 dB

------------

# 1. Installer l'application 
Installer l'application Netatmo Home Coach sur smartphone : 
- Sur android suivre le lien suivant : https://play.google.com/store/apps/details?id=com.netatmo.homecoach&hl=fr&gl=US&pli=1
- Sur apple : https://apps.apple.com/fr/app/healthy-home-coach/id1131510218
Puis suivre les instructions d'installation permettant de mettre en route le capteur.

## 2. Installer le Binding Netatmo sur OpenHab
- Ouvrir OpenHab
- Cliquer sur "Paramètres" 
- Dans la catégorie "Add-ons", cliquer sur "Bindings" 
- Dans la liste "openHab Distributions", chercher "Netatmo Biding" (dans l'ordre alphabétique, donc chercher dans les bindings supplémentaires)


## 3. Création d'une application Netatmo
- Se connecter avec les identifiants du compte de l'application mobile  sur : https://dev.netatmo.com/
- Une fois connecté cliquer sur `MyApps` sous votre login
- Cliquer sur le bouton `create`
- Compléter les informations demandées

## 4. Connection avec le compte Netatmo
- Retourner sur OpenHab
- Dans "Paramètres", cliquer sur "Things"
- Cliquer sur le bouton bleu "+"
- Choisir "Extension Netatmo"
- Choisir "Compte netamo" (netatmo:account)
- Récuper l'ID client et le client secret dans l'app crée sur Netatmo Connect et les copier dans les champs adaptés sur OpenHab
- Cliquer sur `Create Thing`
- Le pont va se déconnecter / CONFIGURATION_ERROR - c’est normal
- Accéder au lien suivant pour autoriser la connection avec Netatmo connect
http://localhost:8080/netatmo/connect/<_CLIENT_ID_>

- Cliquer sur `Authorize Thing` et suivre les instructions.
- Vérifier que le statut sur OpenHab est bien `Online`

## 5. Récupérer l'adresse mac 
Retourner sur l'application mobile Home Coach
- Afficher le menu à gauche
- Cliquer sur paramétres avancés
- Cliquer sur l'appareil concerné
- Dans la partie information récupérer l'adresse MAC puis la recopier sur OpenHab dans 'ID de l'équipement'

## 6. Connection avec l'appareil
- Retourner dans OpenHab
- Dans "Paramètres", cliquer sur "Things"
- Cliquer sur le bouton bleu "+"
- Choisir "Extension Netatmo"
- Choisir 'Capteur Qaulité Air Intérieur' ( netatmo:home-coach)
- Dans Bridge choisir 'Compte Netatmo'
- Dans ID de l'équipement mettre l'adresse MAC de l'équipement
- Puis cliquer sur create Thing

## 7. Ajouter des channels
- Dans paramétres -> Things cliquer sur 'Capteur Qualité Air Intérieur' sur Channels
- L'ensemble des informations du capteur s'affichent.
- Cliquer sur l'information qui vous intéresse
- Cliquer sur `Add link to Item`
- Puis cliquer sur `Create new Item`
- Enfin cliquer sur `Link`
L'élément apparait alors dans Items.

Effectuer l'atape 7 pour toutes les informations récupérées par le capteur que vous souhaitez obtenir.

-------------------------

#### Sources / Liens utiles
- https://www.openhab.org/addons/bindings/netatmo/
- https://www.netatmo.com/fr-fr/aircare/homecoach

