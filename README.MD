## Compose Flask application

### Use with Docker Development Environments

You can open this sample in the Dev Environments feature of Docker Desktop version 4.12 or later.

### Python/Flask application

Project structure:

```
.
├── .docker
    └── docker-compose.yaml
├── compose.yaml
├── app
    ├── Task
        └── Task.pdf
    ├── templates
    ├── app.py
    ├── Dockerfile
    ├── Legends.json
    ├── requirements.txt
    └── views.py
 ├── compose.yaml
 └── README.md


```

[_compose.yaml_](compose.yaml)

```
services: 
  web: 
    build:
     context: app
     target: builder
    ports: 
      - '8000:8000'
```

## Deploy with docker compose

```
$ docker compose up -d
[+] Building 1.1s (16/16) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                                                                                                       0.0s
    ...                                                                                                                                         0.0s
 => => naming to docker.io/library/flask_web                                                                                                                                                                                               0.0s
[+] Running 2/2
 ⠿ Network flask_default  Created                                                                                                                                                                                                          0.0s
 ⠿ Container web-1  Started
```

## Expected result

Listing containers must show one container running and the port mapping as below:

```
$ docker compose ps
NAME                COMMAND             SERVICE             STATUS              PORTS
flask-web-1         "python3 app.py"    web                 running             0.0.0.0:8000->8000/tcp
```
to see the website got to: 
http://localhost:8000


Stop and remove the containers

```
$ docker compose down
```
