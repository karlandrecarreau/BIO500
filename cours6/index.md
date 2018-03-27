---
title       : "Séance 6: La visualisation des données"
subtitle    : "BIO 500 - Méthodes en écologie computationnelle"
author      : "Dominique Gravel & Steve Vissault"
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

# Séance 6

- Ces diapositives sont disponibles en [version web](https://econumuds.github.io/BIO500/cours5/) et en [PDF](./assets/pdf/S6-BIO500.pdf).
- L'ensemble du matériel de cours est disponible sur la page du portail [moodle](https://www.usherbrooke.ca/moodle2-cours/course/view.php?id=12189).
- Vous trouverez du matériel supplémentaire dans le [cours](http://kevincazelles.fr/talks/assets/QCBSGraphsR/Rgraphics.html#4) de [Kevin Cazelles](http://kevincazelles.fr/) et [Nicolas Casajus](http://www.cen.ulaval.ca/membre.aspx?id=3945098&membre=ncasajus) lors d'un atelier de communication visuelle du CSBQ.
- Certaines diapositives sont également extraites de la présentation de [David Taylor](http://dtdata.io/prm/intro_dataviz_csbq.pdf)

--- .transition

# Faire une figure étape par étape avec R

---

# Préparer les données adéquatement

- Habituellement un `data.frame` ou `une matrice`
- Une observation par ligne (format long)

--- &twocol

# Ouvrir une fenêtre graphique

*** =left

```r
dev.new(width = 10, height = 7)
```

*** =right


--- &twocol

# Fixer certains paramètres


```r
# Fixer la largeur et la hauteur des marges
par(mar = c(5,6,2,1))

# Fixer le nombre de figures en colonnes et rangées
par(mfrow = c(1,1))
```

*** =right


--- &twocol

# Démarrer une figure avec `plot()`

*** =left

```r
arbres <- read.csv2("donnees/arbres.csv")
densite <- table(arbres[,c(3,5)])
elevation <- as.numeric(row.names(densite))
plot(elevation, densite[,1], axes = FALSE,
      xlab = "Élévation", ylab = "Densité")
```

*** =right

```
## Warning in file(file, "rt"): cannot open file 'donnees/arbres.csv': No such
## file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```
## Error in table(arbres[, c(3, 5)]): object 'arbres' not found
```

```
## Error in row.names(densite): object 'densite' not found
```

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

--- &twocol

# Échelles logarithmiques

*** =left

```r
plot(elevation, densite[,1], axes = FALSE,
      xlab = "Élévation", ylab = "Densité",
      log = "xy")
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

--- &twocol

# Ajuster les tailles de caractères

## Arguments `cex`, `cex.lab` et `cex.axis`

*** =left

```r
plot(elevation, densite[,1], axes = FALSE,
      xlab = "Élévation", ylab = "Densité",
      cex.lab = 1.5, cex.axis = 1.25, cex = 1.5)
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

--- &twocol

# Modifier les axes

*** =left

```r
axis(1, seq(0,1000,100))
axis(2)
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

```
## Error in axis(1, seq(0, 1000, 100)): plot.new has not been called yet
```

```
## Error in axis(2): plot.new has not been called yet
```

--- &twocolw w1:55% w2:45%

# Ajouter un titre

*** =left

```r
title(main = "Densité au long du gradient d'élévation")
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

```
## Error in axis(1, seq(0, 1000, 100)): plot.new has not been called yet
```

```
## Error in axis(2): plot.new has not been called yet
```

```
## Error in title(main = "Densité au long du gradient d'élévation"): plot.new has not been called yet
```

--- &twocol

# Superposer des points d'une autre série de données

*** =left

```r
points(elevation, densite[,3], pch = 19, cex = 1.5)
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

```
## Error in axis(1, seq(0, 1000, 100)): plot.new has not been called yet
```

```
## Error in axis(2): plot.new has not been called yet
```

```
## Error in title(main = "Densité au long du gradient d'élévation"): plot.new has not been called yet
```

```
## Error in points(elevation, densite[, 3], pch = 19, cex = 1.5): object 'elevation' not found
```

--- &twocol

# Superposer des lignes

*** =left

```r
lines(elevation, densite[,1],lty = 1, lwd = 1.5)
lines(elevation, densite[,3], lty  = 3, lwd = 1.5)
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

```
## Error in axis(1, seq(0, 1000, 100)): plot.new has not been called yet
```

```
## Error in axis(2): plot.new has not been called yet
```

```
## Error in title(main = "Densité au long du gradient d'élévation"): plot.new has not been called yet
```

```
## Error in points(elevation, densite[, 3], pch = 19, cex = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 1], lty = 1, lwd = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 3], lty = 3, lwd = 1.5): object 'elevation' not found
```

--- &twocolw w1:40% w2:60%

# Ajouter une ligne de tendance

*** =left

```r
model = lm(densite[,3]~elevation)
summary(model)
abline(model, col = "darkred")
```

*** =right

```
## Error in eval(predvars, data, env): object 'densite' not found
```

```
## Error in summary(model): object 'model' not found
```

--- &twocol

# Ajouter une ligne de tendance

*** =left

```r
model = lm(densite[,3]~elevation)
abline(model, col = "darkred")
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

```
## Error in axis(1, seq(0, 1000, 100)): plot.new has not been called yet
```

```
## Error in axis(2): plot.new has not been called yet
```

```
## Error in title(main = "Densité au long du gradient d'élévation"): plot.new has not been called yet
```

```
## Error in points(elevation, densite[, 3], pch = 19, cex = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 1], lty = 1, lwd = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 3], lty = 3, lwd = 1.5): object 'elevation' not found
```

```
## Error in eval(predvars, data, env): object 'densite' not found
```

```
## Error in abline(model, col = "darkred"): object 'model' not found
```


--- &twocol

# Ajouter une légende

*** =left

```r
legend("top", bty = "n", pch = c(19,1), lty = 1,
    legend = c("Érable à sucre", "Sapin baumier"),
    cex = 1.5)
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

```
## Error in axis(1, seq(0, 1000, 100)): plot.new has not been called yet
```

```
## Error in axis(2): plot.new has not been called yet
```

```
## Error in title(main = "Densité au long du gradient d'élévation"): plot.new has not been called yet
```

```
## Error in points(elevation, densite[, 3], pch = 19, cex = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 1], lty = 1, lwd = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 3], lty = 3, lwd = 1.5): object 'elevation' not found
```

```
## Error in strwidth(legend, units = "user", cex = cex, font = text.font): plot.new has not been called yet
```

--- &twocol

# Ajouter du texte

*** =left

```r
r2 <- round(summary(model)$r.squared, 2)
text(x = 850, y = 25, paste("R2=",r2),
    cex = 21.5)
```

*** =right

```
## Error in plot(elevation, densite[, 1], axes = FALSE, xlab = "Élévation", : object 'elevation' not found
```

```
## Error in axis(1, seq(0, 1000, 100)): plot.new has not been called yet
```

```
## Error in axis(2): plot.new has not been called yet
```

```
## Error in title(main = "Densité au long du gradient d'élévation"): plot.new has not been called yet
```

```
## Error in points(elevation, densite[, 3], pch = 19, cex = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 1], lty = 1, lwd = 1.5): object 'elevation' not found
```

```
## Error in lines(elevation, densite[, 3], lty = 3, lwd = 1.5): object 'elevation' not found
```

```
## Error in strwidth(legend, units = "user", cex = cex, font = text.font): plot.new has not been called yet
```

```
## Error in summary(model): object 'model' not found
```

```
## Error in paste("R2=", r2): object 'r2' not found
```

---

# Pour plus d'information

- `?plot`
- `?par`
- `?axis`
- `?mtext`

--- .transition

# Créer d'autres types de figure

--- &twocol

# Diagramme de dispersion (Scatter plot)

*** =left


```r
arbres  <- read.csv2("donnees/arbres.csv")
densite <- table(arbres[,c(3,5)])
elevation <- as.numeric(row.names(densite))
plot(elevation, densite[,1], pch = 19,
  xlab = "Elevation", ylab = "Densité")
points(elevation, densite[,3])
```

*** =right


```
## Warning in file(file, "rt"): cannot open file 'donnees/arbres.csv': No such
## file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```
## Error in table(arbres[, c(3, 5)]): object 'arbres' not found
```

```
## Error in row.names(densite): object 'densite' not found
```

```
## Error in plot(elevation, densite[, 1], pch = 19, xlab = "Elevation", ylab = "Densité"): object 'elevation' not found
```

```
## Error in points(elevation, densite[, 3]): object 'elevation' not found
```

--- &twocol

# Diagrammes à bâtons (Bar plot)

*** =left

```r
arbres  <- read.csv2("donnees/arbres.csv")
n_tot <- table(arbres$esp)
barplot(n_tot)
```

*** =right

```
## Warning in file(file, "rt"): cannot open file 'donnees/arbres.csv': No such
## file or directory
```

```
## Error in file(file, "rt"): cannot open the connection
```

```
## Error in table(arbres$esp): object 'arbres' not found
```

```
## Error in barplot(n_tot): object 'n_tot' not found
```

--- &twocol

# Histogrammes

*** =left


```r
hist(densite[,3])
```

*** =right

```
## Error in hist(densite[, 3]): object 'densite' not found
```

--- &twocol

# Représentation 3-D

*** =left


```r
x <- 10*(1:nrow(volcano))
y <- 10*(1:ncol(volcano))

image(x, y, volcano,
  col = terrain.colors(100), axes = FALSE)

axis(1, at = seq(100, 800, by = 100))
axis(2, at = seq(100, 600, by = 100))
box()

title(main = "Maunga Whau Volcano", font.main = 4)
```

*** =right

<img src="assets/fig/unnamed-chunk-34-1.png" title="plot of chunk unnamed-chunk-34" alt="plot of chunk unnamed-chunk-34" height="500px" style="display: block; margin: auto;" />

--- &twocol

# Lignes de contour

*** =left

```r
x <- 10*(1:nrow(volcano))
y <- 10*(1:ncol(volcano))

image(x, y, volcano,
  col = terrain.colors(100), axes = FALSE)

axis(1, at = seq(100, 800, by = 100))
axis(2, at = seq(100, 600, by = 100))
box()

title(main = "Maunga Whau Volcano", font.main = 4)

contour(x, y, volcano,
  levels = seq(90, 200, by = 5),
  add = TRUE, col = "black")
```

*** =right

<img src="assets/fig/unnamed-chunk-36-1.png" title="plot of chunk unnamed-chunk-36" alt="plot of chunk unnamed-chunk-36" height="500px" style="display: block; margin: auto;" />

---

# Enregistrer une figure



```r
dev.copy2pdf(file = "test.pdf")
dev.copy2png(file = "test.png")
dev.copy2eps(file = "test.eps")
```

--- .transition

# Exercice: faire une représentation visuelle de la distribution de degrés

--- .transition

# La visualisation de réseau avec igraph

---

# Installation


```r
install.packages("igraph")
```

```
## Installing package into '/home/travis/R/Library'
## (as 'lib' is unspecified)
```

```r
library(igraph)
```

```
## 
## Attaching package: 'igraph'
```

```
## The following objects are masked from 'package:stats':
## 
##     decompose, spectrum
```

```
## The following object is masked from 'package:base':
## 
##     union
```

---

# Transformer une matrice d'adjacence en objet `igraph`


```r
library(igraph)
C <- 0.1
S <- 15
L <- matrix(0, nr = S, nc = S)
L[runif(S*S) < C] = 1
sum(L)
```

```
## [1] 20
```

```r
g <- graph.adjacency(L)
```

--- &twocol

# Utiliser la fonction `plot` pour faire une représentation d'un réseau

*** =left

```r
plot(g)
```

*** =right
<img src="assets/fig/unnamed-chunk-41-1.png" title="plot of chunk unnamed-chunk-41" alt="plot of chunk unnamed-chunk-41" width="100%" style="display: block; margin: auto;" />

--- &twocol

# Version plus esthétique sans les paramètres par défaut

*** =left

```r
plot(g, vertex.label=NA, edge.arrow.mode = 0, 
    vertex.frame.color = NA)
```

*** =right
<img src="assets/fig/unnamed-chunk-43-1.png" title="plot of chunk unnamed-chunk-43" alt="plot of chunk unnamed-chunk-43" width="100%" style="display: block; margin: auto;" />


--- .transition

# Exercice : Compiler la matrice d'adjacence et faire une première représentation du réseau avec `igraph`

--- &twocol

# Changer la couleur des noeuds

*** =left

```r
# Calculer le degré
deg <- apply(L, 2, sum) + apply(L, 1, sum)

# Le rang pour chaque noeud
rk <- rank(deg)

# Faire un code de couleur
col.vec <- heat.colors(S)

# Attribuer aux noeuds la couleur
V(g)$color = col.vec[rk]

# Refaire la figure
plot(g, vertex.label=NA, edge.arrow.mode = 0, 
    vertex.frame.color = NA)
```

*** =right
<img src="assets/fig/unnamed-chunk-45-1.png" title="plot of chunk unnamed-chunk-45" alt="plot of chunk unnamed-chunk-45" width="100%" style="display: block; margin: auto;" />

--- &twocol

# Changer la taille des noeuds

*** =left

```r
# Faire un code de ctaille
col.vec <- seq(10, 25, length.out = S)

# Attribuer aux noeuds la couleur
V(g)$size = col.vec[rk]

# Refaire la figure
plot(g, vertex.label=NA, edge.arrow.mode = 0, 
    vertex.frame.color = NA)
```

*** =right
<img src="assets/fig/unnamed-chunk-47-1.png" title="plot of chunk unnamed-chunk-47" alt="plot of chunk unnamed-chunk-47" width="100%" style="display: block; margin: auto;" />

--- &twocol

# Changer la disposition des noeuds

*** =left

```r
plot(g, vertex.label=NA, edge.arrow.mode = 0, 
    vertex.frame.color = NA, layout = layout.reingold.tilford(g))
```

*** =right
<img src="assets/fig/unnamed-chunk-49-1.png" title="plot of chunk unnamed-chunk-49" alt="plot of chunk unnamed-chunk-49" width="100%" style="display: block; margin: auto;" />

--- &twocol

# Changer la disposition des noeuds

*** =left

```r
plot(g, vertex.label=NA, edge.arrow.mode = 0, 
    vertex.frame.color = NA, 
    layout = layout.circle(g))
```

*** =right
<img src="assets/fig/unnamed-chunk-51-1.png" title="plot of chunk unnamed-chunk-51" alt="plot of chunk unnamed-chunk-51" width="100%" style="display: block; margin: auto;" />

--- &twocol

# Changer la disposition des noeuds

*** =left

```r
plot(g, vertex.label=NA, edge.arrow.mode = 0, 
    vertex.frame.color = NA, 
    layout = layout.kamada.kawai(g))
```

*** =right
<img src="assets/fig/unnamed-chunk-53-1.png" title="plot of chunk unnamed-chunk-53" alt="plot of chunk unnamed-chunk-53" width="100%" style="display: block; margin: auto;" />

---

# Calcul de propriétés

## La modularité


```r
wtc = walktrap.community(g)
modularity(wtc)
```

```
## [1] 0.36875
```

---

# Calcul de propriétés

## La distance entre les noeuds


```r
distances(g)
```

```
##       [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12] [,13]
##  [1,]    0    3    5    4    4    6    3    5    2     4     1     5     4
##  [2,]    3    0    6    5    5    7    4    6    1     5     2     6     5
##  [3,]    5    6    0    3    3    2    2    2    5     3     4     1     1
##  [4,]    4    5    3    0    2    2    1    1    4     2     3     3     2
##  [5,]    4    5    3    2    0    2    1    1    4     2     3     3     2
##  [6,]    6    7    2    2    2    0    3    1    6     4     5     1     2
##  [7,]    3    4    2    1    1    3    0    2    3     1     2     2     1
##  [8,]    5    6    2    1    1    1    2    0    5     3     4     2     1
##  [9,]    2    1    5    4    4    6    3    5    0     4     1     5     4
## [10,]    4    5    3    2    2    4    1    3    4     0     3     3     2
## [11,]    1    2    4    3    3    5    2    4    1     3     0     4     3
## [12,]    5    6    1    3    3    1    2    2    5     3     4     0     1
## [13,]    4    5    1    2    2    2    1    1    4     2     3     1     0
## [14,]    2    3    3    2    2    4    1    3    2     2     1     3     2
## [15,]    1    4    6    5    5    7    4    6    3     5     2     6     5
##       [,14] [,15]
##  [1,]     2     1
##  [2,]     3     4
##  [3,]     3     6
##  [4,]     2     5
##  [5,]     2     5
##  [6,]     4     7
##  [7,]     1     4
##  [8,]     3     6
##  [9,]     2     3
## [10,]     2     5
## [11,]     1     2
## [12,]     3     6
## [13,]     2     5
## [14,]     0     3
## [15,]     3     0
```

---

# Calcul de propriétés

## La centralité des noeuds


```r
eigen_centrality(g)$vector
```

```
##  [1] 0.031256971 0.009208911 0.365343991 0.532405528 0.827024940
##  [6] 0.431165264 0.807095893 1.000000000 0.031256971 0.337103290
## [11] 0.096883798 0.463465226 0.776588812 0.266329965 0.009208911
```

--- .transition

# Exporter des tableaux

---

# Exporter des tableaux

Exporter des tableaux depuis R vers son document de travail peut être difficile.

## La procédure habituelle serait:

1. Enregistrer le `data.frame` dans un fichier avec la fonction `write.table()` ou `write.csv()`
2. Éditer et faire la mise en page dans MS Excel ou MS Word.

Le package `knitr` permet de faciliter cette procédure en exportant le `data.frame` directement dans son document de travail LaTeX.

---

# Exporter des tableaux

Prenons le jeu de données `iris` directement disponible sous R.


```r
data(iris)
class(iris)
```

```
## [1] "data.frame"
```

```r
head(iris)
```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9         3.0          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
## 4          4.6         3.1          1.5         0.2  setosa
## 5          5.0         3.6          1.4         0.2  setosa
## 6          5.4         3.9          1.7         0.4  setosa
```

---

# Exporter des tableaux

Je souhaite maintenant exporter ce `data.frame` en LateX (un format que nous verrons lors de la prochaine séance):


```r
library(knitr)
iris_tex <- kable(iris,format="latex")
writeLines(iris_tex, con = "./donnees/iris.tex", sep = "\n", useBytes = FALSE)
```

```
## Warning in file(con, "w"): cannot open file './donnees/iris.tex': No such
## file or directory
```

```
## Error in file(con, "w"): cannot open the connection
```

--- .transition

# Travail de la semaine

---

# Consignes

- Identifier clairement vos questions de recherche
- Illustrer le réseau de collaborations
- Compléter votre analyse au moyen de 3 figures et 1 tableau
- Mettre à jour le makefile

---

# Évaluation

- Clareté des questions et adéquation des figures et du tableau
- Efficacité de la présentation
- Respect de normes graphiques
- Originalité

------ .transition

# Essai

---

# Objectifs

L'objectif d'un essai est de présenter une perspective sur un enjeu scientifique, appuyé par une argumentation logique et une lecture critique de la littérature. L'objectif spécifique de ce travail est de formuler et défendre une opinion sur les enjeux de reproductibilité en écologie. 

---

# Mise en situation

Vous êtes invités à préparer un article pour le journal Québec Science, où on vous a demandé de rédiger l'éditorial du mois sur cet enjeu.  Vous devez défendre par quels moyens vous pourriez améliorer la reproductibilité de la science si vous étiez en charge d'un laboratoire dans une institution universitaire. Vous êtes invités à faire une lecture critique de la situation actuelle et à proposer des mesures qui permettront de répondre aux enjeux identifiés.   

---

# Attentes

Québec Science est un journal destiné à un grand public, alors je vous invite à personnaliser votre argumentation et à rendre original sa présentation. Vous pouvez utiliser des tableaux, des figures ou encore des encadrés pour étayer vos propos. Essayez de faire plus que de rapporter les arguments présentés en classe, n'hésitez pas à personnaliser votre essai. 

---

# Consignes

- Le texte doit faire au maximum 1500 mots et doit être accompagné d'un résumé court, provocateur de 100 mots. Le document peut être supporté par une figure et/ou un tableau.
- Le texte peut être structuré en sections afin de permettre au lecteur de suivre le développement de l'argumentaire. 
- La section finale doit résumer les points principaux.
- Utiliser LaTeX pour la mise en forme du document.
- L'argumentaire doit être supporté de littérature scientifique appropriée. Vous pouvez certes utiliser les articles discutés en classe, mais essayez d'aller puis au-delà de ces références pour alimenter vos arguments. 

---

# Évaluation

- Respect des consignes
- Titre et résumé 
- Formulation de la proposition 
- Qualité de l'argumentation 
    + Identification des problèmes
    + Proposition de solutions
- Originalité 
- Mise en page
- Bibliographie
- Qualité de la langue

---
