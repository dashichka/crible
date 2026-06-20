# Prompt maître — Crible

## Source unique

Le prompt complet et toujours à jour est produit par le générateur du site : `site/index.html`, fonction `buildPrompt()`. Pour obtenir le texte intégral courant, ouvrez [crible.cleverapps.io](https://crible.cleverapps.io), réglez les options, puis cliquez sur « Copier le prompt » (ou « Télécharger .md »).

Ce document ne recopie volontairement pas le texte intégral du prompt : éviter une seconde copie manuelle élimine tout risque de désynchronisation entre la doc et l'outil réellement utilisé. Il décrit la structure et les règles invariantes.

## Structure du prompt (ordre des sections)

Le prompt est assemblé dynamiquement selon les cases cochées ; voici toutes les sections possibles, dans l'ordre :

1. RÔLE : analyste factuel impartial, ne juge jamais.
2. SUJET DE L'AUDIT : le ou les candidats saisis.
3. LANGUE DE LA RÉPONSE : la langue choisie pour le rapport.
4. MODE COMPARATIF (si plusieurs candidats) : mêmes critères pour chacun, tableaux côte à côte.
5. RÈGLE DE LISIBILITÉ : phrases complètes, aucune abréviation non explicitée, contextualisation des noms propres.
6. VÉRIFICATION ACTIVE ET CALCUL DIRECT : vérifier réellement, calculer soi-même les ordres de grandeur, ne jamais inventer un chiffre.
7. SOURCES = LIENS CLIQUABLES VÉRIFIÉS.
8. HIÉRARCHIE DES SOURCES : État/institution > organisme indépendant > presse > source partisane. Les réseaux sociaux ne sont jamais une preuve d'un fait (seulement la trace d'un propos publié par la personne). Tout média cité est suivi de son orientation politique documentée entre parenthèses (ou « orientation non établie »).
9. SOURCES CONTRADICTOIRES : présenter les deux, privilégier la plus récente et primaire, signaler le désaccord.
10. DATATION ET FRAÎCHEUR : dater chaque donnée, préférer la plus récente, vérifier en ligne le récent.
11. NEUTRALITÉ (5 interdits) ET ANTI-DÉSINFORMATION : pas de jugement, pas d'opinion, pas de formule vague.
12. CLASSEMENT DES ÉNONCÉS : fait vérifiable / interprétation / non étayé.
13. STATISTIQUES CITÉES (si dimension cochée) : double vérification (source citée + base indépendante).
14. LANGAGE PERSUASIF (si dimension cochée) : repérer les procédés rhétoriques sans juger.
15. MÉTHODE DE VÉRIFICATION : brouillon, questions de contrôle, version finale sans le non-étayé.
16. LÉGENDE COULEUR : Vérifié / À nuancer / Non vérifiable / Contredit.
17. AUDIT DU PROGRAMME (si mode programme) : faisabilité jusqu'au bout (coût, financement, déficit, dette, charge de la dette), décomposition des agrégats, impact par catégorie d'acteur, mécanismes contradictoires ; liens logiques entre promesses sans conclusion.
18. AUDIT DE LA PERSONNE (si mode personne) : profil développé ; pour l'entourage, synthétiser la position politique de chaque proche ; positionnement international par grandes aires (Europe, Amériques, Afrique, Moyen-Orient, Russie, Chine, Asie, Océanie), uniquement les aires documentées ; cohérence traitée en profondeur (plusieurs thèmes, déclarations datées face aux votes, lois, décrets, nominations et arbitrages, sans conclusion vague).
18bis. PROCÉDURES JUDICIAIRES (obligatoire dans tous les cas, quel que soit le mode) : enquêtes, mises en examen, poursuites, condamnations, relaxes du candidat et de ses proches, datées et sourcées, présomption d'innocence respectée.
19. GLOSSAIRE CITOYEN : définir chaque terme technique en une phrase.
20. AUTO-CRITIQUE FINALE : lister honnêtement les angles morts.
21. FORMAT DE SORTIE : plan numéroté du rapport attendu.
22. EXEMPLE DE FORMAT ATTENDU : un exemple fictif pour caler le style.
23. ENTRÉES : candidat, type d'audit, dimensions, période, programme, sources.

## Règles invariantes (l'âme de l'outil)

- Neutralité par transparence de la méthode, pas par prétention à l'objectivité.
- Priorité absolue aux sources produites par l'État.
- Zéro hallucination : refus assumé plutôt qu'invention ; aucun chiffre ni lien inventé.
- Séparation stricte faits / interprétations / non étayé.
- Le langage persuasif est repéré sans confondre « chargé émotionnellement » et « faux ».
- Sur les promesses liées, exposer les interactions sans jamais conclure à la place du lecteur.

## Historique des versions
- v0.5 : hiérarchie des sources, sources contradictoires, datation, glossaire, auto-critique, exemple de format.
- v0.4 : raisonnement budgétaire jusqu'au bout, décomposition des agrégats, impact par catégorie, mécanismes contradictoires, liens logiques entre promesses.
- v0.3 : lisibilité citoyenne, calcul direct, liens cliquables, légende couleur, modes Programme/Personne, comparatif.
- v0.1 à 0.2 : socle (neutralité, anti-hallucination, citations, vérification, priorité aux sources d'État).
