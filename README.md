# TP1 – Programmation dynamique par réflexion en Java

##  Présentation du TP

Ce TP a pour objectif de découvrir la **programmation dynamique par réflexion (Reflection)** en Java, en mettant en place une architecture en couches composée de DAO, Métier et Présentation.

La réflexion permet de charger et d'instancier des classes dynamiquement à partir de leurs noms, ce qui rend l'application plus flexible et facilite le remplacement des implémentations sans modifier directement le code de la couche Présentation.

---

##  Objectifs

- Comprendre le rôle des interfaces en Java.
- Séparer les responsabilités entre les différentes couches d'une application.
- Utiliser la réflexion Java (`Reflection`).
- Instancier des classes dynamiquement.
- Utiliser un fichier de configuration pour choisir les implémentations.
- Comprendre le principe du couplage faible.

---

##  Architecture du projet

Le projet est organisé en trois couches principales :

- **DAO (Data Access Object)** : responsable de la récupération des données.
- **Métier** : responsable de la logique métier et du traitement.
- **Présentation** : responsable de l'exécution et de l'affichage du résultat.


### 2. Couche Métier

L'interface `IMetier` définit la méthode de calcul.

La classe `MetierImpl` implémente cette interface et exploite la couche DAO pour effectuer le traitement métier.

### 3. Couche Présentation

Deux modes d'exécution sont étudiés :

- **Presentation1** : instanciation statique des classes.
- **Presentation2** : instanciation dynamique par réflexion.

### 4. Configuration dynamique

Le fichier `config.txt` permet de spécifier les classes concrètes à utiliser.

```text
dao.DaoImpl
metier.MetierImpl
```

Grâce à ce fichier, les implémentations peuvent être changées sans modifier directement la classe `Presentation2`, à condition que les nouvelles classes respectent les interfaces attendues.

---

##  Réflexion Java

La réflexion permet notamment :

- De charger une classe à partir de son nom avec `Class.forName()`.
- D'obtenir son constructeur avec `getDeclaredConstructor()`.
- De créer dynamiquement une instance avec `newInstance()`.

Exemple :

```java
Class<?> c = Class.forName("dao.DaoImpl");
Object obj = c.getDeclaredConstructor().newInstance();
```

---




##  Captures d'écran
<img width="1920" height="1080" alt="Screenshot 2026-11-25 081119" src="https://github.com/user-attachments/assets/1d2953ea-f46a-4651-81cd-11cf38a8c538" />


##  Concepts appris

- Programmation orientée objet en Java.
- Interfaces et implémentations.
- Architecture en couches.
- Réflexion Java.
- Instanciation dynamique.
- Configuration externe.
- Couplage faible et modularité.

---

##  Auteur

**Hamza Id El Baz**

Étudiant en informatique – ENS Marrakech

---

##  Conclusion

Ce TP m'a permis de comprendre comment la réflexion Java permet de rendre une application plus modulaire et flexible. L'utilisation d'interfaces et d'un fichier de configuration facilite le changement des implémentations et réduit le couplage entre les différentes couches de l'application.
