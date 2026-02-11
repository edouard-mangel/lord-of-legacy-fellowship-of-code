---

# Acte III

## Le "sprint zéro"

*Choix de la stratégie, et des technos*

---
layout: image-right
image: /images/Caradhras.jpg
backgroundSize: 140%
---

# Caradhras

## La tentative de refonte

<!-- Image suggestion : La Communauté dans la tempête -->

<v-click>

- Le chemin "évident"
- La solution "by the book"
- Architecture clean, patterns respectés
- Test Driven Development !
</v-click>

<v-click>

*"On va appliquer toutes les bonnes pratiques, ça ira super vite !"*

*"En tout cas si j'en crois Linkedin c'est dans la poche !"*

</v-click>

<!--
Caradhras c'est la solution propre. Le refacto complet. Le nouveau service bien designé.
Mais ça prend trop de temps. Le business n'attend pas.
-->

---

# Le Test Driven Development

## Le cycle Red-Green-Refactor

<div class="flex items-center justify-center gap-2 mt-12">

<v-click>
<div class="px-6 py-4 rounded-xl text-center text-white font-bold" style="background: #b91c1c; min-width: 200px;">
  <div class="text-3xl mb-2">🔴 RED</div>
  <div class="text-sm font-normal">Écrire un test<br/>qui échoue</div>
</div>
</v-click>

<v-click>
<div class="text-3xl text-gray-400 mx-2">→</div>
</v-click>

<v-click>
<div class="px-6 py-4 rounded-xl text-center text-white font-bold" style="background: #15803d; min-width: 200px;">
  <div class="text-3xl mb-2">🟢 GREEN</div>
  <div class="text-sm font-normal">Écrire le minimum<br/>de code pour passer</div>
</div>
</v-click>

<v-click>
<div class="text-3xl text-gray-400 mx-2">→</div>
</v-click>

<v-click>
<div class="px-6 py-4 rounded-xl text-center text-white font-bold" style="background: #1d4ed8; min-width: 200px;">
  <div class="text-3xl mb-2">🔵 REFACTOR</div>
  <div class="text-sm font-normal">Améliorer le code<br/>sans casser le test</div>
</div>
</v-click>

</div>

<v-click>
<div class="text-center mt-6 text-xl text-gray-400 italic">
  ↩ Recommencer avec un nouveau test
</div>
</v-click>

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
layout: two-cols-header
zoom: 0.9
---

# Tests Couplés à l'Implémentation 💩
## Tester chaque méthode publique

<v-clicks>

- Un test par méthode publique
- Si vous changez l'implémentation → tous les tests à réécrire
- Duplication massive du code de test

</v-clicks>

::left::

```csharp
[TestClass]
public class UserValidatorTests
{
    [TestMethod]
    public void CanVote_Returns_True_When_Over18()
    {
        var validator = new UserValidator();
        var user = new User { Id = 1, Age = 18 };
        Assert.IsTrue(validator.CanVote(user));
    }

    [TestMethod]
    public void CanVote_Returns_False_When_Under18()
    {
        var validator = new UserValidator();
        var user = new User { Id = 1, Age = 17 };
        Assert.IsFalse(validator.CanVote(user));
    }
}
```


<!--
Les tests couplés à l'implémentation.
On teste chaque méthode individuellement.
Si on refactore en regroupant la logique, tous les tests cassent.
-->

---
layout: two-cols-header
zoom: 0.9
---

# Tests Couplés au Comportement ✅

## Tester le cas d'usage

::left::

````md magic-move
```csharp
[TestClass]
public class UserValidatorTests
{
    [TestMethod]
    public void CanVote_Returns_True_When_Over18()
    {
        var validator = new UserValidator();
        var user = new User { Id = 1, Age = 18 };
        Assert.IsTrue(validator.CanVote(user));
    }

    [TestMethod]
    public void CanVote_Returns_False_When_Under18()
    {
        var validator = new UserValidator();
        var user = new User { Id = 1, Age = 17 };
        Assert.IsFalse(validator.CanVote(user));
    }
}
```
```csharp
[TestClass]
public class UserRegistrationTests
{
    [TestMethod]
    public void AdultUser_CanRegisterForVoting()
    {
        // Arrange
        var registrationService = new RegistrationService();
        var user = new User { Id = 1, Age = 18 };

        // Act
        registrationService.RegisterForElection(user);

        // Assert - Vérifie le changement dans le système
        var registeredUsers = registrationService.GetRegisteredVoters();
        Assert.Contains(user, registeredUsers);
    }

    [TestMethod]
    public void MinorUser_CannotRegisterForVoting()
    {
        var registrationService = new RegistrationService();
        var user = new User { Id = 2, Age = 17 };

        registrationService.RegisterForElection(user);

        Assert.Empty(registrationService.GetRegisteredVoters());
    }
}
```
````

