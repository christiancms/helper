### Status
```sh
sudo systemctl status docker
```
### Inicie o Docker manualmente
```sh
sudo systemctl start docker
```
### Habilitar
```sh
sudo systemctl enable docker
```
### Parar o Docker manualmente 
```sh
sudo systemctl stop docker
```

### Add user to docker group
```sh
sudo usermod -aG docker <username>
```
```sh
systemctl --user start docker-desktop
```
```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

### Desabilitar
```sh
sudo systemctl disable docker
```
### Remover da inicialização
```sh
sudo rm /etc/systemd/system/multi-user.target.wants/docker.service
```
or
```sh
sudo rm /var/lib/systemd/deb-systemd-helper-enabled/multi-user.target.wants/docker.service
```
