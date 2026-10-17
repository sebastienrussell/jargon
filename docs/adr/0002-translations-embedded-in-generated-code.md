# Translations embarquées dans le code généré

Le plugin génère les Translations directement en Kotlin dans `commonMain` au lieu de copier le Translation file comme ressource lue à l'exécution. Le JSON ne sert donc qu'au build : il n'y a pas de lecture de ressources par plateforme (`expect/actual`), pas de parsing au démarrage et pas de dépendance runtime à une librairie JSON. La future synchronisation serveur restera possible en superposant une couche distante qui surcharge ces Translations embarquées au runtime, plutôt qu'en remplaçant un fichier.
