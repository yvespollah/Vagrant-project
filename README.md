# Vagrant-project

## RAPPORT SUR VAGRANT

### Nom: Pollah Yves
### Matricule: 21T2516

## INTRODUCTION

Vagrant est un outil open-source permettant la création et la gestion d'environnements de développement virtuels. Il offre un moyen simple et reproductible de configurer des machines virtuelles pour différents projets, ce qui facilite le travail des développeurs en assurant la cohérence des environnements de développement.

                                                
## UTILISATION DE VAGRANT

Pour utiliser Vagrant, il suffit d'installer le logiciel sur la machine hôte, puis de configurer un fichier de configuration appelé Vagrantfile. Ce fichier définit les paramètres de la machine virtuelle, tels que le système d'exploitation, la mémoire et les réglages du réseau. Une fois le Vagrantfile configuré, il est possible de lancer la machine virtuelle avec une simple commande `vagrant up`.

## AVANTAGES DE VAGRANT

- L'un des principaux avantages de Vagrant est sa portabilité. Les Vagrantfiles peuvent être partagés entre les membres d'une équipe, garantissant ainsi que tous les développeurs travaillent dans le même environnement.
  
- De plus, Vagrant prend en charge de nombreux fournisseurs de machines virtuelles, y compris VirtualBox, VMware et AWS, offrant ainsi une flexibilité dans le choix de l'infrastructure sous-jacente.

## INCONVÉNIENTS DE VAGRANT

Bien que Vagrant soit un outil puissant, il présente quelques inconvénients:

- Tout d'abord, le temps nécessaire pour lancer une machine virtuelle peut être assez long, en particulier lorsqu'elle doit être provisionnée avec des logiciels supplémentaires.
  
- De plus, la configuration initiale d'un Vagrantfile peut être complexe, en particulier pour les utilisateurs débutants.

## DEMO SUR UN CAS PRATIQUE

### Énoncé
Créer des environnements virtuels Ubuntu sur VirtualBox en utilisant Vagrant et les configurer de telle sorte que Docker s'installe automatiquement.

### Étape 1 : Préparation de l'environnement

- Installation de Vagrant:
  - Lien: [Install | Vagrant | HashiCorp Developer](https://www.vagrantup.com/downloads)
  - Suivez les instructions d'installation pour votre système d'exploitation.

- Installation de VirtualBox:
  - Téléchargez le package d'installation correspondant à votre système d'exploitation depuis le site officiel de VirtualBox : [Downloads – Oracle VM VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  - Suivez les instructions d'installation fournies pour votre système d'exploitation.

### Étape 2 : Initialiser un nouveau projet Vagrant

Ouvrez votre terminal et créez un nouveau répertoire pour votre projet. Ensuite, initialisez un nouveau projet Vagrant en utilisant la commande suivante : ### vagrant init

### Étape 3 : Configurer le fichier Vagrantfile

Ouvrez le fichier Vagrantfile généré dans votre éditeur de texte préféré. Modifiez ce fichier pour ajouter la configuration permettant l'installation de Docker automatiquement au démarrage de la machine virtuelle.

#### Explication du contenu du Vagrantfile

1. Vagrant.configure("2") do |config| :
   - Cette ligne indique le début de la configuration Vagrant. Elle définit la version de la configuration Vagrant à utiliser (dans ce cas, "2") et ouvre un bloc de code pour définir les paramètres de configuration.
2. config.vm.define "ubuntu2" do |ubuntu2| :
   - Cette ligne définit une machine virtuelle nommée "ubuntu2". Cela permet de référencer cette machine virtuelle dans le reste de la configuration. Le bloc de code après "do" permet de définir les paramètres spécifiques à cette machine virtuelle.
3. ubuntu2.vm.box = "ubuntu/bionic64" :
   - Cette ligne spécifie la box (l'image de la machine virtuelle) à utiliser pour la machine virtuelle "ubuntu2". Dans ce cas, il s'agit de "ubuntu/bionic64", qui est une image Ubuntu 18.04 (bionic64) disponible publiquement.
4. ubuntu2.vm.provider "virtualbox" do |vb| :
   - Cette ligne configure le fournisseur de la machine virtuelle, dans ce cas VirtualBox. Le bloc de code après "do" permet de définir des paramètres spécifiques à VirtualBox.
5. vb.memory = "1024" :
   - Cette ligne définit la quantité de mémoire RAM allouée à la machine virtuelle, en mégaoctets. Dans cet exemple, la machine virtuelle aura 1024 Mo de RAM (soit 1 Go).
6. vb.cpus = 1 :
   - Cette ligne définit le nombre de cœurs CPU alloués à la machine virtuelle. Dans cet exemple, la machine virtuelle aura 1 cœur CPU.
7. ubuntu2.vm.provision "shell", path: "script.sh" :
   - Cette ligne spécifie la provision à appliquer à la machine virtuelle. Dans ce cas, il s'agit d'une provision de type "shell", qui exécute un script shell lors du démarrage de la machine virtuelle. Le chemin du script shell est spécifié avec l'option path, ici "script.sh"

### Explication du contenu du Script.sh

1. sudo apt-get install -y docker.io :
   - Cette commande installe Docker sur le système Ubuntu. -y est un commutateur qui répond automatiquement "oui" à toutes les questions posées par le gestionnaire de paquets apt, garantissant ainsi que l'installation se déroule sans interruption et sans nécessiter d'interaction utilisateur.
2. sudo usermod -aG docker vagrant :
   - Cette commande ajoute l'utilisateur "vagrant" au groupe "docker". Cela donne à l'utilisateur vagrant les permissions nécessaires pour exécuter des commandes Docker sans avoir à utiliser sudo à chaque fois.
3. sudo systemctl start docker :
   - Cette commande démarre le service Docker sur le système Ubuntu. Une fois le service démarré, Docker est prêt à être utilisé pour exécuter des conteneurs.
4. sudo systemctl enable docker :
   - Cette commande configure le service Docker pour qu'il démarre automatiquement au démarrage du système. Cela garantit que Docker sera toujours disponible même après un redémarrage du système.

### Démarrer la machine virtuelle

Dans votre terminal, naviguez vers le répertoire de votre projet Vagrant et démarrez la machine virtuelle en utilisant la commande : ### vagrant up

### Accès à la machine virtuelle

Une fois la machine virtuelle démarrée, vous pouvez vous y connecter en utilisant la commande : ### vagrant ssh

### Vérifier l'installation de Docker

À l'intérieur de la machine virtuelle, vérifiez que Docker a été installé avec succès en exécutant la commande : ### docker --version

## MERCI
