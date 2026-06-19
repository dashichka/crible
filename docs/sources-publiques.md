# Sources publiques pour l'audit de promesses politiques

Principe directeur (consigne du 19/06/2026) : **privilégier les sources produites par l'État** = garantie maximale de neutralité de la donnée. Les sources sont classées par dimension d'audit, puis par tier de confiance.

> Distinction capitale : une source d'État garantit la **neutralité de la donnée brute** (un chiffre INSEE, un vote à l'AN, une ligne de budget). Elle ne garantit PAS la neutralité de la **sélection** ni de l'**interprétation** — ça, c'est le rôle de la méthodologie + des garde-fous du prompt.

---

## TIER 1 — Sources d'État / officielles (neutralité maximale)

### A. Faisabilité budgétaire d'une promesse ("d'où sortent les 100 € ?")
| Source | Ce qu'on vérifie | Accès | Licence |
|---|---|---|---|
| **data.economie.gouv.fr** (Bercy) | Exécution budgétaire, recettes/dépenses, PLF/LFI, indicateurs de performance PAP/RAP | API Opendatasoft Explore v2.1 (`/api/explore/v2.1/...`) | Licence Ouverte 2.0 |
| **budget.gouv.fr / performance-publique** | Repères PLF→LFI→exécution, doctrine LOLF | Portail (pas d'API ; données sur data.economie) | LO 2.0 |
| **OFGL** (data.ofgl.fr) | Finances des communes/départements/régions : dette, fiscalité, investissement | API Opendatasoft v2.1 | LO 2.0 |
| **Cour des comptes** | Contrôle d'exécution, finances locales — l'autorité indépendante | XML depuis 2016 + PDF | LO 2.0 |
| **DGFiP** | Comptes des collectivités | CSV via data.gouv.fr | LO 2.0 |

**Chaîne de vérif d'une promesse budgétaire : PLF (proposé) → LFI (voté) → RAP + indicateurs (exécuté/atteint).**

### B. Réalité socio-économique (le fait contre la promesse)
| Source | Ce qu'on vérifie | Accès | Licence |
|---|---|---|---|
| **INSEE — Melodi** | Catalogue complet : démographie, emploi, salaires, prix, logement | API REST (`api.insee.fr/melodi/`), 30 appels/min sans clé | LO 2.0 |
| **INSEE — BDM** | Séries macro : inflation, chômage BIT, PIB | SDMX sans clé | LO 2.0 |
| **DREES** | Santé / social : soins, minima sociaux, retraites | API sans auth | LO 2.0 |
| **DARES** | Travail / emploi : demandeurs d'emploi, formation | API sans auth | LO 2.0 |
| **Banque de France — Webstat** | Taux, crédit, endettement, défaillances | API (clé, 10 000/j) | Données ouvertes BdF |
| **Eurostat** | Comparaison FR vs UE : dette/déficit, chômage, pauvreté | API sans clé | CC BY 4.0 |

### C. Parcours réel & positions prises (cohérence sur la carrière)
| Source | Ce qu'on vérifie | Accès | Licence |
|---|---|---|---|
| **Assemblée nationale Open Data** | Scrutins nominatifs (ce que la personne a VOTÉ), amendements, comptes rendus | Bulk ZIP XML/JSON | LO 2.0 |
| **Sénat Open Data** | Dossiers législatifs, amendements, débats, votes | Dumps PostgreSQL + CSV | LO 2.0 |
| **Vie-publique.fr (DILA)** | Base de ~150 000 discours publics (qui, quand, à quelle occasion) | Bulk + métadonnées data.gouv.fr | LO 2.0 |
| **Légifrance / JORF (API PISTE)** | Traduction réglementaire réelle d'une promesse : lois promulguées, nominations, décrets | API REST, OAuth2 obligatoire | LO 2.0 |

### D. Intégrité, entourage, conflits d'intérêts
| Source | Ce qu'on vérifie | Accès | Licence |
|---|---|---|---|
| **HATVP — déclarations** | Intérêts, patrimoine, instruments financiers (~8 000 responsables) | Bulk CSV/XML | LO 2.0 |
| **HATVP — répertoire lobbying** | Actions de lobbying, qui a contacté qui, moyens financiers | Bulk JSON (consolidé nocturne) | LO 2.0 |

> ⚠️ HATVP = **déclaratif non audité**. À présenter comme tel, jamais comme une vérité établie.

### E. Élections & UE
| Source | Ce qu'on vérifie | Accès | Licence |
|---|---|---|---|
| **resultats-elections.interieur.gouv.fr** | Résultats officiels de tous les scrutins | Bulk CSV/XML | LO 2.0 |
| **Parlement européen — Open Data** | Votes des eurodéputés, plénières, procédures (meilleure API "votes" du lot) | API REST v2 sans auth (500 req/5 min) | CC BY 4.0 |
| **data.europa.eu** | Méta-portail UE | Search API + SPARQL | CC BY 4.0 |

---

## TIER 2 — Civic-tech bâtie SUR la donnée publique (utile, mais pas État)

Ces projets enrichissent/normalisent la donnée d'État. Très pratiques, mais **licence à respecter** (souvent ODbL = partage à l'identique) et **méthodo à signaler** (certains indices sont interprétatifs).

| Source | Apport | Licence | Vigilance |
|---|---|---|---|
| **NosDéputés.fr / NosSénateurs.fr** (Regards Citoyens) | Mêmes données AN/Sénat, **normalisées + API propre** (`/json /csv /xml`) | ODbL | Republier les dérivés (share-alike) |
| **La Fabrique de la Loi** | Parcours d'une loi (navettes AN↔Sénat) | ODbL | Périmètre = lois sélectionnées |
| **Datan.fr** | Scores de participation, loyauté au groupe, cohésion | GPL / LO | **Indices = interprétation**, à signaler |
| **Wikidata** | Mandats horodatés (modèle "position held" P39) — socle mondial | CC0 (aucune contrainte) | Donnée contributive, à recouper |
| **Google Fact Check Tools API** | Base mondiale de fact-checks existants (claim-matching AVANT de juger) | CC BY | Croisement, pas source primaire |

---

## Ce que les sources d'État ne donnent PAS : la "tendance gauche/droite"

C'est le point honnête à intégrer. **Aucune source d'État ne tague l'orientation politique** d'un média, d'une école ou d'un entourage — l'État ne produit pas ce jugement, par construction.

Conséquences pour le projet :
1. La dimension "tendance" (à la Ground News) **ne peut pas être neutre via des sources d'État**. En France, il n'existe même pas d'équivalent rigoureux d'AllSides (le Décodex mesure la *fiabilité*, pas l'orientation, et n'est plus maintenu).
2. Études concordantes (Institut Montaigne/médialab Sciences Po, Fondation Descartes) : le paysage français se structure sur un axe **"institutionnels vs anti-élites"**, PAS sur l'axe gauche/droite à l'américaine. Importer une grille L/C/R US = réducteur et contestable.
3. **Recommandation** : remplacer "tendance gauche/droite" (interprétatif, indéfendable) par des **affiliations factuelles et sourcées** :
   - appartenance à un parti → registres officiels / HATVP / Wikidata
   - votes effectifs → AN/Sénat Open Data
   - financements/lobbying déclarés → HATVP
   - propriété d'un média cité → carte "Médias français, qui possède quoi" (Le Monde diplo + Acrimed, données ouvertes sur GitHub `mdiplo/Medias_francais`)
   
   Un fait sourcé ("a voté contre le texte X le JJ/MM") est infalsifiable. Une étiquette ("connoté à gauche") ne l'est jamais.
