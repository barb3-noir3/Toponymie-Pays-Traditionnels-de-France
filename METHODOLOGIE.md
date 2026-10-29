# Méthodologie

Ce document fixe les règles de recherche, de classement et de saisie, communes à **toutes les provinces** de la base. Il vise deux objectifs : qu'on puisse **vérifier chaque information**, et que deux contributeurs travaillant sur deux régions différentes saisissent la même donnée de la même façon.

Les exemples sont tirés des provinces déjà traitées. Les règles valent pour l'ensemble de la France métropolitaine (hors Corse).

---

## 1. Principes

1. **Pas de source, pas de donnée.** Toute forme ancienne et toute étymologie doivent pouvoir être retrouvées par un tiers.
2. **La forme ancienne prime sur la forme moderne.** On n'explique pas un nom d'après sa graphie actuelle, mais d'après ses attestations les plus anciennes (Agonges ne s'explique pas par « à Gonge »).
3. **La série prime sur le cas isolé.** Une explication est plus solide quand elle s'inscrit dans une série connue : noms en *-acum*, en *-ialo*, en *-ville*, en *-court*, en *-tot*, en *Plou-*…
4. **Distinguer le fait de l'hypothèse.** L'attestation est un fait daté ; l'étymon est une reconstruction. Le degré de confiance est indiqué dans `Certitude`.
5. **Garder la trace des débats.** Une hypothèse écartée ne s'efface pas : elle passe en `Notes`, avec la raison du rejet.
6. **Une même règle partout.** Une convention adoptée pour une province s'applique à toutes. Une exception régionale doit être justifiée et ajoutée à ce document.

## 2. Hiérarchie des sources

Par ordre de fiabilité décroissante :

| Rang | Type de source | Exemples |
|---|---|---|
| 1 | **Documents originaux** : chartes, cartulaires, pouillés, terriers, polyptyques, monnaies, inscriptions, itinéraires antiques | Polyptyque d'Irminon, cartulaires abbatiaux, monnaies mérovingiennes, Table de Peutinger |
| 2 | **Dictionnaires topographiques** qui relèvent ces documents | DicoTopo (CTHS), dictionnaires topographiques départementaux, Chazaud (Allier) |
| 3 | **Ouvrages de toponymie scientifique** | Nègre, Dauzat et Rostaing, Lacroix, Delamarre, ouvrages régionaux (§ 9), *Revue internationale d'onomastique* |
| 4 | **Monographies locales et érudition régionale** | Monographies communales, bulletins de sociétés savantes, dictionnaires des communes |
| 5 | **Sources de seconde main non vérifiées** | Wikipédia (toutes langues), blogs, sites de mairies |

**Règles générales**
- Une source de rang 5 ne suffit jamais seule. Elle sert de piste : il faut remonter à l'ouvrage qu'elle cite.
- Tant qu'on n'a pas consulté l'original, la mention « via … » ou « réf. à vérifier » est **obligatoire**. On ne cite jamais un ouvrage comme si on l'avait consulté quand on l'a lu chez un tiers.
- En cas de désaccord entre deux rangs, le rang supérieur l'emporte, sauf démonstration contraire publiée.
- En cas de désaccord au même rang, on retient l'avis le plus récent et le mieux argumenté. L'autre est consigné en `Notes`.

**Règles de priorité par domaine**
- **Formes anciennes** : on part de DicoTopo et des dictionnaires topographiques départementaux, que l'on complète par les documents qu'ils citent.
- **Étymons gaulois** : **Jacques Lacroix fait référence** et l'emporte sur Nègre, Dauzat, Rostaing et Delamarre. Les autres avis sont consignés en `Notes` lorsqu'ils divergent.
- **Domaines régionaux** (breton, basque, scandinave, flamand…) : les ouvrages spécialisés de la région (§ 9) priment sur les dictionnaires généraux.

## 3. Démarche pour traiter une commune

1. **Relever toutes les formes anciennes disponibles** et les classer par date.
2. **Retenir la plus ancienne forme fiable** pour `Forme ancienne` et `Date / siècle`. Les autres formes utiles passent en `Notes`.
3. **Identifier les formants** : radical, suffixe (*-acum*, *-etum*, *-ialo*, *-dunum*…), élément de composition (*-villa*, *-curtis*, *-tot*, *Plou-*, *Ker-*…), déterminant (*Saint-*, *-le-Châtel*, *-sur-Loire*…).
4. **Chercher l'étymon dans les ouvrages de rang 3** et vérifier qu'il est compatible avec l'évolution phonétique des formes relevées.
5. **Déterminer la strate linguistique** (§ 5).
6. **Évaluer la certitude** (§ 6).
7. **Classer le type de nom** (§ 7).
8. **Consigner en `Notes`** les autres formes, les hypothèses concurrentes et les étymologies populaires à écarter (§ 8).

