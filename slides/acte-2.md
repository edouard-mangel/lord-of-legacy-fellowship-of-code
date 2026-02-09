

# Acte II

## Le Conseil

*Ou comment 4 heures de réunion n'aboutissent à rien*

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
layout: two-cols-header
---

# Le Conseil d'Elrond

## La grande réunion d'architecture

<v-click>

**Elrond ouvre le Conseil :**

*"Nous sommes réunis ici pour une raison. Sauron a forgé l'Anneau Unique.
Sa complexité corrompt nos systèmes. Il devient plus puissant chaque jour.
Nous devons décider : que faire de l'Anneau ?"*

</v-click>

::left:: 

<v-click>

**Participants :**

</v-click>
<v-clicks>

- Un magicien (l'engineering manager)
- Boromir (Product Owner)
- Aragorn (Scrum Master)
- Legolas (dev frontend)
- Gimli (dev Backend)  
- Frodon (Ops Junior)

</v-clicks>

::right::

<v-click>

**Durée prévue :** 1 heure

**Durée réelle :** 4 heures

</v-click>

<!--
La réunion d'architecture classique. Tout le monde a son avis. Personne n'est d'accord.

Finalement, c'est Frodon qui propose de détruire l'Anneau. C'est accepté, mais personne ne sait comment faire.
-->

--- 
layout: image
image: /images/One_does_not_simply.jpg
backgroundSize: contain
--- 

# Boromir (Product Owner)

## "On ne peut pas se permettre de refactorer tout le code. Nos users attendent des features."




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

*"C'est donc décidé, nous allons faire le refactoring nécessaire pour réduire notre dépendance à l'Anneau Unique."*


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

