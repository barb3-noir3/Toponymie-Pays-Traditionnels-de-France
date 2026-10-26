# Méthodologie

Ce document fixe les règles de recherche et de saisie de la base. Il vise une chose : qu'on puisse **vérifier chaque information** et que deux contributeurs saisissent la même donnée de la même façon.

---

## 1. Principes

1. **Pas de source, pas de donnée.** Toute forme ancienne et toute étymologie doivent pouvoir être retrouvées par un tiers.
2. **La forme ancienne prime sur la forme moderne.** On n'explique pas un nom d'après sa graphie actuelle (« Agonges » ≠ « à Gonge »), mais d'après ses attestations les plus anciennes.
3. **La série prime sur le cas isolé.** Une explication est plus solide si elle s'inscrit dans une série connue (les noms en *-acum*, la série bourbonnaise *-anges/-onges*…).
4. **Distinguer le fait de l'hypothèse.** L'attestation est un fait daté ; l'étymon est une reconstruction. Le degré de confiance est indiqué dans la colonne `Certitude`.
5. **Garder la trace des débats.** Une hypothèse écartée ne s'efface pas : elle passe en `Notes`, avec la raison du rejet.

## 2. Hiérarchie des sources

Par ordre de fiabilité décroissante :

| Rang | Type de source | Exemples |
|---|---|---|
| 1 | **Documents originaux** : chartes, cartulaires, pouillés, terriers, monnaies, inscriptions | Cartulaire de Sauxillanges, pouillé du diocèse de Bourges, monnaies mérovingiennes |
| 2 | **Dictionnaires topographiques** qui relèvent ces documents | DicoTopo (CTHS), Chazaud (Allier, 1881), dictionnaires de la Nièvre et de la Saône-et-Loire |
| 3 | **Ouvrages de toponymie scientifique** | Nègre (TGF), Dauzat et Rostaing, Deroy et Mulon, *Revue internationale d'onomastique* (RIO) |
| 4 | **Monographies locales et sites d'érudition** | Bonin, monographies communales, *Patrimoine des communes de l'Allier* |
| 5 | **Sources de seconde main non vérifiées** | Wikipédia (fr, oc), blogs, sites de mairies |

**Règles :**
- Une source de rang 5 ne suffit jamais seule. Elle sert de piste : il faut remonter à l'ouvrage qu'elle cite.
- Tant qu'on n'a pas pu remonter à l'original, la mention « via Wikipédia » ou « réf. à vérifier » reste **obligatoire**. On ne cite jamais Nègre ou Dauzat comme si on les avait consultés quand on les a lus chez un tiers.
- En cas de désaccord entre deux sources de même rang, on retient l'avis le plus récent et le mieux argumenté. L'autre est consigné en `Notes`.
- En cas de désaccord entre deux rangs, le rang supérieur l'emporte, sauf démonstration contraire publiée.

## 3. Démarche pour traiter une commune

1. **Relever toutes les formes anciennes disponibles** (DicoTopo, Chazaud, Nègre…) et les classer par date.
2. **Retenir la plus ancienne forme fiable** pour `Forme ancienne` et `Date / siècle`. Les autres formes utiles passent en `Notes`.
3. **Identifier le formant** : radical, suffixe (*-acum*, *-iacum*, *-etum*, *-onicas*…), éventuel déterminant (*Saint-*, *-le-Châtel*…).
4. **Chercher l'étymon dans les ouvrages de rang 3** et vérifier qu'il est compatible avec l'évolution phonétique des formes relevées.
5. **Déterminer la strate linguistique** d'après l'étymon, et non d'après le suffixe seul (voir § 5).
6. **Évaluer la certitude** (voir § 6).
7. **Classer le type de nom** (voir § 7).
8. **Consigner en `Notes`** les autres formes, les hypothèses concurrentes et les étymologies populaires à écarter.

## 4. Règles de saisie, colonne par colonne

### Format du fichier
- Le fichier de référence est `communes_bourbonnais.csv` : **UTF-8 sans BOM, séparateur virgule, guillemets doubles** autour des champs contenant une virgule.
- Une ligne par commune. Le `Code INSEE` est la clé unique : il ne doit jamais être modifié ni dupliqué.
- **Une cellule sans information reste vide.** On n'écrit jamais `0`, `-`, `?` ou `N/A`.
- Les communes fusionnées (communes nouvelles) gardent une ligne par **commune déléguée**, avec son code INSEE historique. La fusion est signalée en `Notes`.

> ⚠️ **Attention à Excel** : ouvrir puis enregistrer le CSV dans Excel peut supprimer le zéro initial des codes INSEE (`03001` → `3001`) et changer l'encodage ou le séparateur. Préférez LibreOffice (en cochant « Colonne en texte » à l'import), un éditeur de texte ou l'éditeur intégré de GitHub.

### `Code INSEE`, `Commune`, `Dép.`, `Département`
- Référentiel : Code officiel géographique (COG) de l'INSEE en vigueur.
- `Commune` : nom officiel, avec traits d'union et majuscules réglementaires (`Saint-Pourçain-sur-Sioule`).
- `Dép.` : deux caractères (`03`, et non `3`).

