# MvcMovie - Application de Gestion de Films

Une application web ASP.NET Core MVC développée avec **.NET 8** pour gérer une collection de films. Cette application permet de consulter, créer, modifier et supprimer des films dans une base de données SQL Server.

## 🎯 Fonctionnalités principales

- **Consultation des films** : Affichage de la liste complète des films avec leurs détails
- **Créer** : Ajouter de nouveaux films à la base de données
- **Modifier** : Mettre à jour les informations des films existants
- **Supprimer** : Retirer les films de la collection
- **Recherche et filtrage** : Rechercher les films par titre ou genre
- **Interface responsive** : Une interface utilisateur claire et facile à utiliser

## 🛠️ Stack technologique

| Technologie | Version | Description |
|------------|---------|------------|
| **.NET** | 8.0 | Framework de développement |
| **ASP.NET Core** | 8.0 | Framework web |
| **Entity Framework Core** | 8.0 | ORM pour l'accès à la base de données |
| **SQL Server** | - | Base de données relationnelle |
| **C#** | 12 | Langage de programmation |

## 📋 Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- [Visual Studio 2022](https://visualstudio.microsoft.com/) (Community ou supérieur) ou [Visual Studio Code](https://code.visualstudio.com/)
- [SQL Server 2019](https://www.microsoft.com/sql-server/) ou une version plus récente (ou SQL Server Express)
- Git (optionnel, pour cloner le repository)

## 📦 Installation

### 1. Cloner le repository (si applicable)
```bash
git clone https://github.com/HamzaEssoussi/MvcMovie.git
cd MvcMovie
```

### 2. Restaurer les dépendances NuGet
```bash
dotnet restore
```

### 3. Configurer la base de données

#### Option A : Utiliser la chaîne de connexion par défaut
Modifiez le fichier `appsettings.json` :

```json
{
  "ConnectionStrings": {
    "MvcMovieContext": "Server=(localdb)\\mssqllocaldb;Database=MvcMovieDb;Trusted_Connection=true;"
  }
}
```

#### Option B : Utiliser SQL Server directement
```json
{
  "ConnectionStrings": {
    "MvcMovieContext": "Server=YOUR_SERVER;Database=MvcMovieDb;User Id=sa;Password=YOUR_PASSWORD;"
  }
}
```

### 4. Appliquer les migrations
```bash
dotnet ef database update
```

Si vous n'avez pas encore créé de migrations :
```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## 🚀 Démarrage rapide

### Avec Visual Studio
1. Ouvrez le projet dans Visual Studio
2. Définissez le projet de démarrage
3. Appuyez sur `F5` ou cliquez sur le bouton **Start**

### Avec la ligne de commande
```bash
dotnet run
```

L'application s'ouvrira par défaut sur `https://localhost:7001`

## 📁 Structure du projet

```
MvcMovie/
├── Controllers/           # Contrôleurs MVC
│   ├── HomeController.cs
│   └── MoviesController.cs
├── Models/               # Modèles de données
│   ├── Movie.cs
│   └── ErrorViewModel.cs
├── Views/                # Vues Razor
│   ├── Home/
│   ├── Movies/
│   └── Shared/
├── Data/                 # Contexte Entity Framework
│   └── MvcMovieContext.cs
├── wwwroot/              # Ressources statiques
├── Program.cs            # Configuration de l'application
├── appsettings.json      # Paramètres de configuration
└── MvcMovie.csproj       # Fichier de projet
```

## 🗄️ Modèle de données

### Modèle Movie
```csharp
public class Movie
{
    public int Id { get; set; }              // Identifiant unique
    public string Title { get; set; }        // Titre du film
    public DateTime ReleaseDate { get; set; }// Date de sortie
    public string Genre { get; set; }        // Genre du film
    public decimal Price { get; set; }       // Prix
}
```

## 🔄 Points de terminaison API

| Méthode | Route | Description |
|---------|-------|------------|
| GET | `/Movies` | Affiche la liste de tous les films |
| GET | `/Movies/Details/{id}` | Affiche les détails d'un film spécifique |
| GET | `/Movies/Create` | Affiche le formulaire de création |
| POST | `/Movies/Create` | Crée un nouveau film |
| GET | `/Movies/Edit/{id}` | Affiche le formulaire de modification |
| POST | `/Movies/Edit/{id}` | Met à jour un film existant |
| GET | `/Movies/Delete/{id}` | Affiche la confirmation de suppression |
| POST | `/Movies/Delete/{id}` | Supprime un film |

## 🔍 Recherche et filtrage

Depuis la page d'accueil, vous pouvez :

- **Rechercher par titre** : Entrez le titre du film
- **Filtrer par genre** : Sélectionnez un genre dans la liste déroulante
- **Combinaison** : Utilisez la recherche et le filtrage ensemble

## ⚙️ Configuration

### Variables d'environnement
Vous pouvez définir des variables d'environnement pour la configuration :

```
ASPNETCORE_ENVIRONMENT=Development
ConnectionStrings__MvcMovieContext=Server=...
```

### Paramètres importants (appsettings.json)
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning"
    }
  },
  "AllowedHosts": "*"
}
```

## 🧪 Tests

Exécutez les tests unitaires (si disponibles) :
```bash
dotnet test
```

## 📝 Migrations Entity Framework

### Créer une nouvelle migration
```bash
dotnet ef migrations add NomDeLaMigration
```

### Appliquer les migrations
```bash
dotnet ef database update
```

### Annuler la dernière migration
```bash
dotnet ef migrations remove
```

### Voir l'historique des migrations
```bash
dotnet ef migrations list
```

## 🐛 Dépannage

### Problème : La base de données n'est pas créée
**Solution** : Exécutez `dotnet ef database update` pour appliquer les migrations.

### Problème : Erreur de connexion SQL Server
**Solution** : Vérifiez que SQL Server est en cours d'exécution et que la chaîne de connexion est correcte.

### Problème : Port déjà utilisé
**Solution** : Modifiez le port dans `Properties/launchSettings.json`.

## 📚 Ressources utiles

- [Documentation ASP.NET Core](https://docs.microsoft.com/aspnet/core)
- [Documentation Entity Framework Core](https://docs.microsoft.com/ef/core)
- [Tutoriel MVC ASP.NET Core](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc)
- [Guide .NET 8](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet)

## 🤝 Contribution

Les contributions sont bienvenues ! Voici comment contribuer :

1. Forkez le repository
2. Créez une branche pour votre fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Commitez vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Poussez vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 👤 Auteur

**Hamza Essoussi**

- GitHub: [@HamzaEssoussi](https://github.com/HamzaEssoussi)

## 📞 Support

Si vous avez des questions ou besoin d'aide, n'hésitez pas à :

- Ouvrir une [Issue](https://github.com/HamzaEssoussi/MvcMovie/issues)
- Me contacter directement via GitHub

## 📅 Historique des versions

### Version 1.0.0 (Actuelle)
- ✅ Fonctionnalités CRUD complètes
- ✅ Interface utilisateur responsive
- ✅ Recherche et filtrage
- ✅ Intégration Entity Framework Core
- ✅ .NET 8 et SQL Server

---

**Dernière mise à jour** : Janvier 2025

Fait avec ❤️ par Hamza Essoussi
