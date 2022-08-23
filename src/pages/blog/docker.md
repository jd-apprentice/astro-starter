---
layout: "../../layouts/BlogPost.astro"
title: "Dockerize a database + DBeaver [EN]"
description: "[EN] Docker a database and use it with DBeaver in your application"
pubDate: "Aug 21 2022"
heroImage: "/docker.jpg"
alt: "Docker"
---

### How to build and run our containers.

First create a .env file with the following structure (names are like this because i'm using postgres)

```env
POSTGRES_CONTAINER_NAME=
POSTGRES_CONTAINER_IMAGE_NAME=

postgres_USER=
postgres_PASS=
postgres_DB=
postgres_PORT=
```

#### Fill the data in the .env file where the fields are from

- POSTGRES_CONTAINER_NAME // ContainerName
- POSTGRES*CONTAINER_IMAGE_NAME // Image name you can get it from the Docker Hub -> https://hub.docker.com/*/postgres/
- postgres_USER // User usually postgres for working locally
- postgres_PASS // Password usually postgress too
- postgres_DB // For working locally postgres uses to be a standard name too
- postgres_PORT // 5433 Default

#### Create the docker-compose.yml

```yml
version: "3.8"
services:
  postgres:
    container_name: ${POSTGRES_CONTAINER_NAME}
    image: ${POSTGRES_CONTAINER_IMAGE_NAME}
    restart: "no"
    env_file:
      - .env
    environment:
      - POSTGRES_PASSWORD=${postgres_PASS}
      - POSTGRES_USER=${postgres_USER}
      - POSTGRES_DB=${postgres_DB}
    ports:
      - ${postgres_PORT}:5432
    volumes:
      - ./data_postgres:/var/lib/postgresql/data
```

once we have ready our docker-compose.yml we run the following command

```bash
_ docker compose up -d
```

to check if we have our container running we can check it with the following command

```bash
docker ps
```

![image](https://user-images.githubusercontent.com/68082746/185813790-e8cf59c6-2a4f-411e-adb5-0589933a385f.png)

now for connecting to our db in DBeaver we are going to need the ip for the container to do that copy the container id from
there and run the next command

```bash
docker inspect <Container-ID>
```

at the end of the response we get the following structure

```json
"Networks": {
                "vehiclesretail_default": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": [
                        "string",
                        "string",
                        "string"
                    ],
                    "NetworkID": "string",
                    "EndpointID": "string",
                    "Gateway": "string",
                    "IPAddress": "string", // This is the line we need
                    "IPPrefixLen": "number",
                    "IPv6Gateway": "string",
                    "GlobalIPv6Address": "string",
                    "GlobalIPv6PrefixLen": "number",
                    "MacAddress": "string",
                    "DriverOpts": null
                }
            }
```

now we are going to open DBeaver and create a new connection

- Database
- New Database Collection

![image](https://user-images.githubusercontent.com/68082746/185814323-ff37215a-640c-4bae-817c-727ce9743104.png)

populate the fields required and click on test connection

![image](https://user-images.githubusercontent.com/68082746/185814424-30da7f47-1781-460a-adcd-783fc2d245c3.png)

if everything is okay we should see the following image

![image](https://user-images.githubusercontent.com/68082746/185814444-93e8b2c0-6eaa-42fd-8f8a-4f4b6a9b51a3.png)

after that click finish and here we go! we have our DBeaver connected to our docker container.

you can check the gist [HERE](https://gist.github.com/jd-apprentice/5818628a7815975b1e56e00c5e87704a)
