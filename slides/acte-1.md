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
image: /images/bilbo_baggins.jpg
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

```text {*|8-9|7|5|3}
├── src/
│   ├── utils/
│   │   └── OneRing.cs             // NE PAS TOUCHER
│   ├── legacy/
│   │   └── BilboMagic.cs         // Personne ne sait ce que ça fait
│   └── config/
│       └── secrets.properties    // TODO: move to vault (2011)
├── README.md                      // Dernière mise à jour: 2014
└── CONTRIBUTING.md                // "Demander à Bilbo"
```

<v-click>

Frodon : *"Gandalf, c'est quoi ce OneRing.cs ?"*

</v-click>

<!--
Qui a déjà hérité d'un projet avec un fichier "NE PAS TOUCHER" ?
-->

---
zoom: 1.2
---

# Frodon ouvre `OneRing.cs`

```csharp {*|1-2|4|6-8|10-11|13-14|16-19|21-22}{lines: true}
// TODO: refactor un jour (Bilbo, 2009)
// FIXME: ne surtout pas renommer cette classe
public class OneRing : AbstractBaseManagerServiceUtil {

    public static object DoStuff(object x, object y, int mode) {
        var session = SessionManager.Instance.GetCurrent();
        var mail = new SmtpMailService("smtp.mordor.io", 587);

        if (mode == 1) { return x; }
        else if (mode == 42) { return null; } // ne pas supprimer

        string temp = ((string)x).Substring(0,
            int.Parse((string)y) > 0 ? int.Parse((string)y) : 1);

        new SqlCommand("SELECT * FROM rings WHERE owner = '"
            + session.GetUser().GetTeam().GetManager().Name + "'",
            DbConnectionPool.Instance.GetConnection())
            .ExecuteReader();
        mail.Send(session.GetUser().Email, "Ring used", temp);
    }
}
```

<v-click>

Frodon : *"Mais... pourquoi ça `extends AbstractBaseManagerServiceUtil` ?"*

</v-click>

<!--
On cumule ici un maximum de code smells classiques :
- Commentaires TODO/FIXME vieux de 15 ans
- God class avec un nom à rallonge
- Paramètres Object partout (pas de typage)
- Magic numbers (42)
- Cast non sécurisés
- println de debug en prod
- Méthode "doStuff" qui ne veut rien dire

Code smells de couplage :
- Singletons partout (DatabasePool.getInstance(), SessionManager.getInstance())
- Instanciation directe d'un service concret (new SmtpMailService) avec config en dur
- SQL brut dans la logique métier (pas de séparation des couches)
- Violation de la Loi de Déméter : session.getUser().getTeam().getManager().getName()
- La classe fait TOUT : accès BDD, envoi de mails, logique métier
- Injection SQL en bonus
-->

---
layout: image-right
image: /images/Gandalf_the_Grey.webp
zoom: 0.9
---

# Gandalf le gris

## Engineering manager et mentor de Bilbo
<br>

- Contributeur Unix depuis le siècle dernier

- A mené de nombreuses batailles contre la complexité

- Tech lead originel du framework maison

<v-click>

## Il sait la menace que représente l'Anneau

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

## Le coach agile (free-lance)

- Personne ne sait d'où il vient

- Il a vu des choses dans d'autres entreprises

- Il coûte cher

<v-click>

## "Vous pouvez m'appeler Grands-Pas."

</v-click>

<!--
Le consultant qui débarque sur ton projet legacy.
Il a une aura de mystère. 

Il a travaillé "chez des clients qu'il ne peut pas nommer".
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

A force d'avoir des bugs et des régressions, les managers ont utilisé les pouvoirs de leurs anneaux pour instaurer des process de plus en plus rigides.


-->