## 4. Règles de saisie

### Format des fichiers
- Un fichier par province ou ensemble régional, dans `donnees/`, nommé en minuscules, sans accent ni espace : `bourbonnais.csv`, `pays-de-caux.csv`, `flandre-maritime.csv`.
- **UTF-8 sans BOM, séparateur virgule, guillemets doubles** autour des champs contenant une virgule.
- Les quatorze colonnes standard, **dans l'ordre du README**, sans en ajouter ni en retirer. Une colonne nouvelle se propose dans une Issue et s'ajoute alors à tous les fichiers.
- Une ligne par commune. Le `Code INSEE` est la clé unique **de toute la base** : une commune n'apparaît que dans un seul fichier.
- **Une cellule sans information reste vide.** On n'écrit jamais `0`, `-`, `?` ou `N/A`.

> ⚠️ **Attention à Excel** : ouvrir puis enregistrer un CSV dans Excel peut supprimer le zéro initial des codes INSEE (`03001` → `3001`) et changer l'encodage ou le séparateur. Préférez LibreOffice (en déclarant les colonnes en « Texte » à l'import), un éditeur de texte ou l'éditeur intégré de GitHub.

### `Code INSEE`, `Commune`, `Dép.`, `Département`
- Référentiel : **Code officiel géographique (COG) de l'INSEE** en vigueur.
- `Commune` : nom officiel, avec traits d'union et majuscules réglementaires (`Saint-Pourçain-sur-Sioule`).
- `Dép.` : deux caractères (`03`, et non `3`).
- **Communes nouvelles** : on garde une ligne par **commune déléguée**, avec son code INSEE historique, car chaque ancienne commune a son propre nom et sa propre histoire. La fusion est signalée en `Notes`.

### `Pays retenu` et `Sous-pays retenu`
- Les valeurs sont choisies dans **`referentiels/pays.csv`**, qui liste les pays et sous-pays autorisés pour chaque province.
- `Pays retenu` est obligatoire ; `Sous-pays retenu` reste vide si la commune ne relève d'aucun sous-pays.
- Une commune limitrophe est rattachée au pays auquel l'usage historique la lie (paroisse, châtellenie, diocèse, coutume, appellation attestée), **et non à son département actuel**. Un rattachement discuté est justifié en `Notes`.
- Un pays ou sous-pays nouveau se propose d'abord dans une Issue, puis s'ajoute au référentiel avant d'être utilisé dans les données.

### `Forme ancienne`
- Transcription **exacte** de l'attestation, sans la normaliser : `Parrochia de Agongiis`, et non « Agonges ».
- On garde le contexte attesté avec le nom (`Ecclesia de…`, `Parrochia de…`, `Villa…`, `in pago…`).
- Une forme reconstituée (non attestée) ne va **jamais** ici. Elle va dans `Étymon et explication`, précédée d'un astérisque (`*Vindiciacum`).

### `Date / siècle`
- **Année en nombre entier** (`1155`).
- Fourchette (`1154-1159`) : saisir l'année la plus ancienne, préciser la fourchette en `Notes`.
- Siècle seul : saisir la **première année du siècle** (`1201` pour le XIIIe s.), écrire « XIIIe s. » en `Notes`.
- Datation approximative (monnaie, inscription, copie tardive) : saisir l'année la plus vraisemblable, préciser « vers » ou « copie de … » en `Notes`.
- **Monnaies mérovingiennes** : on saisit la **borne haute** de la datation, pour ne jamais vieillir une attestation au-delà de ce que la monnaie garantit. La datation exacte est recopiée en `Notes`.
  - monnaie datée seulement de l'« époque mérovingienne » → `750` ;
  - monnaie datée d'un siècle (« triens mérovingien du VIIe siècle ») → dernière année du siècle : `700`.
  - Cette règle déroge volontairement à celle du siècle seul (première année du siècle), qui vaut pour les chartes et autres documents écrits.
- Forme connue par une **copie tardive** d'un acte ancien : on date l'acte, et non la copie, en le signalant en `Notes`.

