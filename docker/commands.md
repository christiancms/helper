Starting
```
sudo systemctl start docker
sudo systemctl enable docker
```
Docker status
```
sudo systemctl status docker
```
Information
```
docker info
```
> Error response from daemon: conflict: Unable to delete da89557439d9 (cannot be forced) - image is being used by running container ad98775439d9
```
docker ps -a
```
Get container ID and
```
docker stop da89557439d9
```
Delete/Remove existing container
```
docker rm da89557439d9
```
