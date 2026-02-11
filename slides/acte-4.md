---

# Acte IV

## La reconstruction

*Ou comment se relever après le legacy*

---
layout: image-right
image: /images/Lothlorien.png
backgroundSize: 60em
---

# Lothlórien

## Le refactoring post-crise

<!-- Image suggestion : La forêt de Lothlórien -->

- L'équipe se pose
- On écrit la documentation
- On ajoute des tests
- On fait le deuil du code perdu


<br>

<v-click>

- On pleure Gandalf (qui est en réécriture)

Lothlórien, c'est le sprint de stabilisation après la crise.

</v-click>

<!--
Après la Moria, l'équipe a besoin de souffler.
Sprint de stab. Documentation. Tests. Rétrospective.
-->

---
layout: image-right
image: /images/Galadriel1.jpg
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
image: /images/Gimmethering.webp
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
image: /images/Boromirs-Death.jpg
---

# La mort de Boromir

## Le post-mortem du PO

<!-- Image suggestion : Boromir mourant -->

<v-clicks>

<br/>

- Il voulait livrer trop vite

- Il a sous-estimé les risques

- Il a voulu utiliser la dette comme feature

- Il est tombé au combat

</v-clicks>

<v-click>

*"J'aurais dû écouter la QA."*

</v-click>

<!--
Boromir meurt parce qu'il a voulu aller trop vite.
Le PO qui ignore les warnings.
-->


---
layout: image-right
image: /images/mount-doom-distant.jpg
backgroundSize: 130%
---

# Frodon et Sam : Le Voyage Commence

## Direction : Mordor

<br>


- La plus petite équipe
- La mission la plus dangereuse
- Détruire l'Anneau dans le Mordor (production)

<v-click>

- **Le voyage ne fait que commencer**



*"Sauron nous attend. Mais nous devons y aller."*

</v-click>

<!--
C'est ici que Fellowship se termine.
La quête vers Mordor est lancée, mais pas terminée.
L'équipe la plus petite va affronter la complexité de Sauron directement.
-->


---
layout: intro
---

# Épilogue

## Les leçons de la Terre du Milieu
<br>

<v-clicks>

1. **La Comté** → Profitez du greenfield, ça ne dure pas
2. **L'Anneau** → Le couplage non maîtrisé est un poison lent
3. **La Moria** → Le framework maison vous rattrapera
4. **Le Balrog** → La dette technique existentielle existe
5. **Lothlórien** → Prenez le temps de stabiliser
6. **Amon Hen** → Parfois, il faut se séparer pour avancer

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

--- 
layout: image
image: /images/spons.jpg
--- 

