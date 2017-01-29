---
title       : "Séance 1: Introduction"
subtitle    : "BIO 500 - Méthodes en écologie computationnelle"
author      : "Dominique Gravel"
job         : "Laboratoire d'écologie intégrative"
logo        : "logo.png"
framework   : io2012       # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      #
mode        : selfcontained
knit        : slidify::knit2slides
widgets     : [mathjax]
url:
  lib   : ./libraries
license     : by-nc-sa
assets      :
  css: "https://maxcdn.bootstrapcdn.com/font-awesome/4.6.0/css/font-awesome.min.css"
---
# Séance 2

- Ces diapositives sont disponibles en [version web](https://econumuds.github.io/BIO500/cours1/) et en [PDF](./assets/pdf/S1-BIO500.pdf).
- L'ensemble du matériel de cours est disponible sur la page du portail [moodle](https://www.usherbrooke.ca/moodle2-cours/course/view.php?id=12188).

<!-- TODO 1: Mettre cours 1 en PDF -->
<!-- TODO 2: Changer le lien moodle -->

--- .transition

# Les types de données

---

# La collecte de données

<div style='text-align:center;'>
<img src="assets/img/flow_cours2.png" width="90%"></img>
</div>

---

# La collecte de données

En statistique, il éxiste plusieurs grandes familles de données:

1. Quantitative (variables continues)
2. Semi-quantitative (variables discrètes)
3. Qualitatives (variables de rang)

Le type de données conditionne les analyses statistiques que l'on pourra réaliser sur les données.

---

# La collecte de données

En informatique, on classifie les données selon 4 grands types:

1. Numérique
2. Alphanumérique
3. Temporel
4. Spatial

Le choix d'un type aura une influence sur la taille du fichier et permettra de filtrer certaines erreurs lors de la saisie.

---

# La collecte de données

En biologie, la collecte de données se résume à un hypercube.


Comme nous le verrons plus tard cette multi-dimensionnalité complique notre tâche, car il est difficile de la représenter dans un tableau excel (n-2).
