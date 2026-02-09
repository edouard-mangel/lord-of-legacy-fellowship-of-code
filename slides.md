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
layout: cover
background: /images/lord-of-the-rings.jpg

---

# Le Seigneur du Legacy 

## La Communauté du Code

*"Un code pour les gouverner tous, un code pour les lier..."*

<!-- 
Accroche : Qui ici a déjà travaillé sur un "framework maison" ?
Lever la main si vous avez déjà entendu "c'était mieux avant, quand Jean-Michel était là"
-->

---
layout: intro
---

# Introduction

## De quoi allons-nous parler ? 

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
image: images/3_rings.jpeg
--- 


# 


<!-- 
3 services pour les ops
Jenkins, 
Lambda functions, 
Kubernetes
-->


--- 
layout: image
image: /images/7_rings.jpeg
--- 


# 

<!-- 
7 services pour les développeurs
Mongo Redis Oracle GraphQL MySql, postgres, DynamoDB
-->

---
layout: image
image: /images/9_rings.jpg
backgroundSize: contain
---

#

<!--

9 services pour les managers

Jira, 
Confluence, 
Teams, 
Slack, 
SharePoint
-->

--- 
layout: image
image: /images/The_one_ring.png
backgroundSize: contain
---

---
zoom: 1.2
--- 

# Un anneau pour les coupler tous 

## Le couplage, qu'est-ce que c'est ? 

<br/>

<v-clicks>

- Une mesure pour mesurer le volume d'informations échangé par 2 composants. 

<br/>

- Plus des composants partagent d'information, et plus la modification d'un des deux nécessite de modifier l'autre. 

<br/> 

- 

</v-clicks>



<!-- 

On parle de couplage « fort » ou « serré » entre deux composants s’ils échangent beaucoup de données. 

- Au contraire, on parle de couplage faible s’ils sont indépendants ou s’ils échangent un minimum de données
-->

---

# LegacyCorp : Un Royaume Enchaîné par son Passé
Un monolithe si enchevêtré que personne n’ose plus y toucher…

## Problèmes clés

<v-click>

✅ Le Monolithe Maudit 

→ "Modifier une ligne = risque de tout casser."
</v-click>


<v-click>

✅ Les Dépendances Invisibles 🕸️

→ "Un changement dans le module de templates peut casser le module d'envoi de mails… sans que personne ne sache pourquoi."

</v-click>

<v-click>

✅ La Dette Technique ⌛

→ "Chaque nouvelle feature ajoute 10 bugs. Les devs passent 80% de leur temps à corriger."

</v-click>


---

# Une forteresse bâtie sur du sable 
If it works, don't fix it ! 

## Les conséquences 

<v-click>

❌ On ne refactore plus

→ La structure du code pourrit petit à petit
</v-click>

<v-click>

❌ On néglige la qualité

→ On passe son temps à appliquer des pansements, on n'a pas le temps pour les changements profonds
</v-click>

<v-click>

❌ On ne peut plus rien planifier

→ Les tickets restent dans un état "presque fini" pendant des semaines.
</v-click>




--- 
layout: image 
image: images/orcs.jpg
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
layout: image
image: /images/Frodo_Baggins-house.jpg
---

# Acte I

## Un voyage inattendu

---
layout: image-right
image: /images/green_hills.jpg
--- 

# La Comté

## L'équipe Recherche & Développement

<!-- Image suggestion : La Comté, verte et paisible -->

- Pas d'historique
- Pas de dette technique
- Pas de "on a toujours fait comme ça"

<v-click>

- Les hobbits n'ont jamais vu un NullPointerException 


*"Les hobbits n'ont que faire du monde extérieur..."*

</v-click>


<!--
La Comté c'est le projet qui démarre. Le backlog est vide, le repo est propre, les tests sont à 100% de coverage (parce qu'il n'y a pas de code).
-->

--- 
layout: image
image: images/bilbo_baggins.jpg
---

# Le départ du dev senior

<!--

- Il a tout construit, il connaît tous les secrets.
- Il part pour "faire un métier qui a du sens"