### `Source`
- Format : `Auteur, Titre abrégé, tome, page`. Plusieurs sources sont séparées par ` ; `.
- Quand une attestation est connue par un intermédiaire, on cite **le document d'origine, puis l'ouvrage qui le rapporte**, séparés par un tiret cadratin : `Cartulaire de Sauxillanges — Dauzat & Rostaing`.
- Une source lue chez un tiers est signalée par `via` : `Nègre, TGF (via Wikipédia)`.
- Les abréviations sont celles du § 9. Une abréviation nouvelle doit y être ajoutée dans la même Pull Request.

### `Étymon et explication`
- Indiquer **la langue, l'étymon et le sens** : `Nom de personne gaulois Bilius + -acos`.
- Les formes reconstituées portent un astérisque (`*Carpino-ialon`), les sens sont entre guillemets français (`vindo- « blanc »`).
- Citer l'auteur de l'hypothèse entre parenthèses : `(Nègre, TGF, p. 211)`.

### `Strate linguistique`, `Certitude`, `Type de nom`
Listes fermées, définies aux § 5, 6 et 7.

### `Notes`
Champ libre pour : autres formes anciennes datées, hypothèses concurrentes, étymologies populaires écartées (avec la raison), fusion de communes, rattachement discuté, précisions de datation.

## 5. Strates linguistiques

### Ce que mesure la strate

La strate indique **la racine linguistique la plus ancienne du nom**, et **non l'époque où le nom a été formé**. C'est ce qui permet de cartographier les couches de peuplement et de langue.

Trois conséquences :
1. **Gallo-romain, roman, médiéval, moderne et contemporain forment une seule strate**, `Latine / romane`. Un nom formé au XIXe siècle sur un mot français a donc la même strate qu'un domaine gallo-romain en *-acum* sur un nom de personne latin. L'époque se lit dans `Date / siècle`, la nature du nom dans `Type de nom`.
2. **Un mot gaulois passé en latin puis en roman reste classé `Gauloise`**, même si le nom a été formé à l'époque romane. Par exemple, une *Chassagne* (gaul. *cassanos* « chêne ») ou une *Bessière* (gaul. *bettio-* « bouleau ») relèvent de la strate `Gauloise`.
3. **La strate est celle de l'élément qui porte le sens, et non celle du suffixe.** Pour les noms en *-acum*, la strate suit le nom de personne :
   - *Bilius + -acos* (Billy) → `Gauloise`
   - nom de personne latin + *-acum* → `Latine / romane`
   - *Watenus + -acum* (Gannat) → `Germanique`

   La même règle s'applique aux composés en *-villa* et *-curtis* : nom de personne germanique + *villa* → `Germanique` ; nom de personne norrois + *villa* → `Scandinave`.

### Valeurs

La liste compte **15 strates**, qui font norme pour toutes les provinces. Pour la cartographie, elles sont regroupées en **9 grandes familles** : les strates d'une même famille se recouvrent rarement sur le terrain (scandinave, saxonne et flamande, par exemple, occupent des littoraux distincts), et le regroupement rend les cartes lisibles à l'échelle de la France. La saisie se fait toujours au niveau de la strate.

