# Challenge-Docker

# 🔐 Ansible SSH Docker Challenge

Ce projet est un petit **challenge** donné pour un test technique qui vise à déployer Nginx via Ansible, dans un environnement 100% containerisé, en utilisant **WSL2 Debian** comme poste de contrôle.  
Il met en œuvre les technologies suivantes :

- Docker & Docker Compose
- Conteneur SSH (serveur distant simulé)
- Conteneur Ansible (poste de contrôle)
- Connexion SSH entre conteneurs
- Déploiement d’un service Nginx via Ansible

---

## 🧠 Objectif

> Déployer automatiquement un serveur **Nginx** dans un conteneur Docker via **Ansible** exécuté depuis un autre conteneur, en utilisant **SSH comme mode de communication**.

---

## ⚙️ Architecture

├── ansible_controller/
│   └── Dockerfile
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


- Le conteneur `ansible_controller` se connecte au conteneur `ssh_server` via SSH (port 2222).
- Ansible installe et configure Nginx à l’intérieur du conteneur `ssh_server`.


 ->Technologies utilisées :

-Docker
-Docker Compose
-Ansible
-OpenSSH
-Debian 12
-WSL2


Conclusion :

Malheureusement, je n'ai pas réussi à deployer correctement Nginx via ansible, lorsque je me connecte à mon conteneur, et que je souhaite **RUN** mon playbook dans le conteneur **Ansible**, je me connecte avec mon SSH password.
fatal: [172.17.0.1]: UNREACHABLE! => {
  "changed": false,
  "msg": "Failed to connect to the host via ssh: ssh: connect to host 172.17.0.1 port 2222: Connection timed out",
  "unreachable": true
}
J’ai tenté de changer l’IP vers localhost ou mon adresse locale sans succès.
