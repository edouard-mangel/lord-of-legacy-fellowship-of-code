---
# try also 'default' to start simple
theme: bricks
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
---

# Le Seigneur du Legacy 

## La Communauté du Code

*"Un code pour les gouverner tous, un code pour les lier..."*


<!-- 
Accroche : Qui ici a déjà travaillé sur un "framework maison" ?
Lever la main si vous avez déjà entendu "c'était mieux avant, quand Jean-Michel était là"
-->

---
layout: image-right
image: /images/Frodo_Baggins-house.jpg
---

# Acte I

## Un voyage inattendu

*Ou comment un projet greenfield devient un cauchemar legacy*

---
layout: image-right
image: /images/green_hills.jpg
--- 

# La Comté

## L'équipe Recherche & Développement

<!-- Image suggestion : La Comté, verte et paisible -->

<v-clicks>

- Pas d'historique
- Pas de dette technique
- Pas de "on a toujours fait comme ça"
- Les hobbits n'ont jamais vu un NullPointerException

</v-clicks>

<v-click>

*"Les hobbits n'ont que faire du monde extérieur..."*

</v-click>


<!--
La Comté c'est le projet qui démarre. Le backlog est vide, le repo est propre, les tests sont à 100% de coverage (parce qu'il n'y a pas de code).
-->

--- 

# Bilbo s'en va

## Le départ du dev senior

<!-- Image suggestion : Bilbo qui disparaît à sa fête -->

<v-clicks>

- Il a tout construit
- Il connaît tous les secrets
- Il part "pour écrire ses mémoires"
- Il laisse ses affaires à son mentoré, Frodon

</v-clicks>


<!--
Le burnout du dev senior. Il a porté le projet pendant 10 ans. Il part.
Il laisse "tout ce qu'il possède" à Frodon.
Spoiler : c'est pas que des cadeaux.
-->

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

# L'Anneau Unique

## Le couplage absolu

<!-- Image suggestion : L'Anneau avec ses inscriptions -->

<v-clicks>

- **Un code pour les gouverner tous** → Singleton omniscient
- **Un code pour les trouver** → Dépendance globale
- **Un code pour les amener tous** → Tout passe par lui
- **Et dans les ténèbres les lier** → Impossible à retirer

</v-clicks>

<!--
L'Anneau, c'est une dépendance centrale dont tout le système dépend.
Single point of failure ultime.
Quand Sauron perd l'Anneau, son armée s'effondre.
-->


---

# Gandalf vient chercher Frodon

## "Gardez-le secret. Gardez-le sûr."

<!-- Image suggestion : Gandalf qui parle à Frodon -->

<v-click>

Traduction en code review :

</v-click>

<v-clicks>

- *"Ne commitez pas ça sur main"*
- *"Mettez ça derrière une feature flag"*
- *"Surtout, n'en parlez pas au Product Owner"*

</v-clicks>

<v-click>

La dette technique, c'est comme l'Anneau : on pense pouvoir la cacher.

</v-click>

<!--
La stratégie de Gandalf : on cache le problème et on espère que ça passe.
Spoiler : ça ne marche jamais.
-->

---

# Les Cavaliers Noirs

## Les incidents de production

<!-- Image suggestion : Nazgûl à cheval -->

<v-clicks>

- Ils arrivent toujours la nuit
- Ils arrivent toujours le vendredi
- Ils ne meurent jamais vraiment
- Ils sentent la peur (et les déploiements)

</v-clicks>

<v-click>

*"Je sens... un déploiement en production."*

</v-click>

<!--
Les Nazgûl sont attirés par l'Anneau comme les incidents sont attirés par la dette technique.
Tu crois les avoir vaincus, ils reviennent.
-->

---

# La fuite vers Bree

## L'incident de production

```
🔴 CRITICAL ALERT - 03:47 AM
Service: hobbit-journey-service
Status: NAZGUL_DETECTED
Message: "They are coming"

Runbook: https://wiki.gondor.internal/runbooks/nazgul
Last updated: Third Age 2941
Author: gandalf@istari.me (account disabled)
```

<v-click>

Le runbook renvoie vers un Confluence qui n'existe plus.

</v-click>

<!--
Qui a déjà été appelé à 3h du mat pour un incident dont le runbook date de 5 ans ?
-->

---

# Aragorn à Bree

## Le consultant externe

<!-- Image suggestion : Aragorn dans l'ombre au Poney Fringant -->

