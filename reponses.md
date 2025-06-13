# Réponse à la Question 1

**Quelle est la principale différence entre l'installation locale et l'installation globale des paquets avec npm ?**

La principale différence réside dans l'endroit où les paquets sont installés et leur accessibilité :

- **Installation locale** :
  - Les paquets sont installés dans le dossier `node_modules` du projet courant.
  - Ils ne sont accessibles qu'à ce projet.
  - Commande : `npm install <package>`
  - Exemples : frameworks, bibliothèques et outils spécifiques au projet (React, Express, ESLint, etc.).

- **Installation globale** :
  - Les paquets sont installés dans un dossier global de la machine.
  - Ils sont accessibles depuis n'importe quel projet via la ligne de commande.
  - Commande : `npm install -g <package>`
  - Exemples : outils CLI utilisables partout (npm, nodemon, typescript, create-react-app, etc.).


# Réponse à la Question 2

**Pourquoi Webpack est-il utilisé en interne et pourquoi est-il nécessaire pour gérer à la fois plusieurs fichiers JavaScript et des extensions spéciales comme .vue ?**

Webpack est utilisé car il permet de :

- **Gérer plusieurs fichiers JavaScript** :
  - Dans une application moderne, le code est réparti en plusieurs fichiers pour une meilleure organisation.
  - Webpack rassemble tous ces fichiers et leurs dépendances en un ou plusieurs fichiers finaux optimisés pour le navigateur.
  - Cela simplifie l'inclusion des scripts et améliore les performances.

- **Gérer les extensions spéciales comme `.vue`** :
  - Les fichiers `.vue` contiennent du HTML, du CSS et du JavaScript dans un seul fichier composant.
  - Les navigateurs ne comprennent pas ce format nativement.
  - Webpack, avec des loaders comme `vue-loader`, transforme ces fichiers en code JavaScript standard compréhensible par le navigateur.


# Réponse à la Question 3

**Quel est le rôle de Babel et comment browserslist peut-il configurer sa sortie ?**

Babel est un outil de transpilation JavaScript. Son rôle principal est de convertir du code JavaScript moderne (ES6+ ou JSX, TypeScript, etc.) en une version plus ancienne et compatible avec un plus grand nombre de navigateurs. Cela permet d'utiliser les dernières fonctionnalités du langage sans se soucier de la compatibilité avec les navigateurs plus anciens.

**Browserslist** est un outil qui permet de définir précisément quels navigateurs doivent être supportés par le projet. Babel utilise cette configuration pour savoir jusqu'à quel point il doit transformer le code. Par exemple, si on indique dans browserslist que l'on veut supporter les dernières versions de Chrome et Firefox uniquement, Babel ne transformera que les fonctionnalités non supportées par ces navigateurs. Si on veut supporter Internet Explorer 11, Babel fera plus de transformations pour garantir la compatibilité.

**Exemple de configuration :**
Dans le fichier `package.json` ou dans un fichier `.browserslistrc` :
```
"browserslist": [
  "> 1%",
  "last 2 versions",
  "not dead"
]
```
Cela indique à Babel (et à d'autres outils comme Autoprefixer) quels navigateurs doivent être pris en compte lors de la génération du code final.


# Réponse à la Question 5

**Quelle est la différence entre le CSS scoped et non-scoped ?**

### CSS non-scoped (ou global)

Lorsque tu écris du CSS dans une balise `<style>` sans l'attribut `scoped`, les règles CSS que tu définis sont **globales**. Cela signifie qu'elles s'appliquent à l'ensemble de ton application Vue.js, et non pas seulement au composant dans lequel elles sont déclarées.

- **Avantages :** Utile pour les styles généraux de l'application (par exemple, les styles du `body`, les typographies par défaut, les classes utilitaires globales).
- **Inconvénients :** Risque de conflits de noms de classes. Si tu as deux composants différents avec la même classe CSS (par exemple, `.button`), les styles du dernier composant chargé peuvent écraser les styles du premier, ce qui peut causer des comportements inattendus. Cela rend la maintenance plus difficile à mesure que l'application grandit.

### CSS scoped

Lorsque tu ajoutes l'attribut `scoped` à une balise `<style>` (`<style scoped>`), les règles CSS que tu y définis sont **limitées au composant actuel**. Vue.js (grâce à `vue-loader` avec Webpack) modifie les sélecteurs CSS pour qu'ils soient uniques à ce composant. En pratique, Vue ajoute des attributs de données (`data-v-xxxxxx`) uniques à chaque élément du template et aux règles CSS correspondantes.

- **Avantages :**
    - **Isolation des styles :** Les styles d'un composant n'affectent pas les autres composants, ce qui évite les conflits et facilite la réutilisabilité.
    - **Maintenance facile :** Tu sais que les styles que tu modifies dans un composant `scoped` n'impacteront pas le reste de l'application.
    - **Plus sûr :** Moins de risques d'effets de bord imprévus.
- **Inconvénients :** Les styles scoped ne peuvent pas directement affecter les éléments enfants d'un autre composant. Si tu as besoin de styliser un élément enfant provenant d'un slot ou d'un composant externe, tu devras soit utiliser des sélecteurs plus spécifiques (`>>>` ou `/deep/` dans les versions précédentes, ou des sélecteurs combinés dans Vue 3), soit passer des props, ou encore utiliser un style global volontairement pour ces cas spécifiques.

