# Introductory workflow miaverse — illustré sur le microbiome marin

[![Render and publish](https://github.com/AxelDgn/miaverse-introductory-workflow-marine-biology/actions/workflows/render.yml/badge.svg)](https://github.com/AxelDgn/miaverse-introductory-workflow-marine-biology/actions/workflows/render.yml)

> Tutoriel reproductible en R/Quarto pour découvrir l'écosystème
> [**miaverse**](https://microbiome.github.io/) (Bioconductor) à travers un
> cas d'étude **marin** : océan, eau douce, sédiments estuariens.

📄 **[Voir le rendu en ligne](https://AxelDgn.github.io/miaverse-introductory-workflow-marine-biology/)**

## Objectif

Le workflow d'introduction officiel de miaverse repose sur un dataset
d'intestin humain **[ici](https://github.com/microbiome/OMA/commit/95903b05b47d7715a29ba03967a19bbfdc604dde#diff-28579d357ece0aeb5c1aa00cb974d8def61699d6ca1a774c45fe66907ba59985)**. Celui-ci reprend la même trame pédagogique mais sur des
échantillons aquatiques, pour montrer que les outils s'appliquent
indifféremment à n'importe quel contexte d'écologie microbienne. L'objet
pédagogique reste miaverse — le cas marin n'est qu'un support
d'illustration.

## Concepts miaverse couverts

| Section | Concepts et fonctions |
|---|---|
| Importation | `data()`, indexation Bioconductor `[, ]`, structure `TreeSummarizedExperiment` |
| Stockage | Accesseurs `assay()`, `colData()`, `rowData()` |
| Manipulation | Sous-ensembles par échantillon, `agglomerateByRank()` |
| Diversité alpha | `estimateRichness()`, `estimateDiversity()`, `plotColData()` |
| Diversité bêta | `transformAssay()`, `runMDS()`, `plotReducedDim()`, PCoA Bray-Curtis |
| Visualisation | `altExp`, `subsetByPrevalent()`, heatmap avec `sechm` |

## Reproduire l'analyse

### Prérequis

- R ≥ 4.3
- Quarto ≥ 1.3
- RStudio recommandé

### En local

```bash
git clone https://github.com/AxelDgn/miaverse-introductory-workflow-marine-biology.git
cd miaverse-introductory-workflow-marine-biology
quarto render marine-microbiome-workflow.qmd
```

Les packages requis s'installent automatiquement au premier rendu.

> En cas d'erreur de version sur `rlang` ou `cli` au premier `render` :
> redémarrer R puis exécuter en console
> `install.packages(c("rlang", "cli", "vctrs", "lifecycle"))`.

### En intégration continue

À chaque push sur `main`, le workflow [`render.yml`](.github/workflows/render.yml)
fait tourner Quarto sur une VM Ubuntu vierge et publie automatiquement le
HTML sur GitHub Pages. Le badge en haut du README reflète le statut du
dernier build.

## Jeu de données

`GlobalPatterns` [@Caporaso2011], inclus dans `mia`, restreint aux trois
environnements aquatiques : `Ocean`, `Freshwater`, `Sediment (estuary)`.
Neuf échantillons au total.

Pour passer à de vraies données marines à plus grande échelle, la section
*Pour aller plus loin* du workflow pointe vers
[Tara Oceans](https://fondationtaraocean.org/).

## Arborescence

```
.
├── .github/workflows/render.yml    # CI : rendu Quarto + publication Pages
├── .gitignore
├── README.md
├── marine-microbiome-workflow.qmd  # Le tutoriel
└── references.bib                  # Bibliographie
```

## Références

- Lahti *et al.* — [Orchestrating Microbiome Analysis with Bioconductor (OMA)](https://microbiome.github.io/OMA/)
- Caporaso *et al.* (2011), *PNAS* — jeu de données GlobalPatterns
- Sunagawa *et al.* (2015), *Science* — Tara Oceans

## Auteur

**Axel Dagnaud** — Master 1 Bio-informatique et Bio-statistiques (BIBS), Université Paris-Saclay.

