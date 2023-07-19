# Projet VITK, fait par Steve SUISSA et Vincent DEGOT

## Recalage

Pour le recalage, nous avons commencé par analyser les données et nous avons remarqué que l’image à recaler est légèrement décalée par rapport à l’image fixée, donc une simple translation devrait suffire.
C'est pourquoi nous avons utilisé la méthode `ImageRegistrationMethodv4` de ITK pour effectuer le recalage. Cette méthode a besoin d'une métrique, d'un optimiseur et d'un type de transformation.

Comme dit précédemment, la transformation que l'on va utiliser est une translation en 3 dimensions. Pour l'optimiseur, une simple descente de gradient avec `RegularStepGradientDescentOptimizerv4`, et comme métrique, nous pouvons utiliser `MattesMutualInformationImageToImageMetricv4`.

## Segmentation

Pour la segmentation, on a décidé de prendre une approche similaire à celle que l'on a vu en TP, c'est à dire en utilisant le filtre `ConnectedThresholdImageFilter` pour la segmentation en elle-même et `RescaleIntensityImageFilter` pour pouvoir mieux visualiser l'image finale. 

De plus on a appliqué le filtre `GradientAnisotropicDiffusionImageFilter` pour flouter l'image recalée, nous permettant de détecter plus facilement si deux tumeurs sont proches. Cependant nous ne l'avons pas appliquer à la seconde image, car en accord avec nos tests, cela déterminait plus diifficilement la tumeur recherchée.