Le burnout du dev senior. Il a porté le projet pendant 10 ans. Il part.

Il laisse "tout ce qu'il possède" à Frodon.

Spoiler : c'est pas que des cadeaux.
-->

---
zoom: 1.5
---

# L'héritage de Bilbo

```
├── src/
│   ├── utils/
│   │   └── OneRing.java          // NE PAS TOUCHER
│   ├── legacy/
│   │   └── BilboMagic.java      // Personne ne sait ce que ça fait
│   └── config/
│       └── secrets.properties    // TODO: move to vault (2011)
├── README.md                      // Dernière mise à jour: 2014
└── CONTRIBUTING.md                // "Demander à Bilbo"
```

<v-click>

Frodon : *"Gandalf, c'est quoi ce OneRing.java ?"*

</v-click>

<!--
Qui a déjà hérité d'un projet avec un fichier "NE PAS TOUCHER" ?
-->


---
layout: image-right
image: /images/Gandalf_the_Grey.webp
zoom: 0.9
---

# Gandalf le gris

## Engineering manager et mentor de Bilbo


- Contributeur Unix depuis le siècle dernier
- Dernier dev de l'entreprise présent à sa création
- A mené de nombreuses batailles contre la complexité
- Tech lead originel du framework maison
<v-click>

- **Il sait la menace que représente l'Anneau**

</v-click>

<!--
Gandalf connaît le vrai ennemi : Sauron, l'architecte de la complexité.
Il a vu comment l'Anneau corrompt les systèmes.
-->

---
layout: image-right
image: /images/Aragorn.png
backgroundSize: contain 
---

# Aragorn

## Le Scrum Master

- Personne ne sait d'où il vient
- Il a vu des choses dans d'autres entreprises
- Il coûte cher

<v-click>

*"Vous pouvez m'appeler Grands-Pas."*

</v-click>

<!--
Le consultant qui débarque sur ton projet legacy.
Il a une aura de mystère. Il a travaillé "chez des clients qu'il ne peut pas nommer".
-->


---
layout: image-right
backgroundSize: contain
image: /images/Frodo-and-Sam-prod-incident.jpg
---

# Les process infernaux
Nos amis pourront-ils agir malgré leur rigidité ? 

<v-clicks>

- Ils rôdent à l'affut de quelqu'un qui aurait tenté de merger sans les 2 pouces et 80% de coverage. 
- **Ils sont attirés par ceux qui touchent à l'Anneau**

</v-clicks>

<!--
Supposés cadrer les déploiements et assurer la qualité des livrables, 
Les outils peuvent vite devenir des freins plutôt que des leviers de productivité

-->

--- 

# 

