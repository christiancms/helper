### Procurar pelo nome (Ignorando a caixa alta)
```sh
sudo find / -iname <nome>
```
### Editor de texto
nano
### Atualizar o Google Chrome via terminal
 Abra o terminal com segurando CTRL e apertando a tecla T.
 Para começarmos rode o seguinte comando no terminal para atualizar os pacotes e dependências.
```sh
sudo apt update && sudo apt upgrade -y
```
 Agora, atualize o Chrome com o seguinte comando:
```sh
sudo apt install google-chrome-stable
```
Criar um arquivo vazio no terminal
```
touch fileName
```
Listar arquivos ocultos
```
ls -a
```
Exibe o caminho da pasta atual
```
pwd
```
Vai para a pasta do usuário logado
```
cd ~
```
### Instalar novo app .deb
```
 cd ~/Downloads/
 sudo chmod +x discord-0.0.34.deb 
 sudo apt-get install ./discord-0.0.34.deb 
 rm -rf discord-0.0.34.deb 
```
