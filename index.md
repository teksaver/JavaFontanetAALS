---
title       : "Séance 3 : tableaux"
subtitle    : questions de restructuration
author      : Sylvain Tenier
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Séance précédente : Eclipse, structures conditionnelles

* pas de question

--- .class #id 

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
