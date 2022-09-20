# TP 4 - Gestion des paquets
## Exercice 1. Commandes de base
1. Pour mettre à jour votre système avec les commandes sont `sudo apt update` puis `sudo apt upgrade`.
2. Créez un alias “maj” de la ou des commande(s) de la question précédente. `alias maj="sudo apt update && sudo apt upgrade"` Où faut-il enregistrer cet alias pour qu’il ne soit pas perdu au prochain redémarrage ? Il faut le mettre dans `~/.bashrc`
3. Utilisez le fichier `/var/log/dpkg.log` pour obtenir les 5 derniers paquets installés sur votre machine. `tail -5 /var/log/dpkg.log`
4. Listez les derniers paquets qui ont été installés explicitement avec la commande apt install. `apt list -i`
5. Utilisez les commandes dpkg et apt pour compter de deux manières différentes le nombre de total de paquets installés sur la machine (ne pas hésiter à consulter le manuel !). 
	* `dpkg -l | wc -l` ou `apt list -i | wc -l`
	* Comment explique-t-on la (petite) différence de comptage ? La commande apt list -i renvoi unniquement les packets installé via apt install.
	* Pourquoi ne peut-on pas utiliser directement le fichier dpkg.log ? Il n'y a pas que les paquets installés. Il y a aussi les status des paquets par exemple.
6. Combien de paquets sont disponibles en téléchargement sur les dépôts Ubuntu ? `apt list | wc -l` 
7. A quoi servent les paquets glances, tldr et hollywood ? Installez-les et testez-les. 
	* Glances permet de d'avoir des information sur le système.
	*  tldr Résume les pages de manuel
	* hollywood Simuler une fenêtre de hacking comme au cinéma
8. Quels paquets proposent de jouer au sudoku ? Le packet est `sudoku`

## Exercice 2.
* A partir de quel paquet est installée la commande ls ? `dpkg -S /bin/ls`
* Comment obtenir cette information en une seule commande, pour n’importe quel programme ?  `which ls | dpkg -S | cut -d':' -f1`
* Utilisez la réponse à cette question pour écrire un script appelé origine-commande (sans l’extension .sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a installée.
