Instalando Docker e Docker-Compose Ubuntu

### Passo 1: Instalando o Docker
Antes de instalar o Docker, você precisa atualizar o índice do pacote do seu sistema. Abra o terminal e execute o seguinte comando:
```
sudo apt-get update
```
Em seguida, execute o seguinte comando para instalar o Docker:
```
sudo apt-get install docker.io
```
Após a instalação, inicie o serviço do Docker executando o seguinte comando:
```
sudo systemctl start docker
```
Verifique se o Docker está funcionando corretamente executando o seguinte comando:
```
sudo docker run hello-world
```
Se tudo estiver funcionando corretamente, você verá uma saída como a seguinte:

> Hello from Docker!<br/>
> This message shows that your installation appears to be working correctly.

### Passo 2: Instalando o Docker Compose
Para instalar o Docker Compose, você precisa fazer o download do arquivo binário. Execute o seguinte comando para fazer o download:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
Em seguida, conceda permissões de execução ao arquivo binário do Docker Compose executando o seguinte comando:
```
sudo chmod +x /usr/local/bin/docker-compose
```
Verifique se o Docker Compose está funcionando corretamente executando o seguinte comando:
```
docker-compose --version
```
Se tudo estiver funcionando corretamente, você verá uma saída como a seguinte:

> docker-compose version 1.26.2, build eefe0d31

### Passo 3: Concedendo Permissões para Usuários Não-Root
Por padrão, o Docker requer permissões de root para executar. No entanto, é possível conceder permissões a usuários não-root, o que é uma boa prática de segurança. Para fazer isso, crie um grupo Docker executando o seguinte comando:
```
sudo groupadd docker
```
Em seguida, adicione seu usuário ao grupo Docker executando o seguinte comando (substitua “user” pelo nome de usuário do seu sistema):
```
sudo usermod -aG docker $USER
```
Reinicie o seu sistema para aplicar as alterações executando o seguinte comando:
```
sudo reboot
```
Após a reinicialização, você deve ser capaz de executar comandos Docker sem precisar de permissões de root. Verifique se tudo está funcionando corretamente executando o seguinte comando:
```
docker run hello-world
```
Se tudo estiver funcionando corretamente, você verá uma saída semelhante à seguinte:

> Hello from Docker!<br/>
> This message shows that your installation appears to be working correctly.
