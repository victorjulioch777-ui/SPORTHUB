# 🏆 SportHub

**SportHub** es una plataforma de gestión deportiva diseñada como un proyecto de aprendizaje **Full Stack**. Su objetivo es integrar tecnologías de frontend, backend, bases de datos, desarrollo móvil, control de versiones y Linux dentro de un mismo sistema realista y escalable.

El proyecto permitirá administrar usuarios, equipos, instalaciones deportivas, reservas, torneos, partidos, resultados, estadísticas y notificaciones desde diferentes clientes: una aplicación web para usuarios, un panel administrativo y una aplicación móvil.

> 🚧 **Estado del proyecto:** En desarrollo / etapa de aprendizaje.

---

## 📌 Objetivos del proyecto

SportHub tiene dos objetivos principales:

1. Construir una plataforma deportiva funcional.
2. Utilizar el desarrollo del sistema como ruta práctica para aprender tecnologías modernas de desarrollo de software.

Durante el desarrollo se practicarán conceptos como:

- Programación orientada a objetos.
- APIs REST.
- Arquitectura por capas.
- Bases de datos relacionales.
- Autenticación y autorización.
- Desarrollo frontend moderno.
- Desarrollo móvil.
- Microservicios.
- Git y GitHub.
- Linux y terminal.
- Pruebas de software.
- Buenas prácticas de desarrollo.

---

## 🧠 Tecnologías que se utilizarán

| Área | Tecnología | Uso |
|---|---|---|
| Backend principal | Java | Lógica principal del sistema |
| Framework backend | Spring Boot | Construcción de la API REST |
| Backend secundario | Node.js | Runtime JavaScript del servicio auxiliar |
| Microservicio | Express | Notificaciones y funcionalidades en tiempo real |
| Base de datos | PostgreSQL / SQL | Persistencia de datos |
| Frontend principal | React | Aplicación web para usuarios |
| Administración | Angular | Panel administrativo |
| Aplicación móvil | React Native | App para Android/iOS |
| Lenguaje frontend | JavaScript | Fundamentos web y Node.js |
| Lenguaje frontend | TypeScript | React, Angular, React Native y Express |
| Web | HTML | Estructura de interfaces |
| Web | CSS | Diseño y estilos |
| Sistema | Linux | Entorno de desarrollo y futuro despliegue |
| Scripting | Bash | Automatización y terminal |
| Versiones Node | NVM | Gestión de versiones de Node.js |
| Control de versiones | Git | Historial y flujo de trabajo |
| Repositorio remoto | GitHub | Colaboración y seguimiento del proyecto |

---

# 🏗️ Arquitectura general

La arquitectura propuesta separa las responsabilidades entre frontend, backend, móvil y servicios auxiliares.

```text
                         ┌─────────────────────┐
                         │     PostgreSQL      │
                         │        SQL          │
                         └──────────┬──────────┘
                                    │
                         ┌──────────▼──────────┐
                         │ Java + Spring Boot  │
                         │    API principal    │
                         │                     │
                         │ • Usuarios          │
                         │ • Equipos           │
                         │ • Reservas          │
                         │ • Torneos           │
                         │ • Partidos          │
                         │ • Estadísticas      │
                         └──────────┬──────────┘
                                    │
                               REST API
                                    │
             ┌──────────────────────┼──────────────────────┐
             │                      │                      │
      ┌──────▼──────┐       ┌──────▼──────┐       ┌──────▼───────┐
      │    React    │       │   Angular   │       │ React Native │
      │  Web user   │       │ Admin panel │       │ Mobile app   │
      └─────────────┘       └─────────────┘       └──────────────┘

                         ┌─────────────────────┐
                         │  Node.js + Express  │
                         │ Servicio auxiliar   │
                         │                     │
                         │ • Notificaciones    │
                         │ • WebSockets        │
                         │ • Eventos           │
                         └─────────────────────┘
```

---

# 🎯 Funcionalidades principales

## 👤 Usuarios

El sistema permitirá:

- Registro de usuarios.
- Inicio y cierre de sesión.
- Gestión del perfil.
- Cambio de contraseña.
- Roles y permisos.
- Consulta de actividad deportiva.

Roles iniciales:

- **USER** — usuario normal.
- **ADMIN** — administrador de la plataforma.
- **ORGANIZER** — organizador de eventos o torneos.

---

## 🏃 Equipos

Los usuarios podrán:

- Crear equipos.
- Editar información del equipo.
- Invitar integrantes.
- Unirse o abandonar equipos.
- Consultar integrantes.
- Consultar estadísticas.
- Participar en torneos.

---