---
layout: intro
---

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
- Hobbits (l'équipe ops)

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
zoom: 0.9
---

# La Communauté de l'Anneau

## L'équipe cross-fonctionnelle

<!-- Image suggestion : La Communauté au complet -->

| Membre | Rôle | Spécialité |
|--------|------|------------|
| Gandalf | Engineering Manager | A la vision globale |
| Aragorn | Senior Dev / Scrum master | Sait tout faire |
| Legolas | Dev Frontend | Voit loin, tire vite |
| Gimli | Dev Backend | Robuste |
| Boromir | Product Owner | Veut des résultats |
| Frodon | Ops Junior | Porte le ticket |
| Sam | QA / Support | Loyal, indispensable |
| Merry & Pippin | Stagiaires | Là par accident |

<!--
Une équipe bien équilibrée. Sur le papier.
-->

---
layout: intro
---

# Acte III

## Le "sprint zéro"

*Choix de la stratégie, et des technos*

---
layout: image-right
image: /images/Caradhras.png
backgroundSize: 140%
---

# Caradhras

## La tentative de refonte

<!-- Image suggestion : La Communauté dans la tempête -->

<v-click>

- Le chemin "évident"
- La solution "by the book"
- Architecture clean, patterns respectés
- TDD, DDD, BDD

</v-click>

<v-click>

*"On pourrait passer par le nouveau micro-service..."*

*"Ça prendrait 3 sprints de plus."*

</v-click>

<!--
Caradhras c'est la solution propre. Le refacto complet. Le nouveau service bien designé.
Mais ça prend trop de temps. Le business n'attend pas.
-->

---
layout: image-right
image: /images/Caradhras.png
backgroundSize: 140%
zoom: 0.9
---

# L'échec de la refonte malgré les "Bonnes pratiques"
Malgré une architecture clean, des patterns respectés, et une équipe compétente, la refonte échoue.

## Le TDD qui ralentit 
<v-clicks>


Sans l'expérience d'un code découplé, le TDD devient un frein. Les tests sont difficiles à écrire, et ne couvrent pas les cas réels.

Le couplage entre les tests et l'implémentation du code, fait que les tests sont aussi fragiles que le code lui-même. 

A chaque fois qu'on veut refactorer, on casse des tests. 
</v-clicks>

<!-- 
Mettre des exemples, faire des passes décisives sur les conrérences d'après. 



-->

--- 

# Mais alors, que faire ?
Si les tests unitaires ne sont pas la solution, quelle est l'alternative ?

## Et si le problème était unitaire ? 

Quand on prend la définition d'"unitaire" dans le sens de "test qui teste une unité de code isolée", on couple les tests à la structure du code.

<v-click>

## Et si on se demandait à quoi sert un test ? 
</v-click>

<v-click>

**Un test, c'est un outil au service de notre processus d'assurance qualité.**

</v-click>

<v-click>

Un bon test doit donc : 
</v-click>

<v-clicks>

- Avertir que le système n'a plus le même comportement qu'avant.

- Nous donner confiance pour faire des changements. 

- Nous permettre de refactorer sans peur.

</v-clicks>


---

# Plus le choix 
La refonte complète est trop risquée, trop longue, et a déjà échoué.

## D'une refonte globale à un refactoring progressif

<!-- Image suggestion : Gandalf inquiet -->

*"Il y a un autre chemin..."*

<v-click>

*"Le framework maison."*

</v-click>

<v-click>

**Aragorn** : *"Tu sais ce qui s'y cache. Tu sais ce que les développeurs ont réveillé dans les profondeurs."*

</v-click>

<v-click>

**Gandalf** : *"J'ai lead cette équipe il y a 40 ans. Je connais les chemins."*

</v-click>

<!--
Gandalf était le tech lead de l'équipe Framework.
Il y a longtemps. Très longtemps.
-->

---

<!-- layout: image-right --> 

# La Moria

## Le Framework Maison™ 

<br/>
<br/>

## Autrefois la fierté de l'entreprise

<!-- Image suggestion : Les portes de la Moria -->

<v-clicks>

- "On avait notre propre Query Builder"
- "On avait notre propre injection de dépendances"
- "On avait notre propre moteur de templates"
- "... C'était magnifique"

</v-clicks>

<!--
Le framework maison. Celui qu'on a développé "parce que Spring c'était trop lourd".
Celui dont tout le monde était fier.
Mais il a adopté les patterns de l'Anneau - le couplage centralisé de Sauron.
Maintenant, c'est un piège. Celui que plus personne ne maintient.
-->

---

# L'entrée dans la Moria

## Les premiers pas

<!-- Image suggestion : L'intérieur sombre de la Moria -->

Les premiers tests passent

```bash
$ mvn test
[INFO] Running com.moria.framework.CoreTest
[INFO] Tests run: 3, Failures: 0, Skipped: 847
[INFO] BUILD SUCCESS

$ mvn test -Dtest=IntegrationTest
[INFO] Tests run: 0
[INFO] BUILD SUCCESS
```

<v-click>

Ça a l'air de fonctionner. 

Peut-être que ce n'était pas si grave ?

</v-click>

<!--
Les tests passent. Parce qu'ils sont tous skippés.
Fausse confiance.
-->

---

# Le tombeau de Balin

## Le post-mortem de 2019

<!-- Image suggestion : Le tombeau de Balin -->

<v-click>

*"Ici repose Balin, Seigneur de la Moria"*

```markdown
## Post-Mortem: Tentative de refacto du Framework

**Date:** Janvier 2019
**Lead:** @balin
**Équipe:** 5 développeurs

**Résultat:** Projet abandonné après 6 mois

**Dernière entrée du changelog:**
"Nous ne pouvons plus sortir. Les régressions arrivent."
```

</v-click>

<!--
L'équipe qui a essayé de refactorer le framework en 2019.
On n'en a plus jamais entendu parler.
-->

--- 
layout: image-right
image: /images/Gandalf_confused.jpg
---

# I have no memory of this place

## Un bon magicien se fie à son nez 

### Les code smells comme outils de détection des problèmes de design

<v-click>

Les code smells, c'est un peu comme les odeurs dans la cuisine. 

- On n'est pas sûrs qu'il y a un problème, mais ça sent mauvais.

</v-click>


--- 

# Les code smells : Couplers


## Les signes qui ne trompent pas

<v-clicks>

- Classes qui importent des dizaines de packages différents 

- Classes qui font appel à des méthodes d'autres classes sans que ce soit évident. 

- La logique métier est dispersée dans tout le code, au lieu d'être centralisée. 

- Loi de Déméter violée : les objets ne parlent qu'à leurs amis proches, pas à des étrangers.
</v-clicks>

---
layout: two-cols-header
--- 


# Exemple 💩

```csharp

public class User
{
    public int Id {get; private set;}
    public int Age { get; set; }

    /* ... Plein de code ... */
}

public class UserValidator
{
    public bool CanVote(User user) => theOneRing.Instance().getUser(user.Id).user.Age >= 18;
    public bool CanDrive(User user) => theOneRing.Instance().getUser(user.Id).user.Age >= 18;
    public bool CanBuyAlcohol(User user) => theOneRing.Instance().getUser(user.Id).user.Age >= 18;
}

```

---

# Les gobelins

## Les bugs en cascade

<!-- Image suggestion : L'attaque des gobelins -->

<v-clicks>

- Tu fixes un bug
- Trois régressions apparaissent
- Tu fixes les régressions
- Huit nouveaux bugs surgissent
- Ils viennent de partout

</v-clicks>

<!--
Les bugs dans un framework legacy.
Tu touches une ligne, trois régressions.
Ils sont partout, dans tous les recoins.
-->

---
layout: image-right
image: /images/balrog.jpg
---

# Le Balrog

## La faille de sécurité CVE 10

<v-clicks>

- Il était là depuis le début
- Les fondateurs savaient
- Ils ont préféré ne pas y toucher
- *"Ils ont creusé trop profondément... et ont adopté les patterns de l'Anneau."*

</v-clicks>

<v-click>

**Ce n'est pas juste une dette technique.**

C'est une faille de sécurité impossible à patcher.

*"You shall not pass... this code review."*

</v-click>

<!--
Le Balrog, c'est la corruption de Sauron manifestée dans le code.
Pas un bug qu'on peut fixer. Une décision architecturale prise il y a 15 ans.
Elle a adopté la philosophie de l'Anneau : couplage centralisé, dépendances circulaires.
C'est Sauron qui a gagné cette bataille-là, en 2008.
-->

---
layout: image
image: images/Gandalf-Balrog.jpg
backgroundSize: contain
--- 

# Le sacrifice de Gandalf
## *"Ce mal est au-delà de vos compétences. Fuyez !"*



<!--
Le manager/tech lead qui prend sur lui la réécriture.
Il disparaît pendant 6 mois.
L'équipe doit continuer sans lui.
-->

---

# "Fly, you fools!"

---
layout: intro
---

# Acte IV

## La reconstruction

*Ou comment se relever après le legacy*

---

# Lothlórien

## Le refactoring post-crise

<!-- Image suggestion : La forêt de Lothlórien -->

<v-clicks>

- L'équipe se pose
- On écrit la documentation
- On ajoute des tests
- On fait le deuil du code perdu
- On pleure Gandalf (qui est en réécriture)

</v-clicks>

<v-click>

Lothlórien, c'est le sprint de stabilisation après la crise.

</v-click>

<!--
Après la Moria, l'équipe a besoin de souffler.
Sprint de stab. Documentation. Tests. Rétrospective.
-->

---

# Galadriel

Senior Quality Engineer 

## La QA qui voit tout

<!-- Image suggestion : Galadriel et son miroir -->

*"Je sais ce que tu as vu. Car c'est aussi dans mon miroir."* 

<v-click>

Le miroir de Galadriel = La pipeline CI/CD. 

</v-click>

```yaml
# .gitlab-ci.yml de Lothlórien
tests:
  stage: mirror_of_truth
  script:
    - echo "Je te montre ce qui était..."
    - npm run test:regression
    - echo "Ce qui est..."
    - npm run test:integration
    - echo "Et ce qui sera si tu merges cette PR..."
    - npm run test:chaos
  allow_failure: false
  rules:
    - if: $CI_MERGE_REQUEST_ID
      when: always
```

<!--

| Cadeau | Équivalent technique |
|--------|---------------------|
| **Lumière d'Eärendil** (Frodon) | Les logs structurés |
| **Arc de la Lórien** (Legolas) | Le tooling moderne |
| **Ceinture dorée** (Sam) | Le monitoring |
| **Poignards elfiques** (Merry & Pippin) | Les feature flags |

Galadriel équipe l'équipe pour la suite.
Elle leur donne ce qu'il faut pour survivre.
-->

---
layout: image-right
--- 

# Le backlog repriorisé

## Ca suffit maintenant ! Les clients attendent

- Boromir craque : il veut utiliser la dette pour livrer plus vite


<v-click>

*"J'aurais pu livrer le Sprint 23. Give me the Ring."*

</v-click>

<!--
La Communauté se sépare. Chaque sous-équipe a maintenant sa mission.
C'est le passage du monolithe aux services indépendants.
-->


---
layout: image-right
image: /images/mount-doom-distant.jpg
---

# Frodon et Sam : Le Voyage Commence

## Direction : Mordor

<v-clicks>

- La plus petite équipe
- La mission la plus dangereuse
- Détruire l'Anneau dans le Mordor (production)
- **Le voyage ne fait que commencer**

</v-clicks>

<v-click>

*"Sauron nous attend. Mais nous devons y aller."*

</v-click>

<!--
C'est ici que Fellowship se termine.
La quête vers Mordor est lancée, mais pas terminée.
L'équipe la plus petite va affronter la complexité de Sauron directement.
-->

---

# La mort de Boromir

## Le post-mortem du PO

<!-- Image suggestion : Boromir mourant -->

<v-clicks>

- Il voulait livrer trop vite
- Il a sous-estimé les risques
- Il a voulu utiliser la dette comme feature
- Il est tombé au combat

</v-clicks>

<v-click>

*"J'aurais dû écouter la QA. J'aurais dû écouter la QA."*

</v-click>

<!--
Boromir meurt parce qu'il a voulu aller trop vite.
Le PO qui ignore les warnings.
-->


---
layout: intro
---

# Épilogue

## Les leçons de la Terre du Milieu

<v-clicks>

1. **La Comté** → Profitez du greenfield, ça ne dure pas
2. **L'Anneau** → Le couplage fort détruit tout
3. **Le Conseil** → Les réunions d'archi, c'est long mais nécessaire
4. **La Communauté** → Les équipes découplées sont résilientes
5. **La Moria** → Le framework maison vous rattrapera
6. **Le Balrog** → La dette technique existentielle existe
7. **Lothlórien** → Prenez le temps de stabiliser
8. **Amon Hen** → Parfois, il faut se séparer pour avancer

</v-clicks>

<!--
Résumé des leçons du premier film.
-->


---

# La morale

## Une citation pour finir

<v-click>

*"Même la plus petite PR peut changer le cours de l'avenir."*

— Galadriel (probablement)

</v-click>

<v-click>

<br>

*"Ne touchez pas aux frameworks maison, ça ne vieillit jamais bien."*

— Edouard Mangel (assurément)

</v-click>
