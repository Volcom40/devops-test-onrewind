A savoir :

Installer les paquets pour docker et docker-compose :

  - sudo yum update -y

  - sudo yum install -y docker

  - sudo service docker start

  - sudo usermod -a -G docker ec2-user

  - curl -L https://github.com/docker/compose/releases/download/1.20.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
  
  - chmod +x /usr/local/bin/docker-compose


Pour adapter la configuration à votre infrastructure, il faudra remplacer les valeures suivantes dans le docker-compose.yml :
  
  -Dans le container traefik: "traefik.frontend.rule=Host:domain.com" Remplacer "domain.com" par le votre.

  -Dans le container whoami: "traefik.frontend.rule=Host:first.container.domain.com" Remplacer "domain.com" par le votre
       
  -Dans le container whoami2: "traefik.frontend.rule=Host:second.container.domain.com" Remplacer "domain.com" par le votre


Ensuite, dans le répertoire "conf", ouvrez le fichier traefik.toml et remplacez les valeures suivantes :

  - Remplacez domain.com par le votre
   [docker]
   domain = "domain.com"

  - Remplacez l'adresse mail par la votre
   [acme]
   email = "monadresse@domain.com"

Pour lancer les containers, effectuez la commande suivante : docker-compose up -d
