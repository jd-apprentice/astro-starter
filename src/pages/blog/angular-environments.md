---
layout: "../../layouts/BlogPost.astro"
title: "Services and environments in Angular [ES]"
description: "[ES] Servicios y entornos en angular"
pubDate: "Mar 2 2022"
heroImage: "/angular.jpg"
alt: "Angular"
---

- Primero que todo nos dirigimos a la ruta donde se encuentra este archivo el cual es el que vamos a usar para nuestro entorno de desarollo.

$$
|-->src/environments
  --> environments.ts
$$

<aside>
💡 Los comentarios de angular en este archivo son importantes ya que menciona como trabaja el archivo environments.ts

</aside>

```jsx
// This file can be replaced during build by using the `fileReplacements` array.
// `ng build` replaces `environment.ts` with `environment.prod.ts`.
// The list of file replacements can be found in `angular.json`.

export const environment = {
  production: false,
  baseURL: "TU LOCALHOST",
};
```

- Para el archivo de producción nos dirigimos a la siguiente ruta.

$$
|-->src/environments
  --> environments.prod.ts
$$

```jsx
export const environment = {
  production: true,
  baseURL: "TU URL DE PROD", // Ejemplo la de heroku
};
```

- Después en nuestro servicio vamos a llamar a environment para despues acceder a nuestra url para nuestro entorno local y cuando subamos nuestro proyecto por ejemplo a firebase u vercel se va a utilizar el archivo de prod.

```tsx
export class EmployeesService {
  baseUrl: string = environment.baseURL + "employees"; // Esto va a leer la URL base que definiste en tu archivo environment

  constructor(private http: HttpClient) {}

  getAllEmployees(): Observable<Employee[]> {
    return this.http.get<Employee[]>(this.baseUrl);
  }

  updateEmployee(): Observable<Employee> {
    return this.http.put<Employee>(this.baseUrl, "/:id");
  }

  deleteEmployee(): Observable<Employee> {
    return this.http.delete<Employee>(this.baseUrl, "/:id");
  }
}
```