### `Pays retenu` et `Sous-pays retenu`
- `Pays retenu` est obligatoire et prend une des quatre valeurs de la liste fermée du README.
- `Sous-pays retenu` est facultatif : laissez la cellule vide si la commune ne relève d'aucun sous-pays.
- Un changement de rattachement doit être justifié en `Notes` (limite de paroisse, de châtellenie, de diocèse, usage attesté…).

### `Forme ancienne`
- Transcription **exacte** de l'attestation, sans la normaliser : `Parrochia de Agongiis`, et non « Agonges ».
- On garde le contexte quand il est attesté avec le nom (`Ecclesia de…`, `Parrochia de…`, `Villa…`).
- Une forme reconstituée (non attestée) ne va **jamais** ici : elle va dans `Étymon et explication`, précédée d'un astérisque (`*Vindiciacum`).

### `Date / siècle`
- **Année en nombre entier** (`1155`).
- Si le document donne une fourchette, saisir l'année la plus ancienne et préciser la fourchette en `Notes` (« bulle d'Adrien IV, 1154-1159 »).
- Si seul le siècle est connu, saisir la première année du siècle (`1201` pour le XIIIe s.) et écrire « XIIIe s. » en `Notes`.
- Pour une datation approximative (monnaie, inscription), saisir l'année la plus vraisemblable et préciser « vers » en `Notes`.

### `Source`
- Format : `Auteur, Titre abrégé, tome, page` ; plusieurs sources séparées par ` ; `.
- Quand une attestation est connue par un intermédiaire, on cite **le document d'origine, puis l'ouvrage qui le rapporte**, séparés par un tiret cadratin :
  `Cartulaire de Sauxillanges — Dauzat & Rostaing`
- Une source lue chez un tiers est signalée par `via` : `Nègre, TGF (via Wikipédia oc)`.
- Utiliser les abréviations du § 9, ou les définir dans ce fichier si elles sont nouvelles.

### `Strate linguistique`
Liste fermée (voir § 5).

### `Étymon et explication`
- Indiquer **la langue, l'étymon et le sens** : `Nom de personne gaulois Bilius + -acos`.
- Les formes reconstituées portent un astérisque : `*Carpino-ialon`.
- Les sens sont entre guillemets français : `vindo- « blanc »`.
- Citer l'auteur de l'hypothèse entre parenthèses : `(Nègre, TGF, p. 211)`.
- Les abréviations de langue suivent le § 9 (`lat.`, `gaul.`, `germ.`, `occ.`…).

### `Certitude`
Liste fermée (voir § 6). **Obligatoire dès qu'un étymon est proposé.**

### `Type de nom`
Liste fermée (voir § 7). On choisit **une seule** catégorie, celle du **sens premier du nom**.

### `Notes`
Champ libre pour : autres formes anciennes datées, hypothèses concurrentes, étymologies populaires à écarter (avec la raison), fusions de communes, rattachement discuté.

## 5. Strates linguistiques

| Valeur | Critères |
|---|---|
| `Pré-celtique` | Racine non indo-européenne ou antérieure au gaulois, généralement oronymique ou hydronymique (*kar-*, *alb-*…). À employer avec prudence. |
| `Gauloise` | Étymon gaulois (*-ialo*, *-dunum*, *-briga*, *nemeton*…), y compris un nom de personne gaulois + suffixe *-acos/-acum*. |
| `Latine / romane` | Étymon latin ou formation romane (ancien français, occitan). Comprend les hagionymes et les noms de personnes latins + *-acum*. |
| `Germanique` | Étymon francique ou germanique, y compris un nom de personne germanique + suffixe roman. |
| `Indéterminée` | Formes trop tardives ou trop rares, ou étymologie inconnue. |

**Règle clé : la strate est celle de l'élément porteur de sens, pas celle du suffixe.** *Watenus + -acum* (Gannat) relève de la strate `Germanique`, même si *-acum* est d'origine gauloise ; *Bilius + -acos* (Billy) relève de la strate `Gauloise`.

## 6. Degré de certitude

| Valeur | Conditions |
|---|---|
| `Sûre` | Formes anciennes nombreuses et cohérentes ; étymologie admise sans désaccord par les ouvrages de rang 3 ; évolution phonétique régulière. |
| `Probable` | Une seule bonne attestation, ou étymologie majoritaire mais pas unanime ; aucune objection phonétique sérieuse. |
| `Discutée` | Plusieurs hypothèses concurrentes publiées, forme ancienne douteuse ou latinisation tardive possible, ou explication qui force la phonétique. Les hypothèses concurrentes **doivent** figurer en `Notes`. |

Si aucun étymon n'est proposé, laisser `Certitude` vide et saisir `Indéterminée` en strate.

## 7. Types de nom