## 🏟️ Instalaciones deportivas

El sistema permitirá registrar instalaciones como:

- Canchas de fútbol.
- Canchas de baloncesto.
- Gimnasios.
- Piscinas.
- Canchas de tenis.
- Otros espacios deportivos.

Cada instalación podrá contener:

- Nombre.
- Descripción.
- Ubicación.
- Tipo de deporte.
- Capacidad.
- Horario.
- Disponibilidad.
- Estado.

---

## 📅 Reservas

Los usuarios podrán:

- Consultar disponibilidad.
- Crear reservas.
- Cancelar reservas.
- Consultar historial.
- Validar conflictos de horarios.

Los administradores podrán gestionar todas las reservas.

---

## 🏆 Torneos

El módulo de torneos permitirá:

- Crear torneos.
- Configurar fechas.
- Definir deporte.
- Inscribir equipos.
- Generar partidos.
- Registrar resultados.
- Consultar tabla de posiciones.
- Finalizar torneos.

---

## ⚽ Partidos

Cada partido podrá almacenar:

- Equipo local.
- Equipo visitante.
- Fecha.
- Hora.
- Instalación.
- Estado.
- Marcador.
- Estadísticas.

Estados posibles:

```text
SCHEDULED
IN_PROGRESS
FINISHED
CANCELLED
```

---

## 📊 Estadísticas

A futuro se podrán visualizar estadísticas como:

- Partidos jugados.
- Victorias.
- Derrotas.
- Empates.
- Puntos.
- Goles/puntos anotados.
- Rendimiento por equipo.
- Posiciones en torneos.

---

## 🔔 Notificaciones

El servicio de **Node.js + Express** podrá encargarse de notificaciones como:

- Confirmación de reserva.
- Cancelación de reserva.
- Inscripción a torneo.
- Invitación a equipo.
- Recordatorio de partido.
- Resultado de partido.

Más adelante se podrá experimentar con **WebSockets** para actualizaciones en tiempo real.

---

# 🔐 Seguridad

El backend principal utilizará **Spring Security**.

La autenticación prevista será mediante **JWT (JSON Web Tokens)**.

Flujo aproximado:

```text
Usuario
   │
   ▼
POST /auth/login
   │
   ▼
Spring Boot
   │
   ├── valida credenciales
   │
   ▼
Genera JWT
   │
   ▼
Cliente guarda el token
   │
   ▼
Authorization: Bearer <token>
```

Principios de seguridad:

- Contraseñas almacenadas mediante hash.
- Nunca guardar contraseñas en texto plano.
- Validación de entradas.
- Control de permisos por roles.
- Variables sensibles mediante variables de entorno.
- No subir archivos `.env` ni credenciales al repositorio.

---

# 🗃️ Modelo inicial de base de datos

La base de datos se desarrollará principalmente con **PostgreSQL**.

Entidades previstas:

```text
User
Role
Team
TeamMember
Sport
Facility
Reservation
Tournament
TournamentTeam
Match
Notification
```

Relaciones aproximadas:

```text
USER ─────< TEAM_MEMBER >──── TEAM

USER ─────< RESERVATION >──── FACILITY

TEAM ─────< TOURNAMENT_TEAM >──── TOURNAMENT

TOURNAMENT ─────< MATCH

MATCH ───── TEAM (local)
MATCH ───── TEAM (visitante)

USER ─────< NOTIFICATION
```

---

# 🌐 API REST

La API principal se construirá con **Java + Spring Boot**.

Ruta base propuesta:

```text
/api/v1
```

## Autenticación

```http
POST /api/v1/auth/register
POST /api/v1/auth/login
```

## Usuarios

```http
GET    /api/v1/users
GET    /api/v1/users/{id}
PUT    /api/v1/users/{id}
DELETE /api/v1/users/{id}
```

## Equipos

```http
GET    /api/v1/teams
GET    /api/v1/teams/{id}
POST   /api/v1/teams
PUT    /api/v1/teams/{id}
DELETE /api/v1/teams/{id}
```

## Instalaciones

```http
GET    /api/v1/facilities
GET    /api/v1/facilities/{id}
POST   /api/v1/facilities
PUT    /api/v1/facilities/{id}
DELETE /api/v1/facilities/{id}
```

## Reservas

```http
GET    /api/v1/reservations
GET    /api/v1/reservations/{id}
POST   /api/v1/reservations
PUT    /api/v1/reservations/{id}
DELETE /api/v1/reservations/{id}
```

## Torneos

```http
GET    /api/v1/tournaments
GET    /api/v1/tournaments/{id}
POST   /api/v1/tournaments
PUT    /api/v1/tournaments/{id}
DELETE /api/v1/tournaments/{id}
```

