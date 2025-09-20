Lab 02 - Plastic waste
================
Alice Thibault
16 septembre 2025

## Chargement des packages et des données

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read_csv("data/plastic-waste.csv")
```

Commençons par filtrer les données pour retirer le point représenté par
Trinité et Tobago (TTO) qui est un outlier.

``` r
plastic_waste <- plastic_waste %>%
  filter(plastic_waste_per_cap < 3.5)
```

## Exercices

### Exercise 1

``` r
ggplot(data=plastic_waste %>% filter(plastic_waste_per_cap < 3.5), aes(x=plastic_waste_per_cap)) +
geom_histogram(binwidth=0.2) +
facet_wrap(~continent)
```

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->

### Exercise 2

``` r
ggplot(data=plastic_waste %>% filter(plastic_waste_per_cap < 3.5), aes(x=plastic_waste_per_cap, color=continent,fill=continent)) +
  geom_density(alpha=0.25)
```

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->
Décrivez pourquoi le reglage de la couleur (color et fill) et le réglage
de la transparence (alpha) ne se trouvent pas au même endroit ? L’un
étant réglé dans aes et l’autre dans geom_density()

Les réglages color et fill sont dans aes, car ils dépendent des
variables et modifient leur présentation visuelle. Pour le paramètre
alpha, ce dernier est placé dans geom_density, puisqu’il agit sur la
transparence de la couleur sur graphique directement et non sur la
variable choisie.

### Exercise 3

Boxplot:

``` r
ggplot(data=plastic_waste %>% filter(plastic_waste_per_cap < 3.5), aes(x=continent, y=plastic_waste_per_cap)) + geom_boxplot()
```

![](lab-02_files/figure-gfm/plastic-waste-boxplot-1.png)<!-- -->

Violin plot:

``` r
ggplot(data=plastic_waste %>% filter(plastic_waste_per_cap < 3.5), aes(x=continent, y=plastic_waste_per_cap)) + geom_violin()
```

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

Qu’est ce que les violin plots permettent de voir sur les données que
les boxplot ne permettent pas ?

Les violoins plots permettent de voir une meilleure répartition des
données tandis que les boxplots permettent seulement de voir des
résultats comme la médiane, les quartiles et les données extrêmes qui ne
sortent de la boîte.

### Exercise 4

``` r
ggplot(data=plastic_waste %>% filter(plastic_waste_per_cap < 3.5), aes(x=mismanaged_plastic_waste_per_cap, y=plastic_waste_per_cap, color=continent)) + geom_point()
```

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

On voit la relation entre les déchets qui sont produit et comment ils
sont gérés. On voit bien que pour ce qui est de l’Afrique, la majorité
des déchets qui sont produits sont mal gérés, mais qu’à l’inverse, la
majorité des déchets produits par l’Europe sont bien gérés. On voit
qu’entre les deux de ces extrémités, l’Amérique du nord a environ la
moitié de ses déchets produits qui sont mal gérés et que l’autre moitié
produites est bien gérées. Le graphique montre bien la répartition des
déchets bien et mal gérés par les différents pays.

### Exercise 5

``` r
ggplot(data=plastic_waste %>% filter(plastic_waste_per_cap < 3.5), aes(x=plastic_waste_per_cap, y=total_pop,color=continent)) + geom_point()
```

    ## Warning: Removed 10 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-total-1.png)<!-- -->

``` r
ggplot(data=plastic_waste %>% filter(plastic_waste_per_cap < 3.5), aes(x=plastic_waste_per_cap, y=coastal_pop, color=continent)) + geom_point()
```

![](lab-02_files/figure-gfm/plastic-waste-population-coastal-1.png)<!-- -->

On voit sur le deuxième graphique qu”il y a plus de pays situées sur le
bord de l’eau où la population a moins tendance à produire beaucoup de
déchets par habitant que si l’on regarde le graphique contenant
l’entièreté de la population.

## Conclusion

Recréez la visualisation:

``` r
# insert code here
```