<v-clicks>

- Il a l'air louche
- Personne ne sait d'où il vient
- Il a vu des choses
- Il coûte cher

</v-clicks>

<v-click>

*"Vous pouvez m'appeler Grands-Pas."*

</v-click>

<v-click>

*"Mon TJM est de 1200€."*

</v-click>

<!--
Le consultant qui débarque sur ton projet legacy.
Il a une aura de mystère. Il a travaillé "chez des clients qu'il ne peut pas nommer".
-->

---

# Les conseils d'Aragorn

```
// Code review du consultant

// AVANT (code des hobbits)
public void runAway() {
    if (nazgulDetected) {
        panic();
        runRandomDirection();
    }
}

// APRÈS (code d'Aragorn)
public void tacticalRetreat() {
    if (threatDetected) {
        assessThreat();
        chooseSafeRoute();
        maintainFormation();
        // 15 ans d'XP en Terre du Milieu
    }
}
```

<!--
Le consultant refactore. C'est plus propre. Personne ne comprend pourquoi.
-->

---
layout: intro
---

# Acte II

## Le Conseil

*Ou comment 4 heures de réunion n'aboutissent à rien*

---

# Fondcombe

## L'architecture review

<!-- Image suggestion : Fondcombe, majestueuse -->

<v-clicks>

- C'est beau
- C'est calme
- Ça fait 6000 ans que ça tourne
- Il y a de la documentation

</v-clicks>

<v-click>

Fondcombe, c'est le monolithe bien maintenu.

L'exception qui confirme la règle.

</v-click>

<!--
Fondcombe c'est le système legacy qui marche. Celui que tout le monde cite en exemple.
"Regarde, EDF a un COBOL de 40 ans qui marche très bien."
-->

---

# Elrond

## Le Staff Engineer

<!-- Image suggestion : Elrond, regard sévère -->

<v-clicks>

- Il était là quand le système a été conçu
- Il a vu des architectures naître et mourir
- Il a survécu à la migration Oracle → PostgreSQL de l'an 3000
- Il a des opinions sur les microservices

</v-clicks>

<v-click>

*"J'étais là, Gandalf. J'étais là il y a 3000 ans, quand Isildur a refusé de merger la PR."*

</v-click>

<!--
Le Staff Engineer qui a tout vu. Il te regarde avec ce regard qui dit "j'ai déjà vu ça échouer".
-->

---

# Le Conseil d'Elrond

## La grande réunion d'architecture

<!-- Image suggestion : Le Conseil d'Elrond -->

**Participants :**
- Elfes (équipe Platform)
- Nains (équipe Backend)  
- Hommes (équipe Produit)
- Hobbits (la feature team)
- Un magicien (le CTO)

<v-click>

**Durée prévue :** 1 heure

**Durée réelle :** 4 heures

</v-click>

<!--
La réunion d'architecture classique. Tout le monde a son avis. Personne n'est d'accord.
-->

---

# Le Conseil d'Elrond

## Les échanges

<v-clicks>

**Gimli** : *"On n'a qu'à réécrire from scratch !"* 💥

**Legolas** : *"Les nains ne comprennent rien à l'architecture clean !"* 🏹

**Boromir** : *"Et si on utilisait l'Anneau en prod ?"* 

**Elrond** : *"On ne peut pas simplement utiliser l'Anneau en prod."*

**Gandalf** : *"Il doit être détruit."*

**Frodon** : *"...je peux prendre le ticket."*

</v-clicks>

<!--
Gimli veut tout réécrire. Legolas veut du clean code. Boromir veut utiliser la dette pour livrer plus vite.
Et c'est le junior qui se retrouve avec le ticket.
-->

---

# La décision architecturale

```markdown
# ADR-001: Destruction de l'Anneau Unique

## Statut
Accepté (après 4h de débat)

## Contexte
L'Anneau crée un couplage fort avec Sauron.

## Décision
Détruire l'Anneau dans les feux de la Montagne du Destin.

## Conséquences
- Sauron sera définitivement découplé
- Risque : personne n'est jamais revenu du Mordor
- Budget : 9 personnes, durée indéterminée

## Alternatives rejetées
- "Utiliser l'Anneau contre Sauron" (Boromir) → Rejeté
- "Le cacher sous un lit" (hobbits) → Rejeté
- "Réécrire Sauron" (Gimli) → Hors scope
```

<!--
L'ADR (Architecture Decision Record) du Conseil d'Elrond.
-->

