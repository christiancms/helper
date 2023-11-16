sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl stop docker
Add user to docker group
sudo usermod -aG docker <username>
systemctl --user start docker-desktop
sudo apt-get install docker-ce docker-ce-cli containerd.io