| Famille | Strate | Critères | Exemples de formants |
|---|---|---|---|
| Pré-celtique | `Pré-celtique` | Racine pré-indo-européenne ou paléo-européenne non attribuable, généralement oronymique ou hydronymique. À employer avec prudence et toujours sourcée. | *kar-*, *kal-*, *alp-*, *alb-*, *tur-* |
| Pré-celtique | `Ligure` | Provence, Alpes : formations ligures antiques. Toujours sourcée. | *-asc*, *-osc* (Manosque, Venasque) |
| Pré-celtique | `Aquitaine (proto-basque)` | Gascogne, Pyrénées : racine aquitanienne antique (ancêtre du basque) | *-os*, *-ost*, *-ein* (Biscarrosse) |
| Pré-celtique | `Ibère` | Roussillon, Languedoc occidental. Toujours sourcée. | Elne < *Illiberis* |
| Grecque | `Grecque` | Colonies phocéennes (Marseille, Nice, Antibes, Agde) et racines grecques passées par le latin | *smaragdos* (Montmarault) |
| Gauloise | `Gauloise` | Étymon gaulois, y compris un nom de personne gaulois + suffixe, les ethnonymes de cités et les mots gaulois passés en roman (règle 2) | *-ialo*, *-dunum*, *-briga*, *-magos*, *nemeton*, *cassanos* (chambon, varenne, breuil, ouche, chaux, verne) |
| Latine / romane | `Latine / romane` | Étymon latin ou roman (ancien français, occitan, francoprovençal, catalan), de l'Antiquité à nos jours, y compris les hagionymes et les formations modernes | *-acum* / *-anum* + NP latin, *villa*, *Saint-*, *Villeneuve* |
| Germanique | `Germanique` | Germanique ancien des grandes migrations (Francs, Alamans, Burgondes, Wisigoths), y compris un nom de personne germanique + suffixe ou élément roman, et les mots germaniques passés en roman (*bosc*, *skur*) | *-ing(os)* > *-ange*, *-ans*, *-ens* ; *-heim* ; NP germ. + *-iacum* / *-court* / *-ville* |
| Germanique | `Saxonne` | Littoral boulonnais, Bessin | *-thun*, *-tun* |
| Germanique | `Scandinave` | Étymon norrois ou anglo-scandinave (Normandie surtout) | *-tot*, *-bec*, *-fleur*, *-dal*, *-hogue*, NP norrois + *-ville* |
| Germanique | `Flamande` | Néerlandais médiéval (Flandre maritime) | *-kerque*, *-ghem*, *-hem*, *-becque*, *-brouck* (Dunkerque) |
| Arabe | `Arabe` | Présence arabo-berbère des VIIIe–Xe s. (Septimanie, Narbonne 719–759 ; Fraxinet, La Garde-Freinet 889–973). Racines arabes directes très rares et souvent discutées. | — |
| Bretonne | `Bretonne` | Étymon breton ou brittonique (vieux et moyen breton), à distinguer du gaulois | *Plou-*, *Lan-*, *Tré-*, *Ker-*, *Loc-*, *Pont-* |
| Basque | `Basque` | Formation en basque (Pays basque) | *Etxe-*, *Iri-*, *-berri*, *-ena* |
| Indéterminée | `Indéterminée` | Formes trop tardives ou trop rares, étymologie inconnue ou trop discutée pour être classée | — |

**Cas limites**
- **Scandinave ou germanique ?** En Normandie, un nom de personne norrois relève de la strate `Scandinave`, un nom de personne francique de la strate `Germanique`. En cas de doute, on choisit `Germanique` et on signale l'hypothèse norroise en `Notes`.
- **Flamande ou germanique ?** Une formation néerlandaise médiévale (*-kerque*, *-ghem*, *-becque*) relève de la strate `Flamande` ; un nom de personne francique + *-iacum*, *-court* ou *-ville* reste `Germanique`.
- **Saxonne ou germanique ?** `Saxonne` est réservée aux formations en *-thun* / *-tun* du littoral boulonnais et du Bessin.
- **Aquitaine ou basque ?** `Aquitaine (proto-basque)` désigne une racine antique ; `Basque` une formation en langue basque médiévale ou moderne.
- **Arabe ?** Les noms en *Maure-*, *Sarrasin-* sont des mots romans : `Latine / romane`.
- **Brittonique ou gaulois ?** Hors de Bretagne, une racine celtique est classée `Gauloise`. En Bretagne, on distingue les formations bretonnes (*Plou-*, *Lan-*…) des noms gaulois antérieurs (*-acum*, *-dunum*…).
- **Hybride** : quand deux strates se combinent sans qu'aucun élément ne domine, on retient la plus ancienne et on explique en `Notes`.

## 6. Degré de certitude

| Valeur | Conditions |
|---|---|
| `Sûre` | Formes anciennes nombreuses et cohérentes ; étymologie admise sans désaccord par les ouvrages de rang 3 ; évolution phonétique régulière. |
| `Probable` | Une seule bonne attestation, ou étymologie majoritaire mais pas unanime ; aucune objection phonétique sérieuse. |
| `Discutée` | Plusieurs hypothèses concurrentes publiées, forme ancienne douteuse ou latinisation tardive possible, ou explication qui force la phonétique. Les hypothèses concurrentes **doivent** figurer en `Notes`. |

`Certitude` est **obligatoire dès qu'un étymon est proposé**. Si aucun étymon n'est proposé, laisser `Certitude` vide et saisir `Indéterminée` en strate.

## 7. Types de nom

On choisit **une seule** catégorie : celle du **sens premier** de l'élément principal du nom.