---

# La Communauté de l'Anneau

## L'équipe cross-fonctionnelle

<!-- Image suggestion : La Communauté au complet -->

| Membre | Rôle | Spécialité |
|--------|------|------------|
| Gandalf | Tech Lead / Manager | A la vision globale |
| Aragorn | Senior Dev / Consultant | Sait tout faire |
| Legolas | Dev Frontend | Voit loin, tire vite |
| Gimli | Dev Backend | Robuste, bourrin |
| Boromir | Product Owner | Veut des résultats |
| Frodon | Dev Junior | Porte le ticket |
| Sam | QA / Support | Loyal, indispensable |
| Merry & Pippin | Stagiaires | Là par accident |

<!--
Une équipe bien équilibrée. Sur le papier.
-->

---

# Les principes de la Communauté

## Le couplage faible bien pensé

<v-clicks>

- **Objectif commun** : Détruire l'Anneau (la vision produit)
- **Interfaces claires** : Chacun sait ce qu'on attend de lui
- **Autonomie** : Gandalf n'a pas besoin de savoir comment Legolas code
- **Résilience** : Si un membre tombe, les autres continuent

</v-clicks>

<v-click>

*"Même la plus petite équipe peut changer le cours de l'avenir."*

</v-click>

<!--
La Communauté est un exemple de couplage faible.
Ils collaborent via un contrat (l'objectif), pas via une connaissance intime du code de chacun.
-->

---
layout: intro
---

# Acte III

## Le Framework Maison

*Ou l'histoire de la Moria*

---

# Caradhras

## La solution propre qui échoue

<!-- Image suggestion : La Communauté dans la tempête -->

<v-clicks>

- Le chemin "évident"
- La solution "by the book"
- Architecture clean, patterns respectés
- Météo : -40°C, blizzard

</v-clicks>

<v-click>

*"On pourrait passer par le nouveau micro-service..."*

*"Ça prendrait 3 sprints de plus."*

</v-click>

<!--
Caradhras c'est la solution propre. Le refacto complet. Le nouveau service bien designé.
Mais ça prend trop de temps. Le business n'attend pas.
-->

---

# Le choix

## Gandalf propose la Moria

<!-- Image suggestion : Gandalf inquiet -->

<v-click>

*"Il y a un autre chemin..."*

</v-click>

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

# La Moria

## Le Framework Maison™

<!-- Image suggestion : Les portes de la Moria -->

<v-clicks>

- Autrefois la fierté de l'entreprise
- "On avait notre propre ORM"
- "On avait notre propre DI"
- "On avait notre propre moteur de templates"
- "C'était magnifique"

</v-clicks>

<v-click>

*"Jadis, ces portes étaient gardées par des développeurs seniors..."*

</v-click>

<!--
Le framework maison. Celui qu'on a développé "parce que Spring c'était trop lourd".
Celui dont tout le monde était fier.
Celui que plus personne ne maintient.
-->

---

# Les portes de la Moria

## "Speak, friend, and enter"

<!-- Image suggestion : L'énigme de la porte -->

```bash
$ git clone git@gitlab.internal:platform/moria-framework.git
Cloning into 'moria-framework'...
Enter passphrase for key '/home/dev/.ssh/id_rsa': 
Permission denied (publickey).

$ cat README.md
# Moria Framework

Pour accéder au repo, contacter @balin
Last active: 2847 days ago
```

<v-click>

Le mot de passe ? **Mellon**. 

Mais le compte GitLab a été désactivé.

</v-click>

<!--
L'authentification au repo. Les credentials que personne n'a.
Le compte SSH de l'ancien tech lead qui a été désactivé.
-->

---

# L'entrée dans la Moria

## Les premiers pas

<!-- Image suggestion : L'intérieur sombre de la Moria -->

<v-clicks>

- L'IDE met 5 minutes à indexer
- Les imports sont en rouge mais ça compile
- Il y a 3 versions de `StringUtils`
- Le `pom.xml` fait 2000 lignes

</v-clicks>

<v-click>

*"Bientôt, vous allez découvrir l'hospitalité des devs. Du code legacy, une bonne heure de debug !"*

</v-click>

<!--
Tu ouvres le projet. Tout est rouge dans l'IDE. Mais ça compile.
Personne ne sait pourquoi.
-->

---

# Le silence inquiétant

## Les premiers tests passent

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

</v-click>

<v-click>

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

# Le journal de Mazarbul

## Le changelog abandonné

```
## v2.0.0-alpha (jamais released)

### 2019-03-15 - @balin
Début du refacto. Tout va bien.

### 2019-04-22 - @balin  
Les tests cassent. On investigue.

### 2019-05-30 - @balin
Trouvé une dépendance circulaire. C'est profond.

### 2019-06-14 - @balin
Ils ont réveillé quelque chose. Dans les classes abstraites.

### 2019-06-15 - @balin
Nous ne pouvons plus sortir.
Les bugs arrivent.
```

<!--
Le changelog d'un refacto abandonné.
On sent la descente aux enfers.
-->

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

<v-click>

```java
// TODO: fix this - @goblin1 (2016)
// FIXME: broke something - @goblin2 (2017)  
// HACK: temporary workaround - @goblin3 (2018)
// XXX: don't touch - @goblin4 (2019)
```

</v-click>

<!--
Les bugs dans un framework legacy.
Tu touches une ligne, trois régressions.
Ils sont partout, dans tous les recoins.
-->

---

# La fuite

## Le debug en urgence

```java
// Gandalf débugue en live
public void crossBridgeOfKhazadDum() {
    try {
        this.crossBridge();
    } catch (BalrogException e) {
        System.out.println("YOU SHALL NOT PASS!");
        throw new RuntimeException("Fly, you fools!", e);
    } finally {
        // TODO: handle this better
        this.fallIntoAbyss();
    }
}
```

<v-click>

Le try-catch qui sauve l'équipe mais sacrifie le tech lead.

</v-click>

<!--
Le hotfix en prod qui sauve le sprint.
Mais quelqu'un doit rester pour gérer le Balrog.
-->

---

# Le Balrog

## La dette technique existentielle

<!-- Image suggestion : Le Balrog -->

<v-clicks>

- Il était là depuis le début
- Les fondateurs savaient
- Ils ont préféré ne pas y toucher
- *"Ils ont creusé trop profondément"*

</v-clicks>

<v-click>

Le Balrog, ce n'est pas un bug.

C'est une **décision architecturale de 2008** qui pourrit tout.

</v-click>

<!--
Le Balrog, c'est la dette fondamentale.
Pas un bug qu'on peut fixer. Une décision de design prise il y a 15 ans.
Over-engineering. Trop d'abstraction. Trop de magie.
-->

---

# Le sacrifice de Gandalf

## Le manager qui prend sur lui

<!-- Image suggestion : Gandalf face au Balrog -->

*"Ce mal est au-delà de vos compétences. Fuyez !"*

<v-click>

**Traduction :**

*"Cette réécriture est au-delà de vos sprints. Continuez les features."*

*"Je m'occupe du Balrog."*

</v-click>

<v-click>

Gandalf tombe avec le Balrog.

Le tech lead part en réécriture complète pendant que l'équipe continue.

</v-click>

<!--
Le manager/tech lead qui prend sur lui la réécriture.
Il disparaît pendant 6 mois.
L'équipe doit continuer sans lui.
-->

---

# "Fly, you fools!"

## Le dernier message Slack

```
#moria-framework - il y a 6 mois

@gandalf: Je vais réécrire le core. Ne m'attendez pas.
@gandalf: Continuez sur les features.
@gandalf: Je vous retrouve de l'autre côté.
@gandalf: Ah et...
@gandalf: Ne touchez PAS au package com.moria.core.abyss
@gandalf: Fuyez, pauvres fous.
@gandalf is now offline

Cette personne n'est plus dans le workspace
```

<!--
Le dernier message du tech lead avant de partir en mission impossible.
-->

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

## La QA qui voit tout

<!-- Image suggestion : Galadriel et son miroir -->

*"Je sais ce que tu as vu. Car c'est aussi dans mon miroir."*

<v-clicks>

- Elle voit le passé (les régressions)
- Elle voit le présent (les bugs en prod)
- Elle voit le futur (ce qui va casser si tu merges)

</v-clicks>

<v-click>

Le miroir de Galadriel = La CI/CD pipeline

</v-click>

<!--
Galadriel c'est la QA senior. Celle qui voit les problèmes avant tout le monde.
Son miroir, c'est la CI qui te montre ce qui va casser.
-->

---

# Le miroir de Galadriel

## La CI pipeline

```yaml
# .gitlab-ci.yml de Lothlórien

stages:
  - mirror_of_truth

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
La CI qui empêche les catastrophes.
Elle te montre l'avenir, même si tu n'aimes pas ce que tu vois.
-->

---

# Les cadeaux de Galadriel

## Les outils pour la suite

<v-clicks>

| Cadeau | Équivalent technique |
|--------|---------------------|
| **Lumière d'Eärendil** (Frodon) | Les logs structurés |
| **Arc de la Lórien** (Legolas) | Le tooling moderne |
| **Ceinture dorée** (Sam) | Le monitoring |
| **Poignards elfiques** (Merry & Pippin) | Les feature flags |

</v-clicks>

<v-click>

*"Puisse cette lumière vous éclairer quand toutes les autres s'éteindront."*

→ *"Puissent ces logs vous aider quand la prod sera down à 3h du mat."*

</v-click>

<!--
Galadriel équipe l'équipe pour la suite.
Elle leur donne ce qu'il faut pour survivre.
-->

---

# Amon Hen

## La séparation des responsabilités

<!-- Image suggestion : Boromir qui tente de prendre l'Anneau -->

<v-clicks>

- Boromir craque : il veut utiliser la dette pour livrer plus vite
- La Communauté se divise
- Chaque équipe part avec sa responsabilité
- C'est le découplage final

</v-clicks>

<v-click>

*"J'aurais pu livrer le Sprint 23. Give me the Ring."*

</v-click>

<!--
La Communauté se sépare. Chaque sous-équipe a maintenant sa mission.
C'est le passage du monolithe aux services indépendants.
-->

---

# Le découplage de la Communauté

## Les bounded contexts

```
Communauté (Monolithe)
    │
    ├── Service "Mordor" ──────────► Frodon + Sam
    │   Responsabilité: Destruction de l'Anneau
    │
    ├── Service "Rohan" ──────────► Aragorn + Legolas + Gimli  
    │   Responsabilité: Défense des royaumes
    │
    └── Service "Isengard" ────────► Merry + Pippin (+ Ents)
        Responsabilité: Neutralisation de Saroumane
```

<v-click>

Chaque service est autonome. 

Ils ne dépendent plus les uns des autres pour avancer.

</v-click>

<!--
DDD et bounded contexts.
Chaque équipe a son domaine. Son backlog. Sa responsabilité.
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

# La leçon de Boromir

## Post-mortem

```markdown
## Incident: Chute de Boromir

**Impact:** Perte d'un membre senior de l'équipe

**Root cause:** 
- Pression business excessive
- Tentation d'utiliser des raccourcis
- Ignorance des warnings de l'équipe QA

**Actions:**
- [ ] Écouter la QA
- [ ] Ne pas utiliser la dette comme feature
- [ ] Respecter le Definition of Done

**Citation notable:**
"I would have followed you, my brother. My captain. My king."
(Message Slack de @aragorn après l'incident)
```

<!--
Le post-mortem de la mort de Boromir.
Ce qui arrive quand on ignore les avertissements.
-->

---
layout: intro
---

# Épilogue

## Les leçons de la Terre du Milieu

---

# Ce que nous avons appris

## Récapitulatif

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

# Le retour de Gandalf

## Spoiler du film 2

<!-- Image suggestion : Gandalf le Blanc -->

<v-click>

Il revient.

Gandalf le Gris devient Gandalf le Blanc.

</v-click>

<v-click>

Le tech lead revient de sa réécriture.

Il a vu des choses. Il a changé.

</v-click>

<v-click>

*"J'ai combattu le Balrog. J'ai réécrit le core. Je suis passé à Kotlin."*

</v-click>

<!--
Teaser pour la suite.
Le tech lead revient de sa mission impossible.
Il est transformé.
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

*"Ne touchez pas au package com.moria.core.abyss."*

— Gandalf (certainement)

</v-click>

<!--
Les deux leçons à retenir.
-->

---

# Merci !

## Questions ?

<v-clicks>

*"La route se poursuit sans fin..."*

*"...jusqu'au prochain sprint."*

</v-clicks>

<!-- Image suggestion : La Communauté qui part vers l'horizon -->

<v-click>

<br>

**Crédits:**
- J.R.R. Tolkien pour l'univers
- Peter Jackson pour les images
- Votre dette technique pour l'inspiration

</v-click>

<!--
Questions ?
-->

---
layout: end
---

# The End

*"I will not say: do not deploy on Friday, for not all Fridays are meant to go wrong."*