---
layout: "../../layouts/BlogPost.astro"
title: "Entities notes from Platzi [ES]"
description: "[ES] Entities"
pubDate: "Aug 23 2022"
heroImage: "/platzi.jpg"
alt: "entities"
---

Clase 03 - [PLATZI](https://platzi.com/clases/1566-bd/20197-entidades-y-atributos/)

#### ¿Qué es una entidad?

Una entidad es algo similar a un objeto (programación orientada a objetos) y representa algo en el mundo real, incluso algo abstracto. Tienen atributos que son las cosas que los hacen ser una entidad y por convención se ponen en plural.

#### Ejemplo de entidad en bases de datos

En la imagen puedes observar como ejemplo que la enidad Laptops posee diferentes atributos como colo, pantalla, año, modelo, etc.

![image](https://static.platzi.com/media/user_upload/ENTIDAD%20LAPTOPS-4910405e-b261-44c6-9193-a68d85a92541.jpg)

#### ¿Qué es un atributo?

Son las características o propiedades que describen a la entidad (se encierra en un óvalo). Los atributos se componen de:

Los atributos compuestos son aquellos que tienen atributos ellos mismos.

Los atributos llave son aquellos que identifican a la entidad y no pueden ser repetidos. Existen:

- Naturales: son inherentes al objeto como el número de serie
- Clave artificial: no es inherente al objeto y se asigna de manera arbitraria.

#### Tipos de entidades

- Entidades fuertes: son entidades que pueden sobrevivir por sí solas.

- Entidades débiles: no pueden existir sin una entidad fuerte y se representan con un cuadrado con doble línea.

- Identidades débiles por identidad: no se diferencian entre sí más que por la clave de su identidad fuerte.

- Identidades débiles por existencia: se les asigna una clave propia.

#### Cómo representar las entidades en bases de datos

Existen varios tipos de notaciones para los modelos entidad relacionamiento. Chen es uno de los más utilizados para diagramar lógicamente la base de datos. Aquí te mostramos un ejemplo.

![image](https://static.platzi.com/media/user_upload/ejemplo-notacion-chen-entidades-98a3fc2d-c6c0-4012-9e0e-c51edc2acc40.jpg)

Contribución creada con los aportes de: Roberto Castro y DaRk452.
