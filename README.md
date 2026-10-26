<div align="center">

# 🛡️ HardGuard — Inventario y monitoreo de periféricos en tiempo real

**Qué se conecta, qué se desconecta y a qué equipo se movió, al instante**

![Kotlin](https://img.shields.io/badge/Kotlin_2-7F52FF?style=flat-square&logo=kotlin&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_4-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white)
![React](https://img.shields.io/badge/React_18-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

[🌐 Ver portafolio](https://azixtechnologyco-rgb.github.io/#hardguard)

</div>

![Inventario de equipos](capturas/01-inventario.jpg)

## El problema

Un centro de contacto con cientos de puestos perdía mouses, teclados y monitores sin saber cuándo
ni dónde, y el inventario de hardware se hacía a mano.

## La solución

Un **agente liviano** en cada equipo Windows reporta su hardware y cada evento de periféricos a una API
central. El panel muestra todo en tiempo real.

- **Inventario vivo de cada equipo:** monitores, mouse, teclado, Windows, Citrix, CPU, RAM, disco y versión del agente.
- **Eventos al instante** por WebSocket: conexiones y desconexiones en unos 3 segundos.
- **Detección de traslados:** si un periférico sale de un equipo y aparece en otro, queda registrado.
- Grupos por piso o área, con el número de pantallas esperado, y filtros de equipos afectados.
- Operaciones remotas de dominio y control de versiones del agente.
- En producción sobre **755 equipos** y más de **18 000 eventos** registrados.

## Capturas

![Eventos de hardware](capturas/02-dashboard.jpg)

## Arquitectura

```mermaid
flowchart LR
  A[Agente en cada PC Windows] -- REST --> API[API · Kotlin + Spring Boot]
  API <--> DB[(SQL Server)]
  API -- WebSocket STOMP --> UI[Panel · React]
  subgraph Docker Compose
    API
    DB
    UI
  end
```

**Stack:** Kotlin 2 · Spring Boot 4 · Hibernate · SQL Server · WebSocket STOMP · PowerShell · React 18 · Vite · Docker Compose · Nginx

---

> 🔒 El código fuente es privado. Las capturas usan **datos de ejemplo** (empresa ficticia «ACME»):
> ningún equipo, usuario ni dirección real.
>
> Desarrollado por **[Azix Technology](https://azixtechnologyco-rgb.github.io)** · Isaac Ávila
