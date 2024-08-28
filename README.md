# QuizData

## Description

QuizData est une application console en C# qui permet aux utilisateurs de participer à un quiz interactif sur les voitures. Les questions du quiz sont basées sur des groupes de voitures, et les réponses sont vérifiées en temps réel. L'utilisateur peut choisir de continuer à jouer après chaque question.

## Structure du projet

.gitignore
QuizData/
    QuizData/
        DataProjet/
            Cars.json
            Cars.xml
        Models/
            Cars.cs
            CarsGroup.cs
        Program.cs
        QuizData.csproj
        Services/
            DataServices.cs
    QuizData.sln
README.md

## Compréhension de LINQ et des Transformations de Données

Ce projet utilise LINQ (Language Integrated Query) pour manipuler et interroger des collections de données de manière efficace et intuitive. Les données sont stockées dans différents formats (JSON et XML) et LINQ est utilisé pour les interroger, les transformer et les combiner.

### 1. Utilisation de LINQ pour la Manipulation des Données

LINQ est un composant clé de C# qui permet de manipuler des données de manière déclarative. Dans cette application, LINQ a été utilisé pour :

- **Rechercher des voitures** : Les données des voitures sont stockées dans des fichiers JSON et XML. LINQ est utilisé pour interroger ces données, par exemple, pour lister toutes les voitures d'une certaine marque.
- **Trier les voitures** : Les données peuvent être triées par nom de voiture, par groupe (marque), ou tout autre critère pertinent.
- **Filtrer les données** : Par exemple, le filtrage peut être effectué pour n'afficher que les voitures d'une certaine marque.

### 2. Transformation de Données

Le projet inclut des transformations de données entre les formats JSON et XML. Voici comment ces transformations sont mises en œuvre :

- **Lecture de Données depuis un Fichier XML :**

```csharp
public List<Car> ReadXmlData(string filePath)
{
    XDocument xdoc = XDocument.Load(filePath);
    return xdoc.Descendants("Car")
               .Select(x => new Car
               {
                   Name = (string)x.Element("Name"),
                   Group = (string)x.Element("Group")
               })
               .ToList();
}
```

- **Lecture de Données depuis un Fichier JSON :**

```csharp
public List<Car> ReadJsonData(string filePath)
{
    string jsonData = File.ReadAllText(filePath);
    return JsonSerializer.Deserialize<List<Car>>(jsonData);
}
```
