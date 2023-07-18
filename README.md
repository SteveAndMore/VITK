# VITK

-Recalage

Pour le recalage, nous avons commencé par analyser les données et nous avons remarqué que l’image à recaler est légèrement décalée par rapport à l’image fixée, donc une simple translation devrait suffire.
C'est pourquoi nous avons utilisé la méthode ImageRegistrationMethodv4 de ITK pour effectuer le recalage. Cette méthode a besoin d'une métrique, d'un optimiseur et d'un type de transformation.

Comme dit précédemment, la transformation que l'on va utiliser est une translation en 3 dimensions. Pour l'optimiseur, une simple descente de gradient avec RegularStepGradientDescentOptimizerv4, et comme métrique, nous pouvons utiliser MattesMutualInformationImageToImageMetricv4.