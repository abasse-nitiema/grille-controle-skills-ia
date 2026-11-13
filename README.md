# Grille de contrôle avant installation d'un skill ou d'un plugin IA

Une liste de points à vérifier avant d'installer un skill, un plugin ou un connecteur dans un assistant IA qui a accès à vos fichiers, à votre terminal et à vos outils métier.

## Pourquoi cette grille

Un skill n'est pas un document passif. C'est un jeu d'instructions qui pilote un assistant disposant de vos droits d'accès. Installé sans contrôle, il peut lire vos dossiers, exécuter des commandes, se connecter à des serveurs distants et transmettre ce qu'il trouve, souvent sans que rien d'anormal apparaisse à l'écran.

Le risque n'est pas théorique. Les éditeurs eux-mêmes l'ont documenté : la bibliothèque de plugins juridiques publiée par Anthropic consacre un module entier au contrôle de confiance des contributions communautaires, en rappelant qu'un professionnel qui installe un skill trouvé au hasard installe du code qui accède à ses dossiers clients.

Cette grille ne demande aucune compétence en développement. Elle demande de la méthode.

## Comment l'utiliser

Parcourez les six sections avant toute installation. Chaque point se vérifie en ouvrant un fichier ou une page, sans rien exécuter. Si un point reste sans réponse claire, considérez-le comme non validé.

La règle de décision figure à la fin.

## A. La source

**1. Le propriétaire du dépôt.** Vérifiez le compte sous lequel le dépôt est publié, pas son nom. Les copies, appelées forks, portent le même nom que l'original mais ne sont maintenues par personne. Seul le compte de l'éditeur fait foi.

**2. L'activité réelle.** Regardez la date du dernier commit et le nombre de contributeurs. Un dépôt abandonné depuis longtemps ne recevra pas de correctif en cas de faille.

**3. La licence.** Une licence absente est un signal. Elle indique soit une négligence, soit une volonté de ne pas encadrer l'usage. Vérifiez aussi que la licence autorise votre usage, notamment en contexte commercial.

**4. L'identité de l'auteur.** Un auteur identifiable, avec un historique public et des contributions ailleurs, engage sa réputation. Un compte créé récemment et sans autre activité n'engage rien.

## B. Ce qui s'exécute

C'est la section la plus importante. Ouvrez ces fichiers avant tout le reste.

**5. Les hooks.** Cherchez un dossier `hooks/` ou un fichier `hooks.json`. Les hooks sont des commandes lancées automatiquement, sans validation à chaque usage. Un fichier vide ou absent est le cas favorable. Tout hook présent doit être lu ligne par ligne et compris.

**6. Les scripts.** Cherchez les fichiers en `.sh`, `.py`, `.js` ou `.ps1`. Pour chacun, posez trois questions : que fait-il, à quoi accède-t-il, vers où envoie-t-il quelque chose. Une commande réseau dans un script dont ce n'est pas l'objet annoncé est un signal d'alerte.

**7. Les dépendances.** Si le plugin installe des bibliothèques externes, vérifiez lesquelles. Une dépendance compromise contamine tout ce qui l'utilise.

## C. Les instructions

**8. Les consignes anormales.** Lisez les fichiers d'instructions et cherchez les formulations qui demandent de lire des fichiers de configuration, de transmettre du contenu, de contourner une validation ou de ne pas informer l'utilisateur. Un skill légitime décrit une méthode de travail, il ne demande pas de discrétion.

**9. Le contenu dissimulé.** Certaines instructions malveillantes sont cachées : texte en blanc sur fond blanc, balises invisibles au rendu, caractères de contrôle. Ouvrez les fichiers en mode texte brut, pas en aperçu, et comparez la longueur du fichier à ce que vous voyez.

## D. Les connecteurs

**10. Les adresses déclarées.** Ouvrez le fichier de configuration des connecteurs, souvent nommé `.mcp.json`. Vérifiez chaque adresse : elle doit correspondre au domaine officiel du service annoncé. Le nom affiché n'est qu'une étiquette, il se falsifie en une seconde.

**11. L'étendue des accès.** Demandez-vous à quelles données chaque connecteur donne accès, et si cet accès est nécessaire au service rendu. Un skill de relecture de documents n'a pas besoin d'accéder à votre messagerie.

## E. L'essai

**12. Le bac à sable.** Testez tout skill inconnu dans un dossier vide, avec des documents fictifs, et avec tous les connecteurs désactivés. Observez ce qu'il demande à faire avant de l'approcher de vos dossiers réels.

**13. La surveillance du premier usage.** Pendant le premier test, restez attentif aux actions que l'assistant propose et aux fichiers qu'il consulte. Une lecture de fichiers sans rapport avec la tâche demandée doit interrompre le test.

## F. La durée

**14. Les mises à jour.** Un skill sain en version 1.0 peut être compromis en version 1.1, par un changement de mainteneur ou par une intrusion. Désactivez les mises à jour automatiques, ou acceptez de relire ce qui change.

**15. Le journal d'installation.** Tenez une trace écrite de ce que vous avez installé, depuis quelle source, à quelle date, et sous quelle licence. C'est ce qui vous permettra de réagir vite le jour où une faille est annoncée.

## Règle de décision

Les points de la section B sont bloquants. Un hook ou un script que vous ne comprenez pas suffit à ne pas installer, quelle qu'en soit la source.

Les autres points se pondèrent. Un dépôt officiel, actif, sans code exécutable et sans connecteur superflu peut être installé après une lecture rapide. Un dépôt inconnu demande le parcours complet et un essai en bac à sable.

En cas de doute, l'absence d'installation ne coûte que le temps que l'outil aurait fait gagner. L'installation d'un skill malveillant coûte la confidentialité de ce à quoi il a accédé.

## Limites

Cette grille réduit le risque, elle ne l'annule pas. Elle ne détecte pas une compromission sophistiquée, et elle ne remplace pas la politique de sécurité de votre organisation. Si vous manipulez des données soumises à une obligation contractuelle de confidentialité, la question se tranche avec votre responsable informatique avant de se trancher avec une liste de contrôle.

## Contributions

Les propositions d'ajout sont bienvenues. Ouvrez une issue ou une pull request.

---

Document rédigé par Abasse NITIEMA. Réutilisable et modifiable, sous licence libre.
