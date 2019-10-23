

```
sudo docker ps
sudo docker images
```

```
sudo docker commit [container id] [your user name]/[your repo name]:[your tag name]
```

```
sudo docker login docker.io
sudo docker push [your user name]/[your repo name]:[your tag name]
```

```
sudo docker run -it [your user name]/[your repo name]:[your tag name]
```

If you want to start a new fresh container locally, e.g. with ubuntu18.04:

```
sudo docker run -it ubuntu:18.04
```