::right::

<v-clicks>

- Test du cas d'usage métier complet
- Vérifie le changement d'état du système
- Résilient aux refactorings internes

</v-clicks>

<!--
Les tests couplés au comportement.
On teste le scénario métier, pas les méthodes individuelles.
On peut refactorer UserValidator sans casser les tests.
-->

---
layout: two-cols-header
zoom: 0.8
---

# La différence en pratique

::left::

### Couplé à l'implémentation 💩

```csharp
[TestMethod]
public void CanVote_Returns_True_When_Over18()
{
    var validator = new UserValidator();
    var user = new User { Id = 1, Age = 18 };
    Assert.IsTrue(validator.CanVote(user));
}
```

::right::

### Couplé au comportement ✅

```csharp
[TestMethod]
public void AdultUser_CanRegisterForVoting()
{
    // Arrange
    var registrationService = new RegistrationService();
    var user = new User { Id = 1, Age = 18 };

    // Act
    registrationService.RegisterForElection(user);

    // Assert
    var registeredUsers =
        registrationService.GetRegisteredVoters();
    Assert.Contains(user, registeredUsers);
}
```

<br>
<v-click>

## Le nom des tests peut participer à la documentation vivante du projet.
<br>
<br>

## On peut aussi parler de spécifications exécutables. 

</v-click>

---
layout: image-right
image: /images/moria-entrance2.jpg    
backgroundSize: 80em
---

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
layout: image-right
image: /images/balin.jpg
backgroundSize: contain
---

# Le tombeau de Balin

## Le post-mortem de 2019

<!-- Image suggestion : Le tombeau de Balin -->

*"Ici repose Balin, Seigneur de la Moria"*

<v-click>

```markdown
## Post-Mortem: Tentative de refacto du Framework

**Date:** Janvier 2019
**Lead:** @balin
**Équipe:** 5 développeurs

**Résultat:** Projet abandonné après 6 mois

**Dernière entrée du changelog:**
"Nous ne pouvons plus sortir."
"Les régressions arrivent."
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
<br>
<br>

<v-clicks>

- Classes qui importent des dizaines de packages différents 

- Classes qui font appel à des méthodes d'autres classes sans que ce soit évident. 

- La logique métier est dispersée dans tout le code, au lieu d'être centralisée. 

- Loi de Déméter violée : les objets ne parlent qu'à leurs amis proches, pas à des étrangers.

</v-clicks>

---

# Exemple 💩

```csharp {*|12|13|14}

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
zoom: 0.9
--- 

# Don't Repeat Yourself, what could go wrong ? 

````md magic-move
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

    public bool IsValid(User user) => CanVote(user) && CanDrive(user) && CanBuyAlcohol(user);
}
```
```csharp
public class User
{
    public int Id {get; private set;}
    public int Age { get; set; }

    /* ... Plein de code ... */
}

public class UserValidator
{
    private int GetAge(User user) => theOneRing.Instance().getUser(user.Id).user.Age;

    public bool CanVote(User user) => GetAge(user) >= 18;
    public bool CanDrive(User user) => GetAge(user) >= 18;
    public bool CanBuyAlcohol(User user) => GetAge(user) >= 18;

    public bool IsValid(User user) => CanVote(user) && CanDrive(user) && CanBuyAlcohol(user);
}
```
```csharp
public class User
{
    public int Id {get; private set;}
    public int Age { get; set; }

    /* ... Plein de code ... */
}

public class UserValidator
{
    private int GetAge(User user) => theOneRing.Instance().getUser(user.Id).user.Age;

