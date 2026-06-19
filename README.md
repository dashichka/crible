# Audit citoyen des promesses politiques

Un outil **open source** et **neutre** qui aide chaque citoyen à auditer un programme ou une personnalité politique — **avec sa propre intelligence artificielle**.

> L'outil ne juge pas et ne pense pas à votre place. Il **génère une méthode d'audit** (un *prompt* structuré + une liste de sources publiques officielles) que vous collez dans le modèle d'IA de votre choix (ChatGPT, Claude, Le Chat…). Vous gardez la main ; l'outil ne fait que cadrer la rigueur.

## Pourquoi

La plupart des outils d'analyse politique sont des « boîtes noires » qui livrent un verdict. Ici, le parti pris est inverse : **outiller l'esprit critique**, pas le remplacer. La neutralité ne vient pas d'une prétention à l'objectivité, mais de la **transparence totale de la méthode** et de la **priorité donnée aux sources produites par l'État**.

## Ce que le prompt généré impose à l'IA

- **Vérification active** : aller chercher la donnée publique officielle et **citer le lien**, jamais « à vérifier ».
- **Calcul direct** : recalculer les ordres de grandeur (coût d'une mesure, décomposition d'un agrégat) et montrer la formule.
- **Priorité aux sources d'État** : INSEE, budget de l'État, Assemblée nationale, Sénat, HATVP, Légifrance, Eurostat, Conseil d'orientation des retraites, Cour des comptes…
- **Séparation stricte** fait vérifiable / interprétation / non étayé, avec un **code couleur** de fiabilité.
- **Zéro hallucination** : aucun chiffre ni lien inventé ; refus assumé plutôt qu'invention.
- **Neutralité** : aucun jugement, langage non orienté, mêmes critères pour tous les candidats.
- **Raisonnement jusqu'au bout** : coût → financement → impact sur le déficit, la dette, la charge de la dette ; impact par catégorie (salariés, employeurs, retraités, État).
- **Liens logiques entre promesses** : exposés sans conclure à la place du lecteur.
- **Repérage du langage persuasif** (procédés rhétoriques), sans jamais confondre « chargé émotionnellement » et « faux ».

## Utilisation

Ouvrez `site/index.html` dans un navigateur (ou la version en ligne). Choisissez ce que vous auditez, collez le texte du programme, laissez l'outil suggérer les sources, copiez le prompt généré et collez-le dans votre IA avec le document du programme.

## Développement

Site **100 % statique**, sans backend ni base de données : aucune donnée n'est collectée, tout se passe dans le navigateur. Pour développer, il suffit d'ouvrir `site/index.html` — aucune dépendance, aucune compilation.

## Déploiement (Clever Cloud, statique)

```
clever create --type static-apache "audit-promesses"
clever env set CC_WEBROOT "/site"
clever deploy
```

## Structure

```
site/        application web (un seul fichier autonome)
prompts/     le prompt maître (version lisible et documentée)
docs/        méthodologie, charte de neutralité, catalogue des sources publiques
tests/       cas de test fictif pour éprouver la méthode
```

## Neutralité & limites

Cet outil vise la transparence, pas une objectivité absolue. La vérification dépend des sources fournies et de l'IA utilisée : **aucune IA n'est garantie sans erreur**. Lisez toujours les résultats avec esprit critique et recoupez avec les sources primaires.

## Licence

[MIT](LICENSE) — réutilisez, modifiez, partagez. Les données publiques mobilisées relèvent de la Licence Ouverte (Etalab) et licences équivalentes.
