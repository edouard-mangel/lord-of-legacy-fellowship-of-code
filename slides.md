---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# some information about your slides (markdown enabled)
title: "Le Seigneur du Legacy"
info: |
  ## Le Seigneur des Couplages
  Une histoire de dette technique en Terre du Milieu
# apply UnoCSS classes to the current slide
class: text-center
author: Edouard Mangel 
keywords: couplage, architecture, legacy, dette technique
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# duration of the presentation
duration: 45min
layout: image
image: /images/lord-of-the-rings.jpg

---

# Le Seigneur du Legacy 

## La Communauté du Code

*"Un code pour les gouverner tous, un code pour les lier..."*

<style scoped>
/* Golden yellow with outline for H1 and H2 on first slide */
h1 {
  font-size: 3em !important; /* Much larger for impact */
  color: #FFD700 !important;
  /* Dark outline effect using multiple shadows all around */
  text-shadow: 
    -2px -2px 0 #000,
     2px -2px 0 #000,
    -2px  2px 0 #000,
     2px  2px 0 #000,
     3px  3px 8px rgba(0, 0, 0, 0.9) !important;
}

h2 {
  font-size: 2em !important; /* Larger for subtitle */
  color: #FFD700 !important;
  /* Dark outline effect using multiple shadows all around */
  text-shadow: 
    -2px -2px 0 #000,
     2px -2px 0 #000,
    -2px  2px 0 #000,
     2px  2px 0 #000,
     3px  3px 8px rgba(0, 0, 0, 0.9) !important;
}

/* White italic text with shadow and centered */
p {
  font-size: 1.6em !important; /* Slightly bigger */
  text-align: center !important;
  color: white !important;
  position: absolute !important;
  top: 50% !important; /* Center vertically */
  left: 50% !important; /* Center horizontally */
  transform: translate(-50%, -50%) !important;
  width: 80% !important;
  /* Dark shadow for readability */
  text-shadow: 
    -1px -1px 0 #000,
     1px -1px 0 #000,
    -1px  1px 0 #000,
     1px  1px 0 #000,
     2px  2px 6px rgba(0, 0, 0, 0.9) !important;
}

em {
  color: white !important;
}
</style>

<!-- 
Accroche : Qui ici a déjà travaillé sur un "framework maison" ?
Lever la main si vous avez déjà entendu "c'était mieux avant, quand Jean-Michel était là"
-->

---
layout: image-right
image: /images/barad-dur.jpg
---

# Introduction

## De quoi allons-nous parler ? 

<br>

- De Legacy, 

<v-clicks>

- De couplage,

- De refactoring, 

- De mes troubles liés au stress post-traumatique 

</v-clicks>

<!-- 

Il est encore temps d'appliquer la loi des deux pieds ;)

-->


---
layout: intro
image: /images/Frodo_Baggins-house.jpg
---

# Introduction

## Présentation de LegacyCorp

---
layout: image
image: /images/ring-melting.jpg
backgroundSize: 80%
---

# Les Anneaux de Pouvoir

--- 
layout: image
image: /images/3_rings.jpeg
backgroundSize: 90%
--- 

# 3 services pour les ops

<!-- 
3 services pour les ops
Jenkins, 
Lambda functions, 
Kubernetes
-->

--- 
layout: image
image: /images/7_rings.jpeg
backgroundSize: 80%
--- 


# 7 anneaux pour les dev

<!-- 
7 services pour les développeurs
Mongo Redis Oracle GraphQL MySql, postgres, DynamoDB
-->

---
layout: image
image: /images/9_rings.jpg
backgroundSize: 90%
---

# 9 anneaux pour les managers

<!--

9 services pour les managers

plus facilement corrompus, à cause de leur proximité avec les humains et leur recherche de pouvoir

Jira, 
Confluence, 
Teams, 
Slack, 
SharePoint
-->

--- 
layout: image
image: /images/The_one_ring.png
backgroundSize: 40%
---

# Un anneau pour les coupler tous 

---
zoom: 1.2
--- 

# Un anneau pour les coupler tous 

## Le couplage, qu'est-ce que c'est ? 

<br/>

<v-clicks>

- Une mesure pour mesurer le volume d'informations échangé par 2 composants. 

- Plus des composants partagent d'information, et plus la modification d'un des deux nécessite de modifier l'autre. 

- C'est une notion transitive : si A est fortement couplé à B, et que B est fortement couplé à C, alors A et C sont aussi fortement couplés.

</v-clicks>

<!-- 

On parle de couplage « fort » ou « serré » entre deux composants s’ils échangent beaucoup de données. 

- Au contraire, on parle de couplage faible s’ils sont indépendants ou s’ils échangent un minimum de données
-->

--- 

# 💍 Couplage fort : un enchevêtrement dangereux

```mermaid
graph LR
  A[OrderService] -->|auth via| E[💍 UserService 💍]
  D[NotificationService] -->|contacts via| E
  E -->|dépend de| B[PaymentService]
  E -->|accède| C[InventoryService]
  B -->|identité via| E
  C -->|droits via| E
  A -->|appelle| B
  A -->|accède| C
  B -->|notifie| D
  B -->|dépend de| C
  C -->|lit / écrit| D
  D -->|rappelle| A

  style A fill:#8B0000,stroke:#ff4444,color:#fff
  style B fill:#8B0000,stroke:#ff4444,color:#fff
  style C fill:#8B0000,stroke:#ff4444,color:#fff
  style D fill:#8B0000,stroke:#ff4444,color:#fff
  style E fill:#8B0000,stroke:#FFD700,color:#fff,stroke-width:3px
```

<div class="text-center text-sm italic mt-2">Tous les services dépendent de UserService — l'Anneau Unique qui les lie tous.</div>

---

# LegacyCorp : Un Royaume Enchaîné par son Passé
Un monolithe si enchevêtré que personne n’ose plus y toucher…

## Problèmes clés

<v-click>

✅ Le Monolithe Maudit 

</v-click>

<br>

<v-click>

✅ Les Dépendances Invisibles 🕸️


</v-click>

<br>

<v-click>

✅ La Dette Technique ⌛


</v-click>

<!--

→ "Modifier une ligne = risque de tout casser."


→ "Un changement dans le module de templates peut casser le module d'envoi de mails… sans que personne ne sache pourquoi."

→ "Chaque nouvelle feature ajoute 10 bugs. Les devs passent 80% de leur temps à corriger."

-->

---

# Une forteresse bâtie sur du sable 
If it works, don't fix it ! 

## Les conséquences 

<v-click>

❌ On ne refactore plus

</v-click>
<br>

<v-click>

❌ On néglige la qualité

</v-click>
<br>

<v-click>

❌ On ne peut plus rien planifier

</v-click>

<!-- 

→ La structure du code pourrit petit à petit

→ On passe son temps à appliquer des pansements, on n'a pas le temps pour les changements profonds

→ Les tickets restent dans un état "presque fini" pendant des semaines.

-->

--- 
layout: image 
image: /images/orcs.jpg
backgroundSize: 70%
---

# Les équipes sont esclaves des bugs 

--- 
layout: statement
--- 

## Une menace grandissante

# La concurrence arrive !

Pendant que les efforts sont concentrés sur la maintenance du legacy, des start-ups travaillent dans l'ombre et menacent le marché de LegacyCorp. 


---
src: ./slides/acte-1.md
---

---
src: ./slides/acte-2.md
---

---
src: ./slides/acte-3.md
---

---
src: ./slides/acte-4.md
---
