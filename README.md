<h1 align="center">Website Builder</h1>

<p align="center"><i>par Alexandre SBEGHEN</i></p>

<div align="center">
    <img alt="Bash" src="https://img.shields.io/badge/Bash-4EAA25?logo=gnubash&logoColor=fff">
</div>

<!-- 
<div align="center">
    <img alt="License" src="https://img.shields.io/github/license/Alexandre-SBEGHEN/Website-Builder">
    <img alt="Repo Size" src="https://img.shields.io/github/repo-size/Alexandre-SBEGHEN/Website-Builder">
</div>
-->
---

## Contexte

Dans mes anciens projets web, que ce soit à titre personnel ou dans le cadre de projets à l'IUT, j'ai toujours trouvé pénible de devoir faire la minification, la compilation Sass et la suppression des fichiers inutiles à la main pour obtenir un site web propre.

Je me suis demandé si je ne pouvais pas avoir un script qui ferait tout ça pour moi. Finalement, j'ai décidé de le créer moi-même en bash, plutôt que de me tourner vers un outil existant.

Ce projet m'a aussi permis de me refamiliariser avec le bash, que je n'avais pas touché depuis le début de ma première année.

## Fonctionnalités

Le script automatise les étapes suivantes lors du build d'un site web :

| Etape | Description |
|-|-|
| **Copie vers `build/`** | Copie l'ensemble du projet vers un dossier `build/`, dédié à la version prête pour la production |
| **Suppression des fichiers inutiles** | Retire du dossier `build/` les fichiers masqués (`.gitignore`, `.env`, etc), ainsi que d'autres fichiers pouvant être ajoutés directement dans le script par les développeurs |
| **Minification JS/CSS** | Minifie les fichiers JavaScript et CSS via un algorithme simple : suppression des commentaires, remplacement des espaces multiples par un seul (hors chaînes de caractères), et en supprimant les retours à la ligne |
| **Compilation Sass** | Compile les fichiers `.scss` en CSS classique, avec quelques personnalisations disponibles (voir [pré-requis](#pré-requis)) |

Le résultat est un dossier `build/` contenant une version propre et optimisée du site, prête à être déployée.

## Pré-requis

Le script repose entièrement sur du **bash pur** pour la copie, la suppression des fichiers et la minification. Aucune dépendance externe n'est nécessaire pour ces étapes.

En revanche, la compilation Sass nécessite **[Dart Sass](https://sass-lang.com/dart-sass/)**, qui doit être installé au préalable :

```bash
# Via npm
npm install -g sass

# Via Homebrew (macOS)
brew install sass/sass/sass
```

À noter qu'il existe également des versions standalone trouvables sur la **[page des releases GitHub](https://github.com/sass/dart-sass/releases/)**.

## Utilisation

Le script est compatible **Linux** et **macOS** (nativement, via bash). Sous Windows, il peut être exécuté via WSL ou Git Bash.

Une fois téléchargé, il suffit de l'exécuter avec :

```bash
./wsbuilder
```

Si aucun argument n'est fourni comme ci-dessus, un guide d'utilisation s'affiche automatiquement.

### Problèmes de droits d'exécution

Il est possible que vous n'ayez pas les droits pour exécuter le programme (erreur de type `Permission denied`). Dans ce cas, entrez :

```bash
chmod +x wsbuilder
```