| Valeur | Définition | Exemples de formants |
|---|---|---|
| `Anthroponyme` | Nom de personne (propriétaire, fondateur) | NP + *-acum*, *-iacum*, *-ville*, *-court*, *-ingas* |
| `Hagionyme` | Saint patron de la paroisse | *Saint-…*, *Dompierre* (*dominus Petrus*), *Loc-* + saint |
| `Végétation` | Arbre, plante, couvert végétal | *-etum*, *Chassagne*, *Charmeil*, *Boulay* |
| `Habitat` | Type d'établissement humain | *villa*, *curtis*, *mansus*, *Ker-*, *-heim* |
| `Relief` | Forme du terrain | *mont*, *puy*, *roche*, *val*, *-dalle* |
| `Eau (hydronyme, source, gué, marais)` | Cours d'eau, source, gué, zone humide | *fontana*, *vadum*, *-bec*, *-brouck* |
| `Lieu de culte / monastère` | Église, chapelle, établissement religieux | *ecclesia*, *monasterium*, *celle*, *Lan-* |
| `Fortification / château` | Ouvrage défensif | *castrum*, *castellum*, *ferté*, *-dunum* |
| `Terroir / défrichement` | Mise en valeur agricole, essart | *essart*, *novalis*, *-rode* |
| `Sacré / théonyme` | Divinité ou lieu sacré préchrétien | *nemeton*, *Vosegus*, *Belenos* |
| `Limite / frontière` | Limite de territoire | *fines*, *marche*, *-randa* |
| `Activité (moulin, forge, mine)` | Activité artisanale ou industrielle | *molinum*, *fabrica*, *ferrière* |
| `Voie / passage` | Route, chemin, passage | *strata*, *via*, *calceia* |
| `Faune` | Animal | *lupus*, *corvus* |

**Noms composés** : on classe selon l'élément principal. « Saint-Gérand-le-Puy » est un `Hagionyme` ; le déterminant *le-Puy* est commenté en `Notes`.

**Nom inexpliqué** : laisser `Type de nom` vide.

Toute nouvelle catégorie doit d'abord être proposée dans une Issue pour éviter la dispersion.

## 8. Étymologies populaires et hypothèses à écarter

On ne les supprime jamais : on les déplace en `Notes`, avec une formule explicite :

> L'étymologie de X (« … ») n'est pas recevable : [raison phonétique, chronologique ou documentaire].

Cas typiques à écarter :
- explication par la graphie moderne ou par un mot français actuel (calembour toponymique) ;
- légende de fondation ou anecdote historique sans appui dans les formes anciennes ;
- rattachements « celtomanes » du XIXe siècle sans base phonétique ;
- strate attribuée à un suffixe hors de son aire (*-ing* germanique invoqué pour les *-anges/-onges* du Centre, par exemple).

## 9. Sources de référence et abréviations

### Ouvrages généraux

