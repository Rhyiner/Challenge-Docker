# Challenge-Docker

# 🔐 Ansible SSH Docker Challenge

Ce projet est un petit **challenge** donné pour un test technique qui vise à déployer Nginx via Ansible, dans un environnement 100% containerisé, en utilisant **WSL2 Debian** comme poste de contrôle.  
Il met en œuvre les technologies suivantes :

- Docker & Docker Compose
- Conteneur SSH (serveur distant simulé)
- Conteneur Ansible (poste de contrôle)
- Connexion SSH entre conteneurs
- Déploiement d’un service Nginx via Ansible
- Exposition HTTP (port 8080) mais aussi du sFTP (port 2222)

---

## 🧠 Objectif

> Déployer automatiquement un serveur **Nginx** dans un conteneur Docker via **Ansible** exécuté depuis un autre conteneur, en utilisant **SSH comme mode de communication**.

---

## ⚙️ Architecture

├── ansible_controller/
│   ├── Dockerfile
│
│
├── ssh_server/
│   └── Dockerfile
│
└── playbooks/
    └── nginx/
        ├── site.yml
        └── roles/
            └── nginx/
                └── tasks/
                    └── main.yml


- Le conteneur `ansible_controller` se connecte au conteneur `ssh_server` via SSH.
- Ansible installe et configure Nginx dans `ssh_server`.
- Le port 8080 de l’hôte redirige vers le port 80 de `ssh_server` pour accéder à Nginx.

 ->Technologies utilisées :

-Docker
-Docker Compose
-Ansible
-OpenSSH
-Debian 12
-WSL2


Conclusion :

Malheureusement, je n'ai pas réussi à deployer correctement Nginx via ansible, lorsque je me connecte à mon conteneur, et que je souhaite **RUN** mon playbook dans le conteneur **Ansible**, je me connecte avec mon SSH password.
fatal: ***: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host ***: Connection timed out", "unreachable": true}
J'ai essayé de changer le chemin localhost avec mon adresse local, pas de réussite.
