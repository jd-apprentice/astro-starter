---
layout: "../../layouts/BlogPost.astro"
title: "Routing in angular with modules [ES]"
description: "[ES] Rutas en angular"
pubDate: "Feb 10 2022"
heroImage: "/angular.jpg"
alt: "Angular"
---

# Routing en angular con módulos

```jsx
app - routing.module.ts;

import { NgModule } from "@angular/core";
import { RouterModule, Routes } from "@angular/router";

const routes: Routes = [
  {
    path: "",
    loadChildren: () =>
      import("./views/home/home.module").then((m) => m.HomeModule),
    data: {
      title: "Home",
    },
  },
  {
    path: "clientes",
    loadChildren: () =>
      import("./views/clientes/clientes.module").then((m) => m.ClientesModule),
    data: { title: "Clientes", breadcrumb: "Clientes" },
  },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

- En este ejemplo utilizamos los módulos home y clientes que son `views` en angular pantallas apartes de forma mas simple. De esta forma cada una de las sub-rutas dentro de esos módulos siempre va a llevar el path inicial.
- De esta forma armamos algo asi → `/home` o `/clientes/:id`

```jsx
import { NgModule } from "@angular/core";
import { RouterModule, Routes } from "@angular/router";
import { HomeComponent } from "./home.component";

const routes: Routes = [
  {
    path: "",
    component: HomeComponent,
    data: {
      title: "Home",
    },
  },
];

@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [RouterModule],
})
export class HomeRoutingModule {}
```

- Por esta parte podemos ver que la ruta inicial esta vacía ya que es un child, todo lo que se agregue aca va a ser por encima de `/home`
