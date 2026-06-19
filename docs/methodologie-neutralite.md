# Méthodologie & charte de neutralité

## Posture fondatrice (à reprendre telle quelle dans le projet)

> Cet outil ne prétend pas à l'**objectivité** — il prétend à la **transparence** et à la **pluralité des sources**. C'est exactement ce qui rend AllSides défendable et ce qui fait critiquer MBFC (évaluateur unique). La neutralité absolue n'existe pas ; la neutralité *vérifiable* (méthode publique, sources d'État, refus de l'interprétation non sourcée) existe.

L'outil **ne juge pas** un candidat. Il génère un prompt qui :
1. force le LLM de l'utilisateur à ne s'appuyer que sur des sources fournies/vérifiables (priorité : sources d'État) ;
2. interdit l'opinion, le jugement de valeur et le mimétisme politique ;
3. distingue fait vérifiable / interprétation / non étayé ;
4. produit un rapport **auditable** (chaque affirmation = une source) avec disclaimer.

## Les 9 principes (distillés d'AllSides, IFCN, Polimètre)

1. **Multi-sources, jamais une source unique** — croiser au minimum 2 sources indépendantes.
2. **Sources d'État en priorité** — la donnée brute publique avant toute interprétation.
3. **Distinguer 3 axes orthogonaux** : (1) orientation/affiliation, (2) fiabilité factuelle, (3) faisabilité. Ne jamais les fusionner.
4. **Transparence intégrale** de la méthode, des sources et des critères (publiés, critiquables).
5. **Niveau de confiance affiché** par affirmation (élevé/moyen/faible).
6. **Fait vs opinion** rigoureusement séparés ; pas de qualificatif mélioratif/péjoratif.
7. **Affiliation = fait sourcé, pas étiquette** (cf. sources-publiques.md, dernier §).
8. **Daté et versionné** : toute donnée porte sa date et sa provenance.
9. **Limites explicites** : afficher ce qui n'a pas pu être vérifié = gage de crédibilité.

## Grille d'évaluation d'une promesse (étalon-or : Polimètre / CPPG, U. Laval)

Catégories à règles objectives, automatisables, comparables à l'international :
- **Tenue** : acte officiel sanctionné (loi/règlement/traité).
- **Partiellement tenue** : engagée mais incomplète, ou compromis assumé.
- **En cours** : entamée, ni complète ni compromise.
- **Rompue** : fin de mandat sans aboutissement.
- **Pas encore évaluée** : aucune action formelle (disparaît en fin de mandat).

Règle critique (Full Fact) : **le LLM ne tranche jamais seul la véracité** — il détecte, classe, source ; l'humain valide. C'est le garde-fou anti-hallucination ET anti-IA-Act.

## Les modificateurs du générateur (ce que l'utilisateur paramètre)

Le site assemble le prompt maître + injecte les choix de l'utilisateur :

| Modificateur | Options |
|---|---|
| **Objet de l'audit** | Programme / Parcours & positions / Cohérence de l'entourage / Faisabilité budgétaire / Tenue des promesses passées |
| **Niveau de profondeur** | Synthèse / Détaillé / Exhaustif (fait par fait) |
| **Sources à mobiliser** | cases à cocher du catalogue (INSEE, budget, AN/Sénat, HATVP, Légifrance, Eurostat…) |
| **Périmètre temporel** | mandat en cours / toute la carrière / période donnée |
| **Format de sortie** | tableau / rapport / fiche comparative multi-candidats |
| **Entrées utilisateur** | nom du candidat + PDF du programme (collés dans SON LLM) |

Le générateur produit un **prompt prêt à coller** + une **checklist de sources à fournir** (liens directs vers les portails d'État concernés selon les cases cochées).

## Garde-fous anti-hallucination (résumé — détail dans prompt-maitre.md)

- **Grounding strict** : ne répondre qu'à partir des sources fournies ; sinon « Non étayé ».
- **Citations obligatoires** : 1 affirmation = 1 citation `[Cx]` ou lien vérifiable.
- **Chain-of-Verification** : brouillon → questions de contrôle → réponses isolées → version révisée.
- **Abstention valorisée** : refuser > inventer. Niveaux de confiance explicites.
- **Disclaimer systématique** : « réduction ≠ élimination ; à recouper, validation humaine requise ».

## Modes d'audit & vérification active (v0.2)

**Deux modes** (cases du générateur) : `PROGRAMME` (faisabilité des mesures), `PERSONNE` (profil factuel), ou les deux.

**Mode PERSONNE** — 8 dimensions, toutes sourcées : biographie & mandats / déclarations publiques / entourage / business & intérêts (HATVP) / associations & soutiens / **positionnement international ventilé (Commission UE, pays européens, USA, Chine, Russie, autres)** / déplacements / **cohérence** (discours ↔ parcours ↔ votes ↔ intérêts). Garde-fou : liens factuels documentés seulement, jamais d'insinuation.

**Vérification active (pas de renvoi)** : le prompt ne dit plus « à vérifier via X », il vérifie et cite le lien. Trois conséquences :
1. Le LLM doit avoir un **accès web** OU recevoir les **données dans le contexte** → le site injecte les données d'État selon les mesures détectées.
2. Un **coût** est une **estimation attribuée** (candidat / OFCE / COR / Institut Montaigne…) avec fourchette + date — jamais un chiffre inventé.
3. « Invérifiable » n'est admis que si la donnée n'existe pas publiquement, et toujours accompagné de la **requête exacte**.

**Statut de vérification** (remplace l'ancienne « confiance ») : ✅ Vérifié / 🟡 Partiel (estimation sourcée) / ⚪ Invérifiable en l'état / 🔴 Contredit.

**Faisabilité budgétaire** : pour chaque mesure → Coût (sourcé) | Financement proposé par le candidat | Écart / impact sur le budget France. Le solde global se raisonne sur le **programme entier**, jamais sur un extrait.

## Limites à assumer publiquement

- Un prompt réduit fortement mais **n'élimine pas** l'hallucination (confirmé par la doc Anthropic).
- Le LLM hallucine surtout les **liens/références** → n'accepter que des URL ouvrables par l'utilisateur.
- Knowledge cutoff + fenêtre de contexte → fournir le programme complet, dater les sources.
- La dimension "tendance" n'est pas neutralisable → la remplacer par des affiliations factuelles sourcées.
