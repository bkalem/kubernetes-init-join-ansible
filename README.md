# Deployer un cluster Kubernetes depuis Ansible
## inventory + SSH-Key
pour générez la paire de clé SSH pour l'authentification sans password <br/>
```ssh-keygen -q -f ~/.ssh/id_rsa -N ''``` <br/>
vous pouvez accepter les clés publics de chaque node <br/>
```ssh-keyscan master worker1 worker2 worker3 >> ~/.ssh/known_hosts``` <br/>
enfin vous pouvez envoyer la clé public vers chaque node <br/>
```ansible-playbook 01-copy-ssh-key/ssh-addkey.yml --ask-pass```
## installation docker
```ansible-playbook 02-install-docker-ce/install-docker-ce-centos-7.yml```
## installation kubernetes
```ansible-playbook 03-install-kubernetes/install-kubernetes-centos-7.yml```
## iniatiation du master Kubernetes
```ansible-playbook 04-init-kube-cluster/01-init-kube-master.yml```
## jonction des workers Kubernetes
```ansible-playbook 05-join-worker-kube/01-join-worker-kubernetes.yml```