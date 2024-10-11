# TP1 - Maîtrise de Git
 ![Git Logo](https://avatars.githubusercontent.com/u/18133?s=200&v=4)

• Se familiariser avec Git, un système de gestion de version décentralisé largement utilisé.

• Apprendre à gérer des projets, collaborer avec d'autres développeurs et utiliser les fonctionnalités avancées de Git.

## Commands
    ssh-keygen -t rsa -b 4096 -C sbikamohamed241@gmail.com

La commande génère une paire de clés SSH RSA de 4096 bits, avec l'email sbikamohamed241@gmail.com comme commentaire pour identifier la clé.

    cat ~/.ssh/id_rsa.pub

La commande cat ~/.ssh/id_rsa.pub affiche le contenu de la clé publique SSH située dans le fichier id_rsa.pub. Cette clé publique peut être partagée avec des serveurs ou des services (comme GitHub, GitLab) pour permettre l'authentification par clé SSH sans avoir à utiliser de mot de passe.

    git config --global user.name "MohamedSbika"
    git config --global user.email sbikamohamed241@gmail.com

git config --global user.name "MohamedSbika" : Définit ton nom d'utilisateur Git globalement comme étant "MohamedSbika". Ce nom sera associé à tous les commits que tu fais.

git config --global user.email sbikamohamed241@gmail.com : Associe ton adresse email "sbikamohamed241@gmail.com" à tous tes commits. Cela permet d'identifier qui a effectué un commit particulier, et cette adresse est souvent utilisée pour la synchronisation avec des services comme GitHub.

    ssh -T git@github.com

ssh -T : Le drapeau -T désactive l'allocation d'un pseudo-terminal, car tu n'as pas besoin d'ouvrir une session interactive, juste de tester la connexion.

git@github.com : Indique que tu te connectes à GitHub en utilisant le protocole SSH, via l'utilisateur git.

    git config --global user.name
    git config --global user.email

affichent la configuration actuelle de ton nom d'utilisateur et de ton email globalement dans Git.

    git clone https://github.com/MohamedSbika/TP1_GIT

clonage du repo sur notre machine 

    cd TP1_GIT

acceder au repertoire de projet 

    touch README.md
Créer un nouveau fichier vide appelé README.md dans le répertoire actuel.

    git add README.md
ajouter le fichier au index

    git commit -m "Ajout du fichier README.md"

Crée un commit avec un message "Ajout du fichier README.md" pour enregistrer le fichier dans l'historique du dépôt. Ce commit devient une nouvelle version sauvegardée dans Git.

    git remote add origin https://github.com/MohamedSbika/TP1_GIT.git
lier mon depot local avec mon depot github 

    touch index.html
    echo "Contenu de votre fichier" > index.html
    git add index.html
    git commit -m "Premier commit : ajout index.html"

Créer un fichier sous le nom index.html , ajouter un contenu quelconque à ce fichier , ajouter le fichier au index et ensuite Créer un commit pour notre travail 

    git log

Cela nous  permet de suivre l'évolution des modifications apportées à notre  projet, et de voir les commits précédents et leurs détails.

    git diff 35dc7e6bc4d061d9e24921dcec88ab9965ab8f4d bd04a55d7676aabbb52f0ee3287aa7f944b2225f

affiche les différences (diff) entre le commit actuel dans ton dépôt local et le commit spécifié par le hash 35dc7e6bc4d061d9e24921dcec88ab9965ab8f4d. En d'autres termes, elle te montre toutes les modifications qui ont été faites dans les fichiers depuis ce commit.

    git branch ma-fonctionnalite
    git checkout ma-fonctionnalite

nous venons de créer une nouvelle branche nommée ma-fonctionnalite et nous y sommes maintenant basculé. nous pouvons maintenant y travailler indépendamment de la branche principale.

    git add .
    git commit -m "Modification de ma-fonctionnalite"
    git push origin ma-fonctionnalite

ajouter tous les modifications au index puis les enregistrer avec la creation d'un commit et finalement on va l'envoyer (push) vers le depot github 

    git commit -am "modif dans ma-fonctionalite"
    git checkout master
    git commit -am "modif dans master"
    git merge ma-fonctionnalite
    git add .
    git commit -m "resolu du conf"

Nous avons travaillé sur deux branches, ma-fonctionnalite et master. Après avoir apporté des modifications et fait des commits sur chacune, nous avons fusionné la branche ma-fonctionnalite dans master à l’aide de la commande git merge. Un conflit est apparu lors de cette fusion, que nous avons résolu manuellement. Ensuite, nous avons ajouté les fichiers corrigés et validé le tout avec un commit intitulé "resolu du conf". Ainsi, la branche master intègre maintenant les modifications de ma-fonctionnalite ainsi que la résolution du conflit.


    git fetch origin
    git branch -a
    git checkout -b ma-fonctinnalite/f1
    git checkout master
    git branch -a


Nous avons récupéré les dernières mises à jour du dépôt distant avec git fetch origin, puis listé toutes les branches locales et distantes avec git branch -a. Ensuite, nous avons créé et basculé sur une nouvelle branche appelée ma-fonctinnalite/f1 avec git checkout -b, avant de revenir sur la branche master. Enfin, nous avons vérifié à nouveau les branches disponibles pour s'assurer que tout était en place.

    git checkout master
    git pull origin master 
    git checkout ma-fonctionnalite

    git rebase master
    git checkout master
    git merge ma-fonctionnalite
    git push origin master
    git rebase --abort
    git log --oneline master..HEAD

Nous avons d'abord vérifié que nous étions sur la branche master et que celle-ci était à jour avec origin/master. Ensuite, nous avons effectué un git pull pour synchroniser les dernières modifications, mais il n'y avait aucune nouvelle mise à jour. Après cela, nous avons basculé sur la branche ma-fonctionnalite, où nous avons vérifié que cette branche suivait correctement origin/ma-fonctionnalite et qu'elle était à jour avec la branche master via un git rebase. Enfin, nous sommes revenus sur master, avons tenté de fusionner ma-fonctionnalite, mais il n'y avait rien à fusionner car tout était déjà à jour.

    git flow init
    git flow feature start ma-fonctionnalite
    git flow release start ma-version
    git add .
    git commit -m "ajout 1"
    git flow feature finish ma-fonctionnalite

Nous avons commencé par initialiser Git Flow avec la commande git flow init, puis avons créé une nouvelle fonctionnalité (feature) nommée ma-fonctionnalite avec git flow feature start ma-fonctionnalite. Ensuite, nous avons lancé une nouvelle version (release) avec git flow release start ma-version. Après avoir ajouté des modifications et les avoir validées avec un commit intitulé "ajout 1", nous avons terminé la fonctionnalité avec git flow feature finish ma-fonctionnalite. Cela clôture la branche de fonctionnalité et la fusionne automatiquement dans la branche develop.

    git push origin --tags
    git flow hotfix start mon-correctif
    git flow hotfix finish mon-correctif
    git push origin --tags
    git branch
    git checkout master
    git branch -d ma-fonctionnalite


Nous avons commencé par pousser toutes les balises locales sur le dépôt distant avec la commande git push origin --tags. Ensuite, nous avons créé une branche de correction urgente (hotfix) nommée mon-correctif avec git flow hotfix start mon-correctif. Une fois les modifications apportées, nous avons terminé la correction avec git flow hotfix finish mon-correctif, ce qui fusionne la correction dans les branches master et develop, puis crée une balise pour cette version. Après avoir poussé les balises à nouveau sur le dépôt distant, nous avons vérifié les branches locales et supprimé la branche ma-fonctionnalite avec git branch -d ma-fonctionnalite après nous être assurés d'être sur la branche master.

Cela permet de finaliser le cycle de développement et d'intégrer la correction dans le projet.
    






## Acknowledgements

 - Nous devons avoir le Git bash (sur windows)
 ou bien 
  - installer git et gitflow pour linux 
    
    sudo apt install git 

    sudo apt install git flow 
