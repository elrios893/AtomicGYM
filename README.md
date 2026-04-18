# AtomicGYM

AtomicGYM es una solución en **.NET 9** orientada a la gestión de un gimnasio, compuesta por:

- Una aplicación web MVC (`GYM_PW`) para la interacción de usuarios y administración básica.
- Una API REST (`GestionMaquinas`) para la gestión CRUD de máquinas.
- Recursos de persistencia (`persistencia/`) con script SQL y modelo de base de datos.

## Funcionalidades identificadas

- Registro e inicio de sesión de usuarios (autenticación por cookies y sesión).
- Formulario de contacto con envío de correo SMTP.
- Gestión de máquinas desde la web (listar, detalle, crear, editar y eliminar) consumiendo la API.
- Integración con GeoNames para consultas geográficas (países/estados).
- Modelo de datos de gimnasio con entidades de usuarios, membresías, servicios, sedes, pagos, rutinas y máquinas.

## Arquitectura del repositorio

```text
AtomicGYM/
├─ GYM_PW/                         # Aplicación web ASP.NET Core MVC
├─ API machines/
│  └─ SlnGestionMaquinas/          # API ASP.NET Core para máquinas
├─ persistencia/                   # Script SQL y recursos de base de datos
├─ Informacion proyecto/           # Artefactos de análisis funcional
└─ GYM_PW.sln                      # Solución principal
```

## Tecnologías

- ASP.NET Core MVC / Web API
- Entity Framework Core 9
- PostgreSQL (Npgsql)
- Newtonsoft.Json
- Bootstrap + jQuery

## Requisitos

- .NET SDK 9.0
- PostgreSQL en ejecución

## Configuración local

1. Configura las cadenas de conexión en:
   - `GYM_PW/appsettings.json`
   - (si se usa en API) `API machines/SlnGestionMaquinas/GestionMaquinas/appsettings*.json`
2. Configura credenciales reales para SMTP y evita versionar secretos.
3. Verifica la URL de la API usada por la web en `ApiMachines:Url`:
   - Archivo: `GYM_PW/appsettings.json`
   - Debe apuntar al host/puerto donde realmente se ejecuta `GestionMaquinas`.

## Ejecución

### 1) API de máquinas

```bash
cd "API machines/SlnGestionMaquinas/GestionMaquinas"
dotnet run
```

### 2) Web MVC

```bash
cd GYM_PW
dotnet run
```

## Compilación

```bash
dotnet build GYM_PW.sln
dotnet build "API machines/SlnGestionMaquinas/SlnGestionMaquinas.sln"
```

## Base de datos

- Script de referencia: `persistencia/script.sql`
- Migraciones:
  - Web: `GYM_PW/Migrations`
  - API: `API machines/SlnGestionMaquinas/GestionMaquinas/Migrations`

## Estado actual

El repositorio compila correctamente en su estado base, con advertencias de nulabilidad existentes que no impiden la compilación.
