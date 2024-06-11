# Docker registry - port 5000

% docker, 5000

## Repo listable sans authentification

```
curl http://<ip>:5000/v2/_catalog
```

## Lister les images et les télécharger si le tag 'latest' existe

```
for i in $(curl http://<ip>:5000/v2/_catalog | jq -rc '.repositories[]'); do sudo docker pull <ip>:5000/$i; done
```

## Permettre de récupérer via Docker registry en HTTP

```
sudo systemctl stop docker;sudo nohup dockerd --insecure-registry 54.38.46.205:5000 &
```

## Push une image

```
sudo docker tag <local_image>:latest <ip>:5000/<image_name>;
sudo docker push <ip>:5000/<image_name>
```