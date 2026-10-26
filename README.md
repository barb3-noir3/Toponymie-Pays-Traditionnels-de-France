# Toponymie des communes du Bourbonnais

Base de données ouverte recensant, pour **361 communes** de l'ancien Bourbonnais, le pays traditionnel de rattachement, la plus ancienne forme attestée du nom, sa source, sa strate linguistique et une proposition d'étymologie.

L'objectif est de mettre ce travail à la disposition des passionnés de toponymie, d'onomastique et d'histoire locale pour qu'ils le vérifient, le corrigent et le complètent. **Toute contribution sourcée est la bienvenue.**

---

## Contenu du dépôt

| Fichier | Description |
|---|---|
| `communes_bourbonnais.csv` | Fichier de référence (UTF-8, séparateur virgule). **C'est ce fichier qu'il faut modifier.** |
| `communes_bourbonnais.xlsx` | Copie au format Excel, pour consultation. Elle peut être en retard sur le CSV. |
| `METHODOLOGIE.md` | Règles de saisie, hiérarchie des sources et conventions à respecter |
| `LICENSE` | Texte de la licence Creative Commons Attribution 4.0 International |

## Périmètre

Le Bourbonnais historique ne coïncide pas avec le département de l'Allier. La base couvre donc aussi des communes de départements voisins :

| Département | Communes |
|---|---|
| Allier (03) | 287 |
| Nièvre (58) | 29 |
| Puy-de-Dôme (63) | 26 |
| Saône-et-Loire (71) | 16 |
| Creuse (23) | 2 |
| Loire (42) | 1 |

Les communes sont réparties en quatre **pays** : Bocage bourbonnais, Sologne bourbonnaise, Limagne bourbonnaise et Montagne bourbonnaise. Elles sont parfois précisées par un **sous-pays** : Basses Marches du Bourbonnais, Pays de Commentry, Pays de Tronçais, Pays de Fours, Vichyssois, Forterre bourbonnaise, Moulinois ou Monts de la Madeleine.

## Description des colonnes

| Colonne | Contenu | Exemple |
|---|---|---|
| `Code INSEE` | Code officiel de la commune, sur 5 caractères. **Toujours traité comme du texte.** C'est la clé unique de chaque ligne. | `03001` |
| `Commune` | Nom officiel actuel | `Abrest` |
| `Dép.` | Numéro du département (texte, 2 caractères) | `03` |
| `Département` | Nom du département | `Allier` |
| `Pays retenu` | Pays traditionnel de rattachement | `Montagne Bourbonnaise` |
| `Sous-pays retenu` | Subdivision du pays, si elle existe | `Forterre bourbonnaise` |
| `Forme ancienne` | Plus ancienne forme attestée, transcrite telle quelle (graphie et casse latines respectées) | `Parrochia de Abret` |
| `Date / siècle` | Année de l'attestation (nombre entier) | `1301` |
| `Source` | Référence(s) de l'attestation et de l'étymologie | `Nègre, TGF ; Chazaud (1881)` |
| `Strate linguistique` | Couche de langue à l'origine du nom (liste fermée, voir ci-dessous) | `Latine / romane` |
| `Étymon et explication` | Étymon reconstitué et raisonnement | `lat. arboretum « lieu planté d'arbres »` |
| `Certitude` | Degré de confiance dans l'étymologie (liste fermée) | `Probable` |
| `Type de nom` | Catégorie sémantique du nom (liste fermée) | `Végétation` |
| `Notes` | Autres formes anciennes, débats, hypothèses écartées | `Autres formes : Anonges (XIIIe s.)` |

### Valeurs autorisées

**Strate linguistique**
`Pré-celtique` · `Gauloise` · `Latine / romane` · `Germanique` · `Indéterminée`

**Certitude**
- `Sûre` : étymologie admise par les ouvrages de référence et appuyée sur des formes anciennes cohérentes
- `Probable` : explication la plus vraisemblable, mais qui ne fait pas l'unanimité ou repose sur peu d'attestations
- `Discutée` : plusieurs hypothèses concurrentes, ou explication fragile

**Type de nom**
`Anthroponyme` · `Hagionyme` · `Végétation` · `Habitat` · `Relief` · `Eau (hydronyme, source, gué, marais)` · `Lieu de culte / monastère` · `Fortification / château` · `Terroir / défrichement` · `Sacré / théonyme` · `Limite / frontière` · `Activité (moulin, forge, mine)` · `Voie / passage` · `Faune`

Les définitions détaillées et les règles de choix se trouvent dans [`METHODOLOGIE.md`](METHODOLOGIE.md).

## État d'avancement

La base est un **travail en cours**. Pistes prioritaires :

- **Renseigner la colonne `Source`, encore vide pour la majorité des communes** : c'est la priorité absolue
- Renseigner la colonne `Certitude` encore vide pour une partie des communes
- Compléter le `Type de nom` lorsque l'étymologie est indéterminée
- Remplacer les références de seconde main (« via Wikipédia », « réf. à vérifier ») par les ouvrages ou les chartes d'origine
- Rechercher des attestations plus anciennes que celles déjà relevées

## Principales sources

- **Nègre, Ernest**, *Toponymie générale de la France* (TGF), Genève, Droz, 1990-1998, 3 vol.
- **Chazaud, Martial-Alphonse**, *Dictionnaire des noms de lieux habités du département de l'Allier*, Moulins, 1881
- **Dauzat, Albert et Rostaing, Charles**, *Dictionnaire étymologique des noms de lieux en France*, Paris, Larousse, 1963 (rééd. Guénégaud)
- **DicoTopo**, *Dictionnaire topographique de la France* (CTHS), en ligne : https://dicotopo.cths.fr
- Dictionnaires topographiques départementaux (Nièvre, Puy-de-Dôme…)

Les abréviations utilisées dans la colonne `Source` sont détaillées dans [`METHODOLOGIE.md`](METHODOLOGIE.md#abréviations-des-sources).

## Contribuer

1. Lisez [`METHODOLOGIE.md`](METHODOLOGIE.md).
2. Pour signaler une erreur ou proposer une hypothèse sans modifier le fichier, ouvrez une **Issue** en précisant le code INSEE, la commune et votre source.
3. Pour corriger directement, modifiez `communes_bourbonnais.csv` et proposez une **Pull Request**. Une modification = une commune ou un thème, avec la source dans la description.

**Aucune modification sans source.** Une étymologie non référencée sera placée en `Notes` comme hypothèse, et non dans `Étymon et explication`.

## Licence et citation

Les données sont publiées sous licence **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.fr)**.

Vous pouvez copier, redistribuer, modifier et réutiliser ces données, y compris à des fins commerciales, à condition de :
- **citer la source** (auteur et lien vers ce dépôt) ;
- **indiquer la licence** ;
- **signaler si des modifications ont été apportées**.

Citation suggérée :

> [PSEUDONYME], *Toponymie des communes du Bourbonnais*, 2026, https://github.com/[PSEUDONYME]/[NOM-DU-DEPOT], licence CC BY 4.0.

Les formes anciennes et les étymologies relèvent de travaux publiés (Nègre, Chazaud, Dauzat…) que cette base cite et résume. Pour un usage scientifique, reportez-vous toujours aux ouvrages originaux.
