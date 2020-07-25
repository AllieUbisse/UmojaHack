# Umoja_Hack

## How to run
```
# 1 - build the images
# !This might take some minutes, since some low level packages have to be installed
docker-compose build jupyter

# 2 - launch the stack
docker-compose up -d
```

## Service - Port Mappings
| Service | Port |
| --- | --- |
| Jupyter | 8888 |
| Portainer | 9090 |
| MLflow | 5000 |
