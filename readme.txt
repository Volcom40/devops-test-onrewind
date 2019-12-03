A savoir :

Installer les paquets pour docker et docker-compose :

  - sudo yum update -y

  - sudo yum install -y docker

  - sudo service docker start

  - sudo usermod -a -G docker ec2-user

  - curl -L https://github.com/docker/compose/releases/download/1.20.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
  
  - chmod +x /usr/local/bin/docker-compose


Pour adapter la configuration à votre infrastructure, il faudra remplacer les valeures suivantes dans le docker-compose.yml :
  
  Dans le service traefik: 
    - - --certificatesresolvers.leresolver.acme.email=adresse@domaine.com Remplacez l'adresse par la votre.
    - - "traefik.http.routers.traefik.rule=Host(`domaine.fr`)" Remplacez domaine.fr par le votre

  Dans le service whoami:
    - - "traefik.http.routers.whoami1.rule=Host(`first.container.domaine.fr`)" Remplacez domaine.fr par le votre
       
  Dans le service whoami2:
    - - "traefik.http.routers.whoami2.rule=Host(`second.container.crytom.fr`)" Remplacez domaine.fr par le votre


Pour lancer les services, effectuez la commande suivante : docker-compose up -d
