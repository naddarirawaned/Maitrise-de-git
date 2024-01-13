# tp1devops
TP1 - Maîtrise de Git
Objectifs:
Se familiariser avec Git, un système de gestion de version décentralisé largement utilisé.
Apprendre à gérer des projets, collaborer avec d'autres développeurs et utiliser les fonctionnalités avancées de Git.
Partie 1: Préparation de l'environnement Git
1)Création de clé SSH
a. Utilisez la commande suivante pour générer votre clé SSH:

ssh-keygen -t rsa -b 4096 -C votreadresse@email.com
b. Copiez votre clé publique SSH en utilisant la commande suivante:


cat ~/.ssh/id_rsa.pub
c. Connectez-vous à votre compte sur le dépôt distant (par exemple, GitHub) et ajoutez votre clé publique SSH dans les paramètres de votre compte.

Configuration de Git

Configurez votre nom et votre adresse e-mail pour que vos commits soient correctement identifiés:

git config --global user.name "Votre Nom"
git config --global user.email votre@email.com
Connexion SSH aux dépôts distants

Pour tester votre connexion SSH, exécutez la commande suivante. Assurez-vous de remplacer git@github.com par l'adresse du serveur distant où vous hébergerez vos dépôts:

ssh -T git@github.com
ou
ssh -T git@gitlab.com
Partie 2: Création d'un nouveau projet
Connectez-vous à votre compte GitHub (ou GitLab).

Clonez le projet en utilisant l'URL SSH que vous avez notée à la partie 1. Par exemple, si votre URL est git@github.com:votre-nom-utilisateur/mon-projet.git, exécutez la commande suivante:


git clone git@github.com:votre-nom-utilisateur/mon-projet.git
Vous devriez maintenant avoir cloné avec succès votre projet sur votre machine locale. Accédez-y avec:


cd mon-projet
Partie 3: Concepts de base de Git
Travailler avec les fichiers

Créez un fichier appelé index.html dans votre répertoire de projet et ajoutez-y du contenu:

touch index.html
echo "Contenu de votre fichier" > index.html
Utilisez les commandes suivantes pour ajouter le fichier à l'index (staging) et valider votre premier commit:

git add index.html
git commit -m "Premier commit : ajout de index.html"
Historique des commits

Visualisez l'historique des commits de votre projet avec la commande suivante:


git log
Pour afficher les différences entre deux commits, utilisez la commande suivante:

git diff commit_id_1 commit_id_2
Partie 4: Collaborer sur Git
Créez une nouvelle branche pour travailler sur une fonctionnalité spécifique de votre projet:


git branch ma-fonctionnalite
git checkout ma-fonctionnalite
Effectuez des modifications dans votre dépôt local, ajoutez-les à l'index, faites un commit, puis poussez les modifications vers le dépôt distant:


git add .
git commit -m "Modification de ma-fonctionnalite"
git push origin ma-fonctionnalite
Gestion des conflits

Simulez un conflit en modifiant la même ligne dans deux branches différentes, puis fusionnez les branches et résolvez le conflit:

git checkout ma-fonctionnalite
git commit -am "Modification dans ma-fonctionnalite"
git checkout master
git commit -am "Modification dans master"
git merge ma-fonctionnalite
git add .
git commit -m "Résolution du conflit"
Partie 5: Utilisation de Git Flow
Initialisation de Git Flow:


git flow init
Création d'une nouvelle fonctionnalité:


git flow feature start ma-fonctionnalite
Création d'une nouvelle version:


git flow release start ma-version
Lorsque vous avez terminé, fusionnez la branche de fonctionnalité dans la branche de développement en utilisant GitFlow:


git flow feature finish nouvelle-fonctionnalite
Création d'un correctif:


git flow hotfix start mon-correctif
