# ArchitectureMVC

Voici un exemple simplifié de codes avec une architecture MVC en utilisant un langage de programmation comme PHP :

1. Modèle (Model) :

```php
// Utilisateur.php (Modèle Utilisateur)
class Utilisateur {
  private $login;
  private $nom;
  private $prenom;
  
  // Méthode pour récupérer les utilisateurs depuis la base de données
  public static function getUtilisateurs() {
    // Code pour récupérer les utilisateurs depuis la base de données
    // et retourner un tableau d'objets Utilisateur
  }
  
  // Autres méthodes pour gérer les opérations liées aux utilisateurs
}
```

2. Vue (View) :

```php
<!-- utilisateur_view.php (Vue Utilisateur) -->
<!DOCTYPE html>
<html>
<head>
  <title>Liste des utilisateurs</title>
</head>
<body>
  <h1>Liste des utilisateurs</h1>
  <table>
    <tr>
      <th>Login</th>
      <th>Nom</th>
      <th>Prénom</th>
    </tr>
    <?php foreach ($utilisateurs as $utilisateur) : ?>
    <tr>
      <td><?php echo $utilisateur->getLogin(); ?></td>
      <td><?php echo $utilisateur->getNom(); ?></td>
      <td><?php echo $utilisateur->getPrenom(); ?></td>
    </tr>
    <?php endforeach; ?>
  </table>
</body>
</html>
```

3. Contrôleur (Controller) :

```php
// utilisateur_controller.php (Contrôleur Utilisateur)
class UtilisateurController {
  public function afficherUtilisateurs() {
    // Appeler la méthode du modèle pour récupérer les utilisateurs
    $utilisateurs = Utilisateur::getUtilisateurs();
    
    // Appeler la vue et transmettre les données à afficher
    include 'utilisateur_view.php';
  }
  
  // Autres méthodes pour gérer les actions liées aux utilisateurs
}
```

En utilisant ce modèle MVC, vous pouvez organiser vos fonctionnalités par modèles, vues et contrôleurs. Les modèles gèrent les données et les opérations liées à ces données, les vues gèrent l'interface utilisateur et l'affichage des données, et les contrôleurs coordonnent les actions entre les modèles et les vues.

Dans cet exemple, le contrôleur "UtilisateurController" appelle la méthode statique "getUtilisateurs()" du modèle "Utilisateur" pour récupérer les utilisateurs depuis la base de données. Ensuite, il passe les données récupérées à la vue "utilisateur_view.php" qui les affiche dans un tableau HTML.

Cet exemple est simplifié, mais il illustre comment organiser le code en utilisant l'architecture MVC pour séparer les préoccupations et faciliter la maintenance et l'évolution de l'application.
