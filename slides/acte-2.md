---
layout: image
image: /images/Council.png
backgroundSize: contain
---

# Acte II : Le Conseil

## *Ou comment 1 heure de réunion se transformer en 4*

<!--
Le Conseil d'Elrond, des responsables de différents domaines qui se réunissent pour décider du sort de l'Anneau Unique (la dépendance critique).

--> 

---
layout: image-right
image: /images/Elrond.jpg
backgroundSize: contain
---

# Elrond

## Le Staff Engineer

- Il a survécu à la migration Oracle → PostgreSQL de 2014

*"J'étais là, Gandalf. J'étais là il y a 3000 ans, quand Isildur a refusé de merger la PR."*

<!--
Le Staff Engineer qui a tout vu. Il te regarde avec ce regard qui dit "j'ai déjà vu ça échouer".
-->

---
layout: image-left
image: /images/Elrond.jpg
backgroundSize: contain
---

# Le Conseil d'Elrond

## La grande réunion d'architecture
<br>

<v-click>

#### "Nous sommes réunis ici pour une raison. 

#### Le couplage induit par l'Anneau Unique.
<br>

#### Sa complexité corrompt nos systèmes. Il devient plus puissant chaque jour.
<br>

#### Nous devons décider : que faire de l'UserService ?"

</v-click>


---
layout: image-left
image: /images/Boromir-buste.jpg
backgroundSize: contain
---

# Boromir (Product Owner)

## Pourquoi ne pas l'utiliser à son plein potentiel ? 

<br>

## En utilisant l'anneau à notre avantage, nous pourrons livrer plus vite !

---
layout: image-right
image: /images/Aragorn_buste.jpg
backgroundSize: contain
---

# Aragorn (Coach agile externalisé)

## L'anneau est trop dangereux, ça va se retourner contre nous !

<br>


---
layout: image-left
image: /images/Boromir-buste.jpg
backgroundSize: contain
---

# Boromir (Product Owner)

## Qu'est-ce qu'un scrum master connaît à l'architecture ? 


---
layout: image-right
image: /images/Legolas-upset.jpg
backgroundSize: 160%
---

# Legolas (Dev Frontend)

## Aragorn n'est pas un simple Scrum Master
<br>

## Il est l'héritier du trône d'Isildur. 
<br>

## C'est lui l'architecte légitime du module de paiements. 


---
layout: image-left
image: /images/Boromir-buste.jpg
backgroundSize: contain
---

# Boromir (Product Owner)

## La team paiements est une feature team auto-organisée. 

<br>

## Elle n'a pas besoin d'un architecte "tour d'ivoire" pour faire son travail.

--- 

# La réunion d'architecture classique


## Personne n'est d'accord, tout le monde a son avis, et personne ne veut faire de compromis.


<br> 
<br> 
<br> 

<v-click>

### Jusqu'à ce que Frodon, le plus junior de l'équipe, prenne la parole :

</v-click>


--- 
layout: image-right
image: /images/Frodo.jpg
backgroundSize: cover
---

# Frodon (Ops Junior)

## Je peux prendre le ticket ! 


<br> 
<br> 

## Je peux porter l'Anneau jusqu'au Mordor (production) et le détruire dans les feux de la Montagne du Destin !


<br> 
<br> 



---
zoom: 0.9
---

# La décision architecturale

```markdown
# ADR-001: Destruction de l'Anneau de Sauron

## Statut
Accepté (après 4h de débat)

## Contexte
Sauron a créé l'Anneau pour imposer un couplage fort sur tous les systèmes.
Sa complexité grandit. Nos incidents de production augmentent.
Sauron doit être vaincu.

## Décision
Détruire l'Anneau dans les feux de la Montagne du Destin (production).
Mission confiée à une petite équipe (Frodon + support).

## Conséquences
- Sauron sera définitivement découplé
- Risque : personne n'est jamais revenu du Mordor
- Budget : 9 personnes, durée indéterminée
- **Success metric**: Destruction de OneRing.java en prod

## Alternatives rejetées
- "Utiliser l'Anneau contre Sauron" (Boromir) → L'Anneau sert toujours Sauron
- "Le cacher" (hobbits) → Sauron le trouvera toujours
- "Réécrire Sauron" (Gimli) → Hors scope
```

<!--
L'ADR (Architecture Decision Record) du Conseil d'Elrond.
-->


---
layout: two-cols-header
---

# Le Conseil d'Elrond

## La grande réunion d'architecture



**Elrond clôture le Conseil :**

*"C'est donc décidé, nous allons faire le refactoring nécessaire pour détruire le UserService."*


::left:: 


**Participants :**

- Un magicien (l'engineering manager)
- Boromir (Product Owner)
- Aragorn (Scrum Master)
- Legolas (dev frontend)
- Gimli (dev Backend)  
- Frodon (Ops Junior)



::right::

~~Durée prévue : 1 heure~~

**Durée réelle :** **4 heures**


<!--
La réunion d'architecture classique. Tout le monde a son avis. Personne n'est d'accord.

Finalement, c'est Frodon qui propose de détruire l'Anneau. C'est accepté, mais personne ne sait comment faire.
-->


---
zoom: 0.9
layout: image
image: /images/fellowship.jpg
backgroundSize: 115%
---

# La Communauté de l'Anneau : L'équipe cross-fonctionnelle

<!--

| Membre | Rôle | Spécialité |
|--------|------|------------|
| Gandalf | Engineering Manager | A la vision globale |
| Aragorn | Senior Dev / Scrum master | Sait tout faire |
| Legolas | Dev Frontend | Voit loin, tire vite |
| Gimli | Dev Backend | Robuste |
| Boromir | Product Owner | Veut des résultats |
| Frodon | Ops Junior | Porte le ticket |
| Sam | QA / Support | Loyal, indispensable |
| Merry & Pippin | Alternants  | Là par accident |
Une équipe bien équilibrée. Sur le papier.
-->


--- 
layout: image
image: /images/One_does_not_simply.jpg
backgroundSize: contain
--- 

# Boromir (Product Owner)

## "On ne peut pas se permettre de refactorer tout le code. Nos users attendent des features."