    private bool IsMajor(User user) => GetAge(user) >= 18;

    public bool CanVote(User user) => IsMajor(user);
    public bool CanDrive(User user) => IsMajor(user);
    public bool CanBuyAlcohol(User user) => IsMajor(user);

    public bool IsValid(User user) => IsMajor(user);
}
```
```
```csharp
public class User
{
    public int Id {get; private set;}
    public int Age { get; set; }

    /* ... Plein de code ... */
}

public class UserValidator
{
    private int GetAge(User user) => theOneRing.Instance().getUser(user.Id).user.Age;

    private bool IsMajor(User user) => GetAge(user) >= 18;

    public bool IsValid(User user) => IsMajor(user);
}
```
````

--- 

# Vous le saviez vous, qu'on peut avoir le permis à 17 ans maintenant ? 


## Fonctionne aussi avec : "Notre produit fonctionne, on va faire une croissance à l'international !"


```csharp
public class User
{
    public int Id {get; private set;}
    public int Age { get; set; }
    public string Country { get; set; }
}

public class UserValidator
{
    private int GetAge(User user) => theOneRing.Instance().getUser(user.Id).user.Age;

    private bool isAmerican(User user) => user.Country == "US";

    public bool CanVote(User user) => GetAge(user) >= 18;
    public bool CanDrive(User user) => GetAge(user) >= (isAmerican(user) ? 16 : 18);
    public bool CanBuyAlcohol(User user) => GetAge(user) >= (isAmerican(user) ? 21 : 18);

    public bool IsValid(User user) => CanVote(user) && CanDrive(user) && CanBuyAlcohol(user);
}
```



---
layout: image-right
image: /images/Horde.png
--- 

# Les gobelins

## Les bugs en cascade

<!-- Image suggestion : L'attaque des gobelins -->

<v-click>

- Tu fixes un bug
- Trois régressions apparaissent
- Tu fixes les régressions
- Huit nouveaux bugs surgissent
- Ils viennent de partout

</v-click>

<!--
Les bugs dans un framework legacy.
Tu touches une ligne, trois régressions.
Ils sont partout, dans tous les recoins.
-->

--- 
layout: two-cols-header
---

# Un refacto nécessaire

## Tell, Don't Ask, aka "Hollywood Principle"

<br>

<v-click>

AKA "Respecter le principe d'encapsulation"
</v-click>

<br>
<br>

::left::

```csharp
public abstract class User
{
    public int Id { get; private set; }
    private int Age { get; set; }

    protected abstract int VotingAge { get; }
    protected abstract int DrivingAge { get; }
    protected abstract int DrinkingAge { get; }

    public bool CanVote() => Age >= VotingAge;
    public bool CanDrive() => Age >= DrivingAge;
    public bool CanBuyAlcohol() => Age >= DrinkingAge;
}
```

::right::

```csharp
public class FrenchUser : User
{
    protected override int VotingAge => 18;
    protected override int DrivingAge => 17;
    protected override int DrinkingAge => 18;
}

public class AmericanUser : User
{
    protected override int VotingAge => 18;
    protected override int DrivingAge => 16;
    protected override int DrinkingAge => 21;
}
```

---
layout: image-right
image: /images/balrog.jpg
---

# Le Balrog

## La faille de sécurité CVE 10

<v-click>

- Il était là depuis le début
- Les fondateurs savaient
- Ils ont préféré ne pas y toucher

<br>

- *"Ils ont creusé trop profondément... et ont adopté les patterns de l'Anneau."*

</v-click>

<v-click>

**Ce n'est pas juste une dette technique.**

C'est une faille de sécurité impossible à patcher.

*"You shall not pass... this code review."*

</v-click>

<!--
Le Balrog, c'est l'over engineering qui rend le code impossible à maintenir.'

Pas un bug qu'on peut fixer. Une décision architecturale prise il y a 15 ans.

Elle a adopté la philosophie de l'Anneau : couplage centralisé, dépendances circulaires.

C'est Sauron qui a gagné cette bataille-là, en 2008.
-->

---
layout: image
image: /images/Gandalf-Balrog.jpg
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
layout: image
image: /images/fly-you-fools.gif
backgroundSize: contain
---

# "Fly, you fools!"