| Valeur | Définition | Exemples de formants |
|---|---|---|
| `Anthroponyme` | Nom de personne (propriétaire du domaine) | NP + *-acum*, *-iacum*, *-anicas* |
| `Hagionyme` | Saint patron de la paroisse | *Saint-…*, *Dompierre* (*dominus Petrus*) |
| `Végétation` | Arbre, plante, couvert végétal | *-etum* collectif, *Charmeil*, *Abrest* |
| `Habitat` | Type d'établissement humain | *villa*, *curtis*, *mansus*, *casalis* |
| `Relief` | Forme du terrain | *mont*, *puy*, *roche*, *val* |
| `Eau (hydronyme, source, gué, marais)` | Cours d'eau, source, gué, zone humide | *-ialo* près d'un gué, *fontana*, *vadum* |
| `Lieu de culte / monastère` | Église, chapelle, établissement religieux | *ecclesia*, *monasterium*, *celle* |
| `Fortification / château` | Ouvrage défensif | *castrum*, *castellum*, *ferté*, *-dunum* |
| `Terroir / défrichement` | Mise en valeur agricole, essart | *essart*, *novalis*, *bouchet* |
| `Sacré / théonyme` | Divinité ou lieu sacré préchrétien | *nemeton*, *Vosegus*, *Belenos* |
| `Limite / frontière` | Limite de territoire | *fines*, *marche*, *-randa* |
| `Activité (moulin, forge, mine)` | Activité artisanale ou industrielle | *molinum*, *fabrica*, *ferrière* |
| `Voie / passage` | Route, chemin, passage | *strata*, *via*, *calceia* |
| `Faune` | Animal | *lupus*, *corvus* |

**Cas des noms composés** : on classe selon l'élément **principal**. « Saint-Gérand-le-Puy » est un `Hagionyme` ; le déterminant *le-Puy* est commenté en `Notes`.

Toute nouvelle catégorie doit d'abord être proposée dans une Issue pour éviter la dispersion.

## 8. Étymologies populaires et hypothèses à écarter

Ne jamais les supprimer : les déplacer en `Notes` avec une formule explicite :

> L'étymologie de X (« … ») n'est pas recevable : [raison phonétique, chronologique ou documentaire].

Cas typiques à écarter : explication par la graphie moderne, rapprochement avec un mot français actuel, suffixe *-ing* germanique invoqué pour des *-anges/-onges* bourbonnais, rattachements « celtomanes » du XIXe siècle sans base phonétique.

## 9. Abréviations

### Abréviations des sources

| Abréviation | Référence complète |
|---|---|
| **TGF** | Ernest Nègre, *Toponymie générale de la France*, Genève, Droz, 1990-1998, 3 vol. |
| **Chazaud** | Martial-Alphonse Chazaud, *Dictionnaire des noms de lieux habités du département de l'Allier*, Moulins, 1881 |
| **Dauzat & Rostaing** | Albert Dauzat, Charles Rostaing, *Dictionnaire étymologique des noms de lieux en France*, Paris, Larousse, 1963 |
| **Deroy & Mulon** | Louis Deroy, Marianne Mulon, *Dictionnaire de noms de lieux*, Paris, Le Robert, 1992 |
| **DicoTopo / Dico Topo** | *Dictionnaire topographique de la France*, CTHS, https://dicotopo.cths.fr (préciser le département) |
| **RIO** | *Revue internationale d'onomastique* |
| **Longnon, Pouillés** | Auguste Longnon, *Pouillés de la province de…* (Recueil des historiens de la France) |
| **Gall. christ.** | *Gallia christiana* |
| **Chaume** | Maurice Chaume, *Les Origines du duché de Bourgogne* |
| **A. N.** | Archives nationales |
| **C.O.** | Archives départementales de la Côte-d'Or (suivi de la cote, ex. `B 10477`) |
| **Itin.** | Itinéraire antique (Antonin ou Table de Peutinger) : à préciser |
| **S**, **C** | Sigles employés par le *Dictionnaire topographique* d'origine : à vérifier et à expliciter |

### Abréviations linguistiques

| Abréviation | Sens |
|---|---|
| lat. | latin |
| b. lat. | bas latin |
| gaul. | gaulois |
| germ. | germanique |
| frq. | francique |
| occ. | occitan |
| a. fr. | ancien français |
| NP | nom de personne |
| \* | forme reconstituée, non attestée |
| > | « a donné » |
| < | « vient de » |

## 10. Processus de contribution

1. **Une Pull Request = un sujet** (une commune, ou une même correction sur plusieurs communes).
2. Le titre indique le code INSEE et la commune : `03002 Agonges — nouvelle attestation 1155`.
3. La description donne **la source complète** et, si possible, une capture ou un lien vers la page consultée.
4. Les propositions sans source sont acceptées uniquement en `Notes`, marquées « hypothèse non publiée ».
5. Un désaccord se discute dans l'Issue ou la Pull Request ; la base reflète ensuite l'état de la discussion (§ 1, principe 5).

---

*Ce document peut lui-même évoluer : toute amélioration de méthode peut être proposée par une Issue.*
