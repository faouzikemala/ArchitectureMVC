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


### architecture MVC en utilisant PHP et le framework Laravel :

1. Modèle (Model) :

```php
// User.php (Modèle User)
namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    protected $fillable = ['name', 'email'];
}
```

2. Vue (View) :

```php
<!-- users.blade.php (Vue User) -->
<!DOCTYPE html>
<html>
<head>
    <title>Liste des utilisateurs</title>
</head>
<body>
    <h1>Liste des utilisateurs</h1>
    <table>
        <tr>
            <th>ID</th>
            <th>Nom</th>
            <th>Email</th>
        </tr>
        @foreach ($users as $user)
        <tr>
            <td>{{ $user->id }}</td>
            <td>{{ $user->name }}</td>
            <td>{{ $user->email }}</td>
        </tr>
        @endforeach
    </table>
</body>
</html>
```

3. Contrôleur (Controller) :

```php
// UserController.php (Contrôleur User)
namespace App\Http\Controllers;

use App\Models\User;
use Illuminate\Http\Request;

class UserController extends Controller
{
    public function index()
    {
        $users = User::all();
        return view('users', compact('users'));
    }
    
    // Autres méthodes pour gérer les actions liées aux utilisateurs
}
```

Dans cet exemple, nous utilisons le framework Laravel qui facilite la mise en œuvre de l'architecture MVC. Le modèle "User" étend la classe de modèle fournie par Laravel, et nous définissons les colonnes "name" et "email" comme attributs remplissables.

La vue "users.blade.php" utilise le moteur de templating Blade de Laravel pour afficher la liste des utilisateurs à partir des données fournies par le contrôleur.

Le contrôleur "UserController" utilise la méthode "index()" pour récupérer tous les utilisateurs à partir du modèle "User" et les passe à la vue "users.blade.php" en utilisant la fonction "view()" de Laravel.

Cet exemple utilise Laravel, mais l'architecture MVC peut être mise en œuvre dans d'autres frameworks et langages de programmation avec des variations syntaxiques. L'idée principale reste la séparation des responsabilités entre les modèles, les vues et les contrôleurs pour rendre le code plus organisé, maintenable et évolutif.