## Partidos

```http
GET    /api/v1/matches
GET    /api/v1/matches/{id}
POST   /api/v1/matches
PUT    /api/v1/matches/{id}
DELETE /api/v1/matches/{id}
```

> Los endpoints pueden cambiar conforme evolucione el diseño.

---

# ☕ Backend principal — Java + Spring Boot

El backend seguirá una arquitectura por capas similar a:

```text
Controller
    ↓
Service
    ↓
Repository
    ↓
Database
```

Estructura prevista:

```text
backend/
└── src/
    └── main/
        └── java/
            └── com/
                └── sporthub/
                    ├── config/
                    ├── controller/
                    ├── dto/
                    ├── entity/
                    ├── exception/
                    ├── repository/
                    ├── security/
                    └── service/
```

Conceptos de Java que se practicarán:

- Variables y tipos.
- Métodos.
- Clases y objetos.
- Encapsulamiento.
- Herencia.
- Polimorfismo.
- Interfaces.
- Colecciones.
- Genéricos.
- Excepciones.
- Streams.
- Lambdas.
- Anotaciones.

Conceptos de Spring Boot:

- Controllers.
- Services.
- Repositories.
- Dependency Injection.
- Spring Data JPA.
- Hibernate.
- DTOs.
- Validaciones.
- Manejo de errores.
- Spring Security.
- JWT.
- Configuración por perfiles.

---

# 🟢 Servicio auxiliar — Node.js + Express

El servicio Node/Express se utilizará para aprender una segunda arquitectura backend sin reemplazar el backend principal de Java.

Responsabilidades previstas:

- Notificaciones.
- Eventos.
- WebSockets.
- Comunicación en tiempo real.
- Servicios auxiliares.

Estructura aproximada:

```text
notification-service/
├── src/
│   ├── controllers/
│   ├── routes/
│   ├── services/
│   ├── middleware/
│   └── app.ts
├── package.json
└── tsconfig.json
```

---

# ⚛️ Frontend web — React

React será la aplicación principal para los usuarios.

Pantallas previstas:

- Inicio.
- Registro.
- Login.
- Dashboard.
- Perfil.
- Equipos.
- Detalle de equipo.
- Instalaciones.
- Reservas.
- Torneos.
- Partidos.
- Estadísticas.
- Notificaciones.

Conceptos que se practicarán:

- Componentes.
- JSX.
- Props.
- State.
- Hooks.
- Formularios.
- React Router.
- Consumo de APIs.
- Manejo de autenticación.
- Context API o gestor de estado.
- TypeScript.
- Componentes reutilizables.

---

# 🅰️ Panel administrativo — Angular

Angular tendrá una función distinta de React: será utilizado para construir el **panel administrativo**.

Funciones previstas:

- Gestión de usuarios.
- Gestión de instalaciones.
- Gestión de equipos.
- Gestión de torneos.
- Gestión de partidos.
- Gestión de reservas.
- Dashboard administrativo.
- Reportes.

Conceptos que se practicarán:

- TypeScript.
- Components.
- Services.
- Dependency Injection.
- Routing.
- Reactive Forms.
- HttpClient.
- Guards.
- Interceptors.
- Pipes.
- Standalone Components.

---

# 📱 Aplicación móvil — React Native

La aplicación móvil utilizará la misma API de Spring Boot.

Funciones previstas:

- Registro/login.
- Perfil.
- Equipos.
- Consulta de instalaciones.
- Reservas.
- Torneos.
- Partidos.
- Notificaciones.

Conceptos:

- Views.
- Components.
- Navigation.
- State.
- Forms.
- API requests.
- Almacenamiento local.
- Autenticación.
- Android/iOS.
- Expo durante las primeras etapas.

---

# 📁 Estructura propuesta del repositorio

Inicialmente se utilizará un **monorepo** para mantener todas las partes del proyecto juntas.

```text
SPORTHUB/
│
├── backend/                 # Java + Spring Boot
│
├── frontend-web/            # React
│
├── admin-web/               # Angular
│
├── mobile/                  # React Native
│
├── notification-service/    # Node.js + Express
│
├── database/
│   ├── migrations/
│   └── scripts/
│
├── docs/
│
├── .gitignore
├── README.md
└── LICENSE
```

Esta estructura puede evolucionar conforme aumente la complejidad.

---

# 🌿 Estrategia Git

Se utilizará Git desde el inicio del proyecto.

Ramas propuestas:

```text
master
develop
feature/*
fix/*
```

Ejemplo:

