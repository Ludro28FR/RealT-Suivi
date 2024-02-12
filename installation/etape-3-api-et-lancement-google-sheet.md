---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Etape 3 : API et Lancement Google Sheet

1 : Rendez-vous sur Gnosis Scan et créez vous un compte. Cela vous permettra d'avoir une clé API. Une fois votre compte créé, rendez-vous dans l'onglet : "[API-KEYs](https://gnosisscan.io/myapikey)",

2 : Cliquez sur "Add" à droite de "My API Keys",

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 110434.png" alt=""><figcaption><p>Screen pour le 2</p></figcaption></figure>

3 : Donnez un nom par exemple "RealT Google Sheet", puis cliquez sur "Continue",

4 : Une fois cela fait, une Clé API apparrait juste en dessous de "Api-Key Token". Copier cette clé API et rendez-vous sur votre Google Sheet que vous avez importé à [l'étape 1](etape-1-importation-google-sheet.md).

5 : Sur votre Google Sheet, cliquez sur l'onglet "Extensions" puis sur "Apps Script",

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 110923.png" alt=""><figcaption><p>Screen pour le 5</p></figcaption></figure>

5 Bis : Si vous avez une Erreur 400, suivez ce [lien](https://script.google.com/home/my), puis double cliquez "RealT Suivi"&#x20;,

6 : Une fois arrivé sur AppsScript, remplacer "YOUR-KEY" de "const KeyAPIGnosis" :

```javascript
const keyAPIGnosis = "YOUR-KEY"
```

```javascript
const keyAPIRealT = "IFKZNCKE"
```

7 : Pour avoir votre clé API RealT Communautaire, rendez-vous sur ce [lien](https://forms.gle/nFVfuxk8WRZBDR6u8) et remplissez le formulaire. Une clé API vous sera envoyé sur votre mail renseigné. (Comptez quelque jours pour avoir votre clé). Une fois que vous avez reçu votre clé, remplacer "YOUR-KEY" de "const keyAPIRealT" :

```javascript
const keyAPIRealT = "YOUR-KEY"
```

```javascript
const keyAPIRealT = "a0de50bb-prepord-1ee0"
```

8 : Une fois cela fait, remplacer "YOUR-WALLET" par votre wallet commencant par 0x. Si vous avez plusieurs wallet, séparez les par une virgule et des "" :

```javascript
const walletToken = ["YOUR-WALLET"];
```

```javascript
const walletToken = ["0x00000000000000000"];
```

9 : Une fois cela fait, rendez-vous à gauche dans l'onglet "Déclencheurs",

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 112414.png" alt=""><figcaption><p>Screen pour le 9</p></figcaption></figure>

10 : Cliquez sur "Ajouter un déclencheur" en bas à droite, puis dans "Choisir la fonction à exécuter", trouver "autoMenu", puis dans "Paramètres de notification d'échec", trouver "Recevoir une notification immédiatement". Cliquer ensuite sur "Enregistrer",

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 112638.png" alt=""><figcaption><p>Screen 10</p></figcaption></figure>

11 : Une page s'ouvre pour vous demander à vous connecter à votre compte google. Cela est normal nous sommes entrain de donner les autorisations au script. Connecter votre compte google, puis vous arriver sur une page de warning. Cliquer sur "Advenced". Puis sur "Go to RealT Suivi (unsafe)" en bas.

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 113215.png" alt=""><figcaption><p>Screen pour le 11</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 113710.png" alt=""><figcaption><p>Screen pour le 12</p></figcaption></figure>

12 : Puis tout en bas, cliquez sur "Allow". Une fois fait votre premier déclencheur est créé,

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 114003.png" alt=""><figcaption><p>Screen pour le 12</p></figcaption></figure>

13 : Nous allons créer les autres déclencheurs, nécessaires pour le bon fonctionnement du programme. Cliquer de nouveau sur "Ajouter un déclencheur", puis dans "Choisir la fonction à exécuter", trouver "autoRentReport" et régler ce déclencheur pour qu'il se déclenche toutes les heures,

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 114503.png" alt=""><figcaption><p>Screen pour le 13</p></figcaption></figure>

14 : Faites un déclencheur pour les fonctions suivantes :&#x20;

("Choisir la fonction à exécuter" - "Sélectionnez la source de l'évènement" - Sélectionnez le type de déclencheur temporel" - "Sélectionnez un intervalle en heures")

&#x20;\- "autoMailToDriveAndSheet" - Déclencheur horaire - Quotidien - Entre 0h et 1h,

&#x20;\- "autoUpdate1" - Déclencheur horaire - Quotidien - Entre 0h et 1h,

&#x20;\- "autoUpdate2" - Déclencheur horaire - Quotidien - Entre 1h et 2h,

&#x20;\- "autoUpdate3" - Déclencheur horaire - Quotidien - Entre 2h et 3h,

Bien IMPORTANT entre "autoUpdate1" et "autoUpdate2", il faut 1h d'ecart et la même chose entre "autoUpdate2" et "autoUpdate3",

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 115027.png" alt=""><figcaption><p>Screen pour le 14</p></figcaption></figure>

15 : Une fois cela fait vous pouvez relancer votre Google Sheet en faisant F5, attendez quelques secondes et dans la barre d'en haut à droite de "Aide" un onglet "RealT" apparait. Dans un premier temps, lancer "RealT  API Création", puis une fois fini "RealT API / Balance Update", puis une fois fini "RealT Mail" puis "Rent Report",

<figure><img src="../.gitbook/assets/Capture d&#x27;écran 2024-02-12 115934.png" alt=""><figcaption><p>Screen pour le 15</p></figcaption></figure>

16 : Dans la feuille Suivi - Rent, chercher la colonne qui a pour en-tête "Colonne à Supprimer après votre première ligne de Rents" et supprimer cette colonne une fois que votre première ligne de Rent est apparue dans vote Google Sheet,

Voila, l'installation est finie : je vous invite à aller voir l'onglet Utilisation, pour savoir comment utiliser le Google Sheet. Nota : Il est fortement recommandé pour les utilisateurs ayant déjà des propriétés de remplir une feuille par bien, pour le bon fonctionnement du script. Voir [ceci](../utilisation/bien-des-proprietes.md) pour savoir quelles informations mettre.
