# Évolution Artificielle

## 2V483 project 

Dans le cadre d'un projet pour l'unité d'enseignement complémentaire *"programmation avancée en python pour la bioinformatique"*, nous avons tenté de simuler le processus de l'évolution biologique. 
Pour ce faire, nous avons pris comme modèle une molécule d'ARN de transfert (ARNt). 
L'ARNt est une petite molécule d'ADN qui permet de traduire un codon en son acide aminé correspondant lors de la traduction de l'ADN en protéines. 
Grâce au langage de programmation python, nous avons codé différents processus à l'origine de l'évolution biologique 
intervenant lors de la reproduction tel que : 
* les mutations (délétions, insertions, ou substitutions)
* la recombinaison entre séquences 
* et la sélection des séquences les mieux adaptés, en les comparant à une "séquence cible", c'est à dire dont la configuration est optimale.

Ainsi nous avons simulé la reproduction d'une population d'ARNt. Nous avons ensuite observé à l'aide d'une courbe tracée grâce à la bibliothèque python Matplotlib, l'évolution de nos séquences en analysant leur score. Le score des séquences étant une mesure de la ressemblance de nos séquences générées à la "séquence cible".  

Dans la réalisation de ce  programme, nous avons utilisé un certain nombre de fonctions. La première, nommée PopDeDepart a pour but de créer notre population d'ARNt originel, celle que l'on va faire évoluer au fil des générations. Elle prend en argument la longueur de la séquence de notre population d'origine (ici, 75 nucléotides) et le nombre d'individus (ici, 10 000). Elle renvoit une liste de listes, contenant la séquence de chaque individu de cette première génération.
Ensuite, la fonction ListeAppariements a pour objectif de créer une liste des appariements cibles que nous espérons obtenir au fil des générations, ce qui va être utile pour calculer le score de chaque individu et donc sa facilité à se reproduire ou non. Elle prend pour argument "repli" qui est une liste de listes contenant les "coordonées" de nos replis cibles, c'est-à-dire le premier nucléotide appariés dans le sens 5'-->3', le premier dans le sens 3'-->5' et le dernier dans le sens 5'-->3'. Cette focniton renvoie une liste contenant tous les appariements cibles.
Pour qu'ils puissent y avoir des appriements, il faut que les nucléotides face à faces sont complémentaires comme AU, CG ou UG. Ainsi, nous avons créer la troisième fonction "complementaire" afin de vérifier que les nucléotides qui sont en face des autres et qui doivent s'apparier sont bien complémentaires. Elle prend en arguments les séquences d'une génération (sequences) ainsi que les positions d'appariements cibles explicitées dans la fonction suivante: la fonction score. La fonction "complementaire" revoie un False ou True en fonction de si l'appariement est faisable ou non.
La fonction suivante, la fonction score, a pour but de calculer le score de chaque individu d'une génération en fonction de la position des appariements et des séquences consensus de l'ARNt en fonction de l'ARNt cible. Plus l'ARNt a de ressemblance à la séquence cible, plus son score sera élevé. Cette fonction a donc pour argument la liste des appariements cibles, les séquences d'une génération et les séquences consensus cibles. Elle renvoie la liste des scores de toute une génération.