```text
feature/user-registration
feature/login
feature/team-crud
feature/reservations
fix/login-validation
```

Flujo básico:

```bash
git checkout develop
git pull

git checkout -b feature/nombre-feature

# realizar cambios

git add .
git commit -m "feat: descripcion del cambio"
git push origin feature/nombre-feature
```

Después se podrá crear un **Pull Request** hacia `develop`.

---

# ✍️ Convención de commits

Se intentará utilizar **Conventional Commits**.

Ejemplos:

```text
feat: add user registration
fix: validate duplicate email
docs: update README
refactor: improve reservation service
test: add user service tests
chore: configure project dependencies
```

---

# 🐧 Linux

Linux formará parte del proceso de aprendizaje y desarrollo.

Se practicarán comandos como:

```bash
pwd
ls
cd
mkdir
touch
cp
mv
rm
cat
grep
find
chmod
ps
kill
curl
ssh
```

También se aprenderá:

- Sistema de archivos.
- Permisos.
- Procesos.
- Variables de entorno.
- Bash.
- Instalación de paquetes.
- SSH.
- Configuración de servidores.

---

# 🔄 NVM y Node.js

NVM se utilizará para gestionar versiones de Node.js.

Ejemplos:

```bash
nvm install --lts
nvm use --lts
nvm list
node --version
npm --version
```

Más adelante podrá agregarse un archivo:

```text
.nvmrc
```

para definir la versión recomendada de Node.js del proyecto.

---

# 🧪 Testing

El proyecto tendrá pruebas progresivamente.

## Java

Herramientas previstas:

- JUnit.
- Mockito.
- Spring Boot Test.

Se practicarán:

- Unit tests.
- Integration tests.
- Tests de servicios.
- Tests de repositories.
- Tests de controllers.

## JavaScript / TypeScript

Dependiendo de cada aplicación se podrán utilizar herramientas como:

- Vitest.
- Jest.
- React Testing Library.

---

# ⚙️ Variables de entorno

Las credenciales y configuraciones sensibles no deben almacenarse directamente en Git.

Ejemplo conceptual:

```env
DB_HOST=localhost
DB_PORT=5432
DB_NAME=sporthub
DB_USER=sporthub_user
DB_PASSWORD=change_me

JWT_SECRET=change_me
```

Los archivos reales `.env` deberán estar incluidos en `.gitignore`.

Se podrán agregar archivos de ejemplo:

```text
.env.example
```

sin credenciales reales.

---

# 🚀 Roadmap

## Fase 1 — Fundamentos

- [ ] Configurar Linux / terminal.
- [ ] Configurar Git.
- [ ] Aprender flujo básico de GitHub.
- [ ] Aprender Java básico.
- [ ] Aprender POO en Java.
- [ ] Aprender SQL básico.
- [ ] Diseñar la primera versión de la base de datos.

## Fase 2 — Backend Java

- [ ] Crear proyecto Spring Boot.
- [ ] Configurar PostgreSQL.
- [ ] Crear entidades.
- [ ] Crear repositories.
- [ ] Crear services.
- [ ] Crear controllers.
- [ ] Implementar DTOs.
- [ ] Implementar validaciones.
- [ ] Implementar manejo global de errores.
- [ ] Implementar registro.
- [ ] Implementar login.
- [ ] Implementar JWT.
- [ ] Implementar roles.

## Fase 3 — React

- [ ] Crear proyecto React.
- [ ] Configurar TypeScript.
- [ ] Crear layout.
- [ ] Crear registro/login.
- [ ] Consumir API.
- [ ] Crear dashboard.
- [ ] Crear módulo de equipos.
- [ ] Crear módulo de instalaciones.
- [ ] Crear módulo de reservas.
- [ ] Crear módulo de torneos.

## Fase 4 — Node.js + Express

- [ ] Configurar NVM.
- [ ] Crear servicio Node.js.
- [ ] Configurar Express.
- [ ] Aprender middleware.
- [ ] Crear servicio de notificaciones.
- [ ] Explorar WebSockets.
- [ ] Comunicar Express con el backend principal.

## Fase 5 — React Native

- [ ] Crear aplicación móvil.
- [ ] Crear navegación.
- [ ] Implementar autenticación.
- [ ] Consumir la API de SportHub.
- [ ] Crear equipos.
- [ ] Crear reservas.
- [ ] Mostrar torneos.
- [ ] Mostrar notificaciones.

## Fase 6 — Angular

- [ ] Crear panel administrativo.
- [ ] Crear routing.
- [ ] Crear autenticación.
- [ ] Crear guards.
- [ ] Crear servicios HTTP.
- [ ] Gestión de usuarios.
- [ ] Gestión de instalaciones.
- [ ] Gestión de torneos.
- [ ] Dashboard administrativo.

