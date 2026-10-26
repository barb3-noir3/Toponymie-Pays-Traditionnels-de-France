# Toponymie des communes de France et pays traditionnels

Base de données ouverte qui associe chaque commune de France métropolitaine à son **pays traditionnel**, et qui recense pour chacune :

- la plus ancienne **forme attestée** de son nom, avec sa date et sa source ;
- la **strate linguistique** de son nom (pré-celtique, gauloise, latine, germanique…) ;
- une proposition d'**étymologie**, avec son degré de certitude ;
- le **type de nom** (nom de personne, saint, relief, cours d'eau, végétation…).

L'objectif est double : permettre la **cartographie des pays traditionnels** à partir des territoires communaux, et mettre à la disposition des passionnés de toponymie, d'onomastique et d'histoire locale une base qu'ils peuvent vérifier, corriger et compléter. **Toute contribution sourcée est la bienvenue.**

---

## Organisation du dépôt

```
├── README.md              Présentation du projet (ce fichier)
├── METHODOLOGIE.md        Règles de recherche, de classement et de saisie
├── LICENSE                Licence Creative Commons Attribution 4.0
├── donnees/
│   ├── bourbonnais.csv    Un fichier par province ou ensemble régional
│   ├── bourbonnais.xlsx   Copie Excel pour consultation (peut être en retard sur le CSV)
│   └── …
└── referentiels/
    └── pays.csv           Liste des pays et sous-pays autorisés, par province
```

- **Les fichiers `.csv` font foi** : ce sont eux qu'il faut modifier.
- Chaque fichier de `donnees/` couvre **une province ou un ensemble régional**. Il contient toutes les communes qui s'y rattachent, quel que soit leur département actuel : le Bourbonnais, par exemple, déborde sur la Nièvre, le Puy-de-Dôme et la Saône-et-Loire.
- Tous les fichiers ont **exactement les mêmes colonnes**, dans le même ordre, ce qui permet de les concaténer en une base nationale unique.

## Avancement

| Province / ensemble | Fichier | Communes | État |
|---|---|---|---|
| Bourbonnais | `donnees/bourbonnais.csv` | 361 | Formes anciennes et strates saisies ; sources et certitudes à compléter |
| *Autres provinces* | — | — | À venir |

**Périmètre** : France métropolitaine, **hors Corse**, dont la toponymie relève d'autres strates et méthodes que celles décrites ici. L'outre-mer n'est pas couvert.

## Description des colonnes

| Colonne | Contenu | Exemple |
|---|---|---|
| `Code INSEE` | Code officiel de la commune, sur 5 caractères, **toujours traité comme du texte**. C'est la clé unique de chaque ligne, dans toute la base. | `03001` |
| `Commune` | Nom officiel actuel | `Abrest` |
| `Dép.` | Numéro du département (texte, 2 caractères : `03`, `58`…) | `03` |
| `Département` | Nom du département | `Allier` |
| `Pays retenu` | Pays traditionnel de rattachement, choisi dans `referentiels/pays.csv` | `Montagne Bourbonnaise` |
| `Sous-pays retenu` | Subdivision du pays, si elle existe (sinon : vide) | `Forterre bourbonnaise` |
| `Forme ancienne` | Plus ancienne forme attestée, transcrite telle quelle | `Parrochia de Abret` |
| `Date / siècle` | Année de l'attestation (nombre entier) | `1301` |
| `Source` | Référence(s) de l'attestation et de l'étymologie | `Nègre, TGF ; Chazaud (1881)` |
| `Strate linguistique` | Racine linguistique la plus ancienne du nom (liste fermée) | `Latine / romane` |
| `Étymon et explication` | Étymon reconstitué et raisonnement | `lat. arboretum « lieu planté d'arbres »` |
| `Certitude` | Degré de confiance dans l'étymologie (liste fermée) | `Probable` |
| `Type de nom` | Catégorie sémantique du nom (liste fermée) | `Végétation` |
| `Notes` | Autres formes anciennes, débats, hypothèses écartées | `Autres formes : Anonges (XIIIe s.)` |

### Valeurs autorisées

**Strate linguistique**
`Pré-celtique` · `Gauloise` · `Latine / romane` · `Germanique` · `Scandinave` · `Bretonne` · `Basque` · `Indéterminée`

**Certitude**
`Sûre` · `Probable` · `Discutée`

**Type de nom**
`Anthroponyme` · `Hagionyme` · `Végétation` · `Habitat` · `Relief` · `Eau (hydronyme, source, gué, marais)` · `Lieu de culte / monastère` · `Fortification / château` · `Terroir / défrichement` · `Sacré / théonyme` · `Limite / frontière` · `Activité (moulin, forge, mine)` · `Voie / passage` · `Faune`

Les définitions, les critères de choix et les cas limites sont détaillés dans [`METHODOLOGIE.md`](METHODOLOGIE.md).

## Utiliser les données

- **Cartographie** : le `Code INSEE` permet de joindre la base aux contours communaux (Admin Express de l'IGN, découpage OpenStreetMap…), puis de regrouper les communes par pays ou de les colorer par strate, par date d'attestation ou par type de nom.
- **Base nationale** : concaténez tous les fichiers de `donnees/` (mêmes colonnes) ; le nom du fichier indique la province.
- **Tableur** : à l'import, déclarez les colonnes `Code INSEE` et `Dép.` en **texte**, sinon le zéro initial disparaît (`03001` → `3001`).

## Principales sources

**Sources communes à toute la base**
- *Dictionnaire topographique de la France* (DicoTopo), CTHS : https://dicotopo.cths.fr
- **Nègre, Ernest**, *Toponymie générale de la France* (TGF), Genève, Droz, 1990-1998, 3 vol.
- **Dauzat, Albert et Rostaing, Charles**, *Dictionnaire étymologique des noms de lieux en France*, Paris, Larousse, 1963
- **Lacroix, Jacques**, *Les Noms d'origine gauloise*, Paris, Errance, 3 vol. (2003-2007), qui fait référence pour la strate gauloise
- **Delamarre, Xavier**, *Dictionnaire de la langue gauloise*, Paris, Errance, 2001 (2e éd. 2003)

**Sources régionales** : voir la liste par région dans [`METHODOLOGIE.md`](METHODOLOGIE.md#9-sources-de-référence-et-abréviations).

## Contribuer

1. Lisez [`METHODOLOGIE.md`](METHODOLOGIE.md).
2. **Signaler une erreur ou proposer une hypothèse** sans modifier les fichiers : ouvrez une *Issue* en indiquant le code INSEE, la commune et votre source.
3. **Corriger ou compléter** : modifiez le fichier CSV de la province concernée et proposez une *Pull Request*. Une Pull Request = une commune ou un thème, avec la source dans la description.
4. **Ouvrir une nouvelle province** : proposez d'abord, dans une *Issue*, la liste de ses pays et sous-pays pour `referentiels/pays.csv`, puis créez le fichier `donnees/<province>.csv` avec les colonnes standard.

**Aucune modification sans source.** Une étymologie non référencée est placée en `Notes` comme hypothèse, et jamais dans `Étymon et explication`.

## Licence et citation

Les données et la documentation sont publiées sous licence **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.fr)**.

Vous pouvez copier, redistribuer, modifier et réutiliser ces données, y compris à des fins commerciales, à condition de :
- **citer la source** (auteur et lien vers ce dépôt) ;
- **indiquer la licence** ;
- **signaler si des modifications ont été apportées**.

Citation suggérée :

> [Barbe_Noir3], *Toponymie des communes de France et pays traditionnels*, 2026, https://github.com/[barb3_noir3]/[Toponymie-Pays-Traditionnels-de-France], licence CC BY 4.0.

Les formes anciennes et les étymologies proviennent de travaux publiés, que cette base cite et résume. Pour un usage scientifique, reportez-vous toujours aux ouvrages originaux.
