```sh
sudo systemctl start docker
```
```sh
sudo systemctl enable docker
```
```sh
sudo systemctl stop docker
```
Add user to docker group
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