| Abréviation | Référence complète |
|---|---|
| **DicoTopo** | *Dictionnaire topographique de la France*, CTHS, https://dicotopo.cths.fr (préciser le département) |
| **TGF** | Ernest Nègre, *Toponymie générale de la France*, Genève, Droz, 1990-1998, 3 vol. |
| **Dauzat & Rostaing** | Albert Dauzat, Charles Rostaing, *Dictionnaire étymologique des noms de lieux en France*, Paris, Larousse, 1963 |
| **Deroy & Mulon** | Louis Deroy, Marianne Mulon, *Dictionnaire de noms de lieux*, Paris, Le Robert, 1992 |
| **Lacroix** | Jacques Lacroix, *Les Noms d'origine gauloise*, Paris, Errance, 3 vol. : *La Gaule des combats* (2003), *La Gaule des activités économiques* (2005), *La Gaule des dieux* (2007) |
| **Delamarre** | Xavier Delamarre, *Dictionnaire de la langue gauloise*, Paris, Errance, 2001 (2e éd. 2003) |
| **Vincent** | Auguste Vincent, *Toponymie de la France*, Bruxelles, 1937 |
| **Gendron** | Stéphane Gendron, *L'Origine des noms de lieux en France : essai de toponymie*, Paris, Errance, 2003 |
| **RIO** | *Revue internationale d'onomastique* |
| **Longnon, Pouillés** | Auguste Longnon, *Pouillés de la province de…* (Recueil des historiens de la France) |
| **Gall. christ.** | *Gallia christiana* |
| **A. N.** | Archives nationales |
| **A. D.** + n° | Archives départementales (ex. `A. D. 03` pour l'Allier), suivi de la cote |
| **EDH** | *Epigraphic Database Heidelberg*, Académie des sciences de Heidelberg, https://edh.ub.uni-heidelberg.de : inscriptions latines (rang 1, § 2), citées par leur numéro (ex. `EDH HD000515`). Données sous licence CC BY-SA 4.0 |

### Référentiel des noms de personnes attestés

Pour les noms formés sur un nom de personne (*-acum*, *-anum*, *villa*, *curtis*…), le dépôt fournit `referentiels/anthroponymes_edh.csv` : les gentilices et surnoms des inscriptions latines des Gaules, des Germanies et des Alpes, tirés de l'**EDH**, avec leurs occurrences, leurs lieux de découverte et le pays traditionnel de chaque inscription.

- Un nom **attesté** dans ce référentiel peut être cité comme tel (`EDH`, avec le numéro de l'inscription) ; un nom seulement **reconstitué** à partir du toponyme garde son astérisque (*\*Albinius*).
- Le référentiel ne dit rien de la **langue** du nom : un gentilice latinisé peut porter un radical gaulois. La strate se décide avec les ouvrages du § 2 (Lacroix pour la strate gauloise).
- Les colonnes « Forme en -(i)acum théorique » et « Indice celtique » sont des dérivations mécaniques, à titre indicatif.
- La couverture de l'EDH est inégale (bonne en Narbonnaise et dans les Germanies, faible en Lyonnaise, en Aquitaine et en Belgique) : l'absence d'un nom ne prouve pas qu'il n'existait pas.
- Ce fichier est sous **CC BY-SA 4.0**, comme les données de l'EDH dont il dérive (voir `referentiels/LICENCE-EDH.md`).

### Ouvrages régionaux

Chaque province ajoute ici ses ouvrages de référence et ses abréviations propres.

| Région | Abréviation | Référence complète |
|---|---|---|
| Bourbonnais | **Chazaud** | Martial-Alphonse Chazaud, *Dictionnaire des noms de lieux habités du département de l'Allier*, Moulins, 1881 |
| Bourgogne | **Chaume** | Maurice Chaume, *Les Origines du duché de Bourgogne* |
| Bourgogne | **C.O.** | Archives départementales de la Côte-d'Or, suivi de la cote (ex. `B 10477`) |
| Normandie | **Lepelley** | René Lepelley, *Dictionnaire étymologique des noms de communes de Normandie*, Caen, Charles Corlet / Presses universitaires de Caen, 1993 |
| Normandie | **Beaurepaire** | François de Beaurepaire, *Les Noms des communes et anciennes paroisses* de la Seine-Maritime (1979), de l'Eure (1981) et de la Manche (1986), Paris, Picard |
| Normandie | **Renaud** | Jean Renaud, *Vikings et noms de lieux de Normandie*, Cully, OREP, 2009 |
| Bretagne | **Deshayes** | Albert Deshayes, *Dictionnaire des noms de lieux bretons*, Douarnenez, Le Chasse-Marée / ArMen, 1999 |
| Flandre | **Gysseling** | Maurits Gysseling, *Toponymisch woordenboek van België, Nederland, Luxemburg, Noord-Frankrijk en West-Duitsland (vóór 1226)*, Tongres, 1960 |

À préciser : **Itin.** (itinéraire antique : Antonin ou Table de Peutinger) et les sigles **S** et **C** relevés dans le DicoTopo de la Nièvre.

### Abréviations linguistiques

| Abréviation | Sens |
|---|---|
| lat. | latin |
| b. lat. | bas latin |
| gaul. | gaulois |
| germ. | germanique |
| frq. | francique |
| norr. | norrois |
| bret. | breton |
| fl. | flamand |
| occ. | occitan |
| a. fr. | ancien français |
| NP | nom de personne |
| \* | forme reconstituée, non attestée |
| > | « a donné » |
| < | « vient de » |

## 10. Processus de contribution

1. **Une Pull Request = un sujet** : une commune, ou une même correction appliquée à plusieurs communes.
2. Le titre indique le code INSEE et la commune : `03002 Agonges — nouvelle attestation 1155`.
3. La description donne **la source complète** et, si possible, un lien ou une capture de la page consultée.
4. Les propositions sans source ne sont acceptées qu'en `Notes`, marquées « hypothèse non publiée ».
5. **Nouvelle province** : ouvrir d'abord une Issue avec la liste de ses pays et sous-pays ; une fois validée, l'ajouter à `referentiels/pays.csv`, puis créer le fichier `donnees/<province>.csv`.
6. Un désaccord se discute dans l'Issue ou la Pull Request ; la base reflète ensuite l'état de la discussion (§ 1, principe 5).

---

*Ce document peut lui-même évoluer : toute amélioration de méthode peut être proposée dans une Issue.*