## Fase 7 — Calidad y despliegue

- [ ] Agregar pruebas.
- [ ] Mejorar seguridad.
- [ ] Documentar API.
- [ ] Agregar logs.
- [ ] Dockerizar servicios.
- [ ] Preparar entorno Linux.
- [ ] Configurar CI/CD.
- [ ] Desplegar aplicación.

---

# 🧭 Ruta de aprendizaje

El orden recomendado de aprendizaje durante el proyecto es:

```text
1. Linux
2. Git y GitHub
3. Java
4. Programación Orientada a Objetos
5. SQL
6. PostgreSQL
7. Maven / Gradle
8. Spring Boot
9. APIs REST
10. JavaScript
11. TypeScript
12. NVM + Node.js
13. React
14. Express
15. React Native
16. Angular
17. Testing
18. Docker
19. CI/CD
20. Despliegue
```

La intención es aprender cada tecnología cuando exista una necesidad real dentro de SportHub.

---

# 🏁 Primer sprint

El primer sprint tendrá como objetivo establecer los fundamentos del proyecto.

## Sprint 1 — Base del proyecto

### Objetivos

- Preparar Git.
- Establecer estructura inicial del repositorio.
- Aprender Java fundamental.
- Configurar PostgreSQL.
- Diseñar usuarios y roles.
- Crear el backend inicial con Spring Boot.

### Tareas

- [x] Crear repositorio de GitHub.
- [x] Crear README inicial.
- [ ] Configurar `.gitignore`.
- [ ] Crear ramas de trabajo.
- [ ] Instalar/configurar Java.
- [ ] Crear proyecto Spring Boot.
- [ ] Ejecutar aplicación Spring Boot localmente.
- [ ] Instalar PostgreSQL.
- [ ] Crear base de datos `sporthub`.
- [ ] Crear entidad `User`.
- [ ] Crear entidad `Role`.
- [ ] Crear primer repository.
- [ ] Crear primer service.
- [ ] Crear primer controller.
- [ ] Crear endpoint de prueba.
- [ ] Realizar primer Pull Request.

---

# 📚 Filosofía de aprendizaje

Este proyecto no busca solamente producir código.

Cada módulo se desarrollará comprendiendo:

1. **Qué problema resuelve.**
2. **Por qué se utiliza esa tecnología.**
3. **Cómo funciona internamente.**
4. **Cómo se conecta con las demás partes del sistema.**
5. **Qué alternativas existen.**
6. **Qué buenas prácticas deberían seguirse.**

La meta es poder explicar el proyecto completo, no simplemente lograr que funcione.

---

# 🔮 Posibles mejoras futuras

Una vez completada la versión principal se podrán explorar:

- Docker.
- Redis.
- RabbitMQ o Kafka.
- Microservicios más avanzados.
- GraphQL.
- WebSockets.
- CI/CD con GitHub Actions.
- Cloud deployment.
- Observabilidad y métricas.
- Caché.
- Pagos.
- Emails.
- Push notifications.
- Inteligencia artificial para recomendaciones.
- Análisis avanzado de estadísticas deportivas.

---

# 🤝 Contribución

Actualmente SportHub es un proyecto personal de aprendizaje.

El flujo de contribución previsto será:

1. Crear una rama desde `develop`.
2. Implementar una funcionalidad.
3. Crear commits pequeños y descriptivos.
4. Subir la rama.
5. Crear un Pull Request.
6. Revisar cambios.
7. Integrar a `develop`.

---

# 📖 Documentación

Conforme avance el proyecto se agregará documentación adicional dentro de:

```text
/docs
```

Posibles documentos:

- Arquitectura.
- Modelo entidad-relación.
- Especificación de API.
- Guía de instalación.
- Decisiones técnicas.
- Diagramas.
- Guía de contribución.

---

# 👨‍💻 Autor

**Victor Julio**

Proyecto desarrollado con fines de aprendizaje y práctica de Ingeniería en Computación y desarrollo Full Stack.

---

## 📌 Estado actual

```text
Repositorio creado           ✅
Especificación inicial       ✅
README                       ✅
Backend Spring Boot          ⏳
Base de datos                ⏳
Frontend React               ⏳
Servicio Express             ⏳
React Native                 ⏳
Panel Angular                ⏳
Testing                      ⏳
Despliegue                   ⏳
```

---

> **SportHub** será construido de forma incremental. Cada nueva tecnología se incorporará cuando exista una necesidad concreta dentro del sistema.
