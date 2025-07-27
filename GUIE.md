# 📘 Guía de Uso — менеджер гильдии (Servidor estilo Mu Online)

**менеджер гильдии** es un bot de Discord para organizar eventos, gestionar personajes, roles, parties y notificaciones dentro de un gremio o comunidad de Mu Online.

---

## ⚙️ Paso 1: Configuración Inicial del Gremio

### 🕓 Establecer zona horaria del servidor

/server update utc: "America/Bogota"

### 🛡️ Asignar rol de administración del gremio

/server rol-admin role: @GuildMaster

---

## 👥 Paso 2: Gestión de Roles

### 🎭 Crear roles personalizables

/role create nombre: "PVP" mencionable: true

### 🎖️ Asignar roles a miembros

/role assign usuario: @Zenor rol: PVP

---

## 🔔 Paso 3: Canal de Notificaciones

Puedes configurar qué tipo de eventos deseas anunciar y en qué canal se publicarán.
Un canal puede ser asignado a múltiples tipos de evento.
Además, puedes asignar un rol opcional que será mencionado en los avisos.
---
### Tipos de Aviso:
- Individual: Se notificará cada evento por separado cuando falte un tiempo específico.
- Resumen: Se mostrará una lista con todos los eventos próximos.

/notification assign-channel tipo: "evento" canal: #eventos notification-type: "Resumen" role: @GuildMember

---

## 📅 Paso 4: Eventos PvE, PvP y Tipo de evento

### Crear tipo evento
/event type add nombre: PvP 

### 🩸 Crear evento único — _Blood Castle_

/event add unico nombre: "Arka" hora: 21:00 tipo: "PvP" dia: "Viernes" avisar: "30"

### 🌀 Crear evento recurrente — _Chaos Castle diario_

/event add recurrente nombre: "Castle Siege" hora: 22:00 tipo: "PvP" dia: "Domingo" avisar: "15" eliminar: true

---

## 🧝 Paso 5: Registro de Personajes y Creacion de roles

### ➕ Añadir personaje

/character add usuario: @Zenor nombre: "ZenorDW" raza: "Dark Wizard"

### ➕ Añadir rol

/role-m create nombre: SUPP

### 📋 Ver personajes

/character list

---

## 🛡️ Paso 6: Crear y Administrar Parties

### 🧩 Crear party para evento

/party create nombre: "GM" evento: "Arka"

### ➕ Añadir miembros con clase y rol

/party member add party: "GM" usuario: @Zenor personaje: "ZenorDW" rol: "SUPP"

---

## Paso 7: Crear registro de evento

/event register evento: "Castle siege"

## 🔎 Paso 7: Consultas Rápidas

### 📌 Ver parties donde estás registrado

/event myparty

### 👥 Ver miembros de una party

/party members party: "GM"

### 👀 Ver participantes de evento

/event participants evento: "Castle Siege"

---

## 🧹 Mantenimiento y Limpieza

### 🧽 Limpiar mensajes de canal

/channel clear channel: #general amount: 50

### ❌ Eliminar evento o party

/event delete evento: "Castle Siege"

/party delete party: "GM"

---

### ⚠️ Nota sobre la opción `eliminar: true` en eventos recurrentes

Al crear un evento recurrente con la opción `eliminar: true`, el bot ejecuta un comportamiento automático para facilitar la reutilización de las parties asociadas.

> **Aproximadamente 10 minutos después de la hora de inicio del evento**, el bot eliminará a **todos los miembros** de las parties vinculadas a ese evento.

-   ✅ **Las parties NO se eliminan**, solo se vacían.
-   🔄 Esto permite **reutilizar las mismas parties** para futuros eventos recurrentes sin tener que crearlas nuevamente.
-   🎯 Útil para eventos diarios como _Chaos Castle_, _Devil Square_, _Kalima_, etc., donde las formaciones cambian constantemente.

#### 🧪 Ejemplo práctico:

/event add recurrente nombre: "Chaos Castle" hora: 12:00 tipo: "PvP" dia: "Todos" avisar: "15" eliminar: true

Con esta configuración:

-   El evento se notificará todos los días a las 12:00.
-   Las parties asociadas se limpiarán automáticamente a las 12:10 aprox.
-   Puedes mantener la estructura de party sin tener que volver a crearla.

### 🗓️ Nota sobre eventos únicos

Los eventos creados con `/event add unico` tienen un comportamiento automático de limpieza:

> **Un evento único se elimina automáticamente un tiempo después de su hora de inicio.**

-   🕑 Esto ocurre aproximadamente **unos minutos después de la hora configurada** (usualmente entre 5 y 15 minutos).
-   🧼 Sirve para mantener el listado de eventos limpio y sin acumulación innecesaria.
-   🔁 Si necesitas repetir el mismo evento otro día, simplemente vuelve a crearlo.

#### 🧪 Ejemplo práctico:

/event add unico nombre: "Battle Event" hora: 20:30 tipo: "PvP" dia: "Sábado" avisar: "30"

Este evento será visible y funcional para todos los usuarios hasta poco después de las 20:30. Luego, el bot lo eliminará automáticamente del sistema.
