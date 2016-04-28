---
title       : "Support de restructuration"
subtitle    : "Réponse à vos questions"
author      : Sylvain Tenier
job         : s.tenier@groupe-esigelec.fr
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : mathjax            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

--- 

## Séance précédente : Eclipse, structures conditionnelles

* pas de question

---  #id 

## Structure itérative *for*

* à quoi correspond le i++ ?


```java
for (int i=0;i<=10;i++)
{
  System.out.println("Voici la ligne "+i);
}

```

---

## Structure itérative *while* / *do .. while* (1)

 - Combien d'itérations ?


```java
int a=15;
while (a<10){
  System.out.println("Rattrapage !")
}
```

---

## Structure itérative *while* / *do .. while* (2)

 - Combien d'itérations ?


```java
int a=15;
do{
  System.out.println("Rattrapage !")
}while (a<10);
```

---

## Application aux tableaux (1)

- Simple boucle


```java
String impairs[]={"un","trois","cinq","sept","neuf"};
int nbImpairs=5;
for(int i=0;i<nbImpairs;i++){
  System.out.println(impairs[i]);
}
```

---

## Application aux tableaux (2)

- Double boucle


```java
String chiffres[][]={ {"un","trois","cinq","sept","neuf"},
                    {"deux","quatre","six","huit","zero"} };
int nbParSerie=5;
for(int i=0;i<2;i++){
  System.out.println("Série :" + (i+1));
  for(int j=0;j<nbParSerie;j++){
    System.out.println(chiffres[i][j]);
  }
}
```

--- .title-slide

## Restructuration séance 4

- Structures conditionnelles / itératives alternatives
- Retour sur les tableaux
- Les méthodes statiques

---

## Structures alternatives

- Conditions ternaires
  - Méthode complexe !
  - \(\mathtt{(x < y) ? y : x)}\)
  
- Itérations 

```java
String tab[] = {"toto", "titi", "tutu", "tete", "tata"};
for(String str : tab)
  // à chaque itération, str prend la valeur suivante de tab 
  System.out.println(str);
```

---

## Random

- Génération d'un nombre dans l'intervalle \(\mathbf{[min;max]} \)


```java
	public static void main(String[] args) {
		int min=3; // valeur minimale de l'intervale
		int max=45; // valeur maximale de l'intervale
		while(true){
			//tirage aléatoire
			int n=(int)(Math.random()*(max-min+1))+min;
			//affichage pour validation
			if(n==min||n==max||n==(min-1)||n==(max+1))
				System.out.println(n);
		}
```

---

## Classification 

- Utilisation du modulo pour créer un nombre défini de classes à partir de n'importe quel entier positif


```java
	public static void main(String[] args) {
		int max=1545858; // valeur très grande
		int nbClasses=4; // nombre de classes souhaitées
		while(true){
			//tirage aléatoire entre 1 et max
			int n=(int)(Math.random()*(max))+1;
			//affichage du résultat entre 1 et 4
			System.out.println("classe :"+((n%nbClasses)+1));
		}
	}
```

---

## Création et appel de méthode statique

- Comment écrire une méthode et l'appeler plusieurs fois ?


```java
	/** création d'une méthode affichant le paramètre */
	public static void afficherParametre(double valeur){
		System.out.println("la valeur passée est :" + valeur);
	}

	/** utilisation de la méthode depuis le main*/
	public static void main(String[] args) {
		double val1=3.2;
		//appel avec la variable
		afficherParametre(val1);
		//appel avec une valeur 
		afficherParametre(8.3);
		//appel avec le résultat d'un calcul
		afficherParametre(val1+2);	
	}
```

---

## Recherche de méthodes existantes

- Dans votre code
  - Ecrire le début et \(\mathbf{Ctrl+Espace}\)
  - Afficher la liste des méthodes (\(\mathbf{Ctrl+O}\))
  - Rechercher par nom (\(\mathbf{Ctrl+H}\))
- Dans les librairies
  - Utiliser la javadoc !
  - https://docs.oracle.com/javase/8/docs/api/

---

## Passage de tableaux en paramètres

- Deux tableaux de dimensions différentes ne sont pas du même type !


```java
  public static void utiliserTableau(int tab[]){
		System.out.println("le premier élément du tableau est :"+tab[0]);
	}
	
	public static void main(String[] args) {
		int tab[]={1,2,3};
		int tab2d[][]={ {1,2},{3,4},{5,6} };
		utiliserTableau(tab);
		//affiche 1
		utiliserTableau(tab2d);
		//The method utiliserTableau(int[]) in the type Essai is not 
		//applicable for the arguments (int[][])
	}
```

---
	
## Solution : surcharge de méthode !

- méthode avec *le même nom* mais des *paramètres différents*


```java
	/** affichage du premier élément d'un tableau 1D */
	public static void utiliserTableau(int tab[]){
		System.out.println("le premier élément du tableau est :"+tab[0]);
	}

	/** affichage du premier élément d'un tableau 2D */
	public static void utiliserTableau(int tab[][]){
		System.out.println("le premier élément du tableau est :"+tab[0][0]);
	}
```

---

## Méthodes de la classe String (1/2)

-	charAt(int index)
  - renvoie les caractère situé à l'indice \(\mathbf{index}\)
- substring(int beginIndex)
  - renvoie la sous-chaine à partir de \(\mathbf{beginIndex}\)
- substring(int beginIndex, int endIndex) (surcharge de la même méthode !)
  - renvoie la sous-chaine entre  \(\mathbf{beginIndex}\) et \(\mathbf{endIndex}\) (non inclus)

```java
String str="Bonjour";
str.charAt(2); //renvoie 'n'
str.charAt(5); //renvoie 'u'
str.substring(2); //renvoie "njour"
str.substring(2,5); //renvoie "njo"
str.substring(2,12); //StringIndexOutOfBoundsException !
```

---

## Méthodes de la classe String (2/2)

-	lastIndexOf(int ch)
  - renvoie la dernière occurence du caractère \(\mathbf{ch}\) ou -1 si non trouvé
- lastIndexOf(String str)
   - renvoie la dernière occurence de la chaîne \(\mathbf{str}\) ou -1 si non trouvé


```java
  String str="Bonjour";
  str.lastIndexOf('r') //renvoie 6
  str.lastIndexOf('z') //renvoie -1
  str.lastIndexOf("jou") //renvoie 3
  str.lastIndexOf("zou") //renvoie -1
```

---

## Méthode *pow* de la classe Math

- Méthode *statique* de la classe Math
- https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#pow-double-double-
- Math.pow(pow(double a, double b))
  - Renvoie a à la puissance b

---

## Casting de double en int et de int vers double


```java
double a=5.1;
double b=7.2;
//calcul avec des variables de type double 
(a * Math.pow(10, b) + .5) / Math.pow(10, b); // renvoie 5.100000031547867
//casting du résultat en int
(int) ((a * Math.pow(10, b) + .5) / Math.pow(10, b)); // renvoie 5
//casting de l'int en double
(double) ((int) ((a * Math.pow(10, b) + .5) / Math.pow(10, b))); // renvoie 5.0
}

```
