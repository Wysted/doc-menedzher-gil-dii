# Documentación de Comandos - менеджер гильдии

менеджер гильдии es un bot de Discord para gestión de eventos, parties, notificaciones y roles en servidores de comunidad.

---

## Índice de Comandos

-   [Server](#server)
-   [Role](#role)
-   [User](#user)
-   [Channel](#channel)
-   [Event](#event)
-   [Notification](#notification)
-   [Role-m](#role-m)
-   [Party](#party)
-   [Character](#character)

---

## Server

### `/server add`

Registrar un servidor Discord en la base de datos.  
**Acceso:** `w-only`

### `/server list`

Listar todos los servidores registrados.  
**Acceso:** `w-only`

### `/server delete`

Eliminar un servidor Discord.

-   `servidor` (string, requerido) — Seleccionar servidor  
    **Acceso:** `w-only`

### `/server update`

Actualizar la zona horaria del servidor.

-   `utc` (string, requerido) — Seleccionar zona horaria  
    **Acceso:** `role-restricted`

### `/server rol-admin`

Asignar rol como administrador.

-   `role` (string, requerido) — Seleccionar rol  
    **Acceso:** `owner-only`

---

## Role

### `/role create`

Crear un nuevo rol.

-   `nombre` (string, requerido) — Nombre del rol
-   `mencionable` (bool, opcional) — Si se puede mencionar  
    **Acceso:** `owner-only`

### `/role assign`

Asignar un rol a un usuario.

-   `usuario` (user, requerido) — Usuario destino
-   `rol` (rol, requerido) — Rol a asignar  
    **Acceso:** `owner-only`

### `/role remove`

Remover un rol de un usuario.

-   `usuario` (user, requerido) — Usuario destino
-   `rol` (rol, requerido) — Rol a remover  
    **Acceso:** `owner-only`

### `/role delete`

Eliminar un rol.

-   `role` (string, requerido) — Rol a eliminar  
    **Acceso:** `owner-only`

---

## User

### `/user kick`

Expulsar usuario.

-   `usuario` (user, requerido)
-   `razón` (string, opcional)  
    **Acceso:** `role-restricted`

### `/user ban`

Banear usuario.

-   `usuario` (user, requerido)
-   `razón` (string, opcional)  
    **Acceso:** `owner-only`

### `/user unban`

Quitar ban.

-   `user` (string, requerido)  
    **Acceso:** `owner-only`

---

## Channel

### `/channel clear`

Limpiar mensajes del canal.

-   `channel` (string, requerido) — Canal a limpiar
-   `amount` (int, requerido) — Cantidad (máx 100)  
    **Acceso:** `role-restricted`

---

## Event

### `/event add unico`

Agregar evento único.

-   `nombre` (string, requerido)
-   `hora` (string, requerido, formato HH:MM)
-   `tipo` (string, requerido)
-   `dia` (string, requerido) — Lunes a Domingo o "none"
-   `avisar` (string, opcional) — Minutos antes de notificación  
    **Acceso:** `role-restricted`

### `/event add recurrente`

Agregar evento recurrente.

-   `nombre` (string, requerido)
-   `hora` (string, requerido, formato HH:MM)
-   `tipo` (string, requerido)
-   `dia` (string, requerido) — Día o "all"
-   `avisar` (string, opcional)
-   `eliminar` (bool, opcional) — Si elimina parties al finalizar  
    **Acceso:** `role-restricted`

### `/event list`

Listar eventos del servidor.  
**Acceso:** `everyone`

### `/event delete`

Eliminar evento.

-   `evento` (string, requerido)  
    **Acceso:** `role-restricted`

### `/event party`

Mostrar parties vinculadas a un evento.

-   `evento` (string, requerido)  
    **Acceso:** `everyone`

### `/event register`

Asignar rol para reaccionar en evento.

-   `evento` (string, requerido)  
    **Acceso:** `role-restricted`

### `/event participants`

Listar participantes de un evento.

-   `evento` (string, requerido)  
    **Acceso:** `everyone`

### `/event myparty`

Listar parties donde estás inscrito.  
**Acceso:** `everyone`

---

## Notification

### `/notification assign-channel`

Asignar canal de notificaciones.

-   `tipo` (string, requerido)
-   `canal` (string, requerido)
-   `notification-type` (string, requerido) — Individual / Resumen
-   `role` (string, opcional)  
    **Acceso:** `role-restricted`

### `/notification unassign-channel`

Quitar canal de notificaciones.

-   `canales` (string, requerido)  
    **Acceso:** `role-restricted`

---

## Role-m

### `/role-m create`

Crear rol para miembros.

-   `nombre` (string, requerido)
-   `description` (string, opcional)  
    **Acceso:** `role-restricted`

### `/role-m update`

Actualizar rol para miembros.

-   `role` (string, requerido)
-   `nombre` (string, opcional)
-   `descripcion` (string, opcional)  
    **Acceso:** `role-restricted`

### `/role-m delete`

Eliminar rol para miembros.

-   `role` (string, requerido)  
    **Acceso:** `role-restricted`

### `/role-m list`

Listar roles para miembros.  
**Acceso:** `role-restricted`

---

## Party

### `/party create`

Crear party.

-   `nombre` (string, requerido)
-   `evento` (string, requerido)  
    **Acceso:** `role-restricted`

### `/party update`

Actualizar party.

-   `party` (string, requerido)
-   `nombre` (string, requerido)  
    **Acceso:** `role-restricted`

### `/party delete`

Eliminar party.

-   `party` (string, requerido)  
    **Acceso:** `role-restricted`

### `/party members`

Listar miembros de una party.

-   `party` (string, requerido)  
    **Acceso:** `role-restricted`

#### Subcomandos para miembros de party

##### `/party member add`

Añadir miembro a party.

-   `party` (string, requerido)
-   `usuario` (user, requerido)
-   `personaje` (string, requerido)
-   `rol` (string, requerido)  
    **Acceso:** `role-restricted`

##### `/party member update`

Actualizar miembro.

-   `party` (string, requerido)
-   `miembro` (string, requerido)
-   `personaje` (string, opcional)
-   `rol` (string, opcional)
-   `usuario` (user, opcional)  
    **Acceso:** `role-restricted`

##### `/party member delete`

Eliminar miembro.

-   `party` (string, requerido)
-   `miembro` (string, requerido)  
    **Acceso:** `role-restricted`

---

## Character

### `/character add`

Añadir personaje.

-   `usuario` (user, requerido)
-   `nombre` (string, requerido)
-   `raza` (string, requerido)  
    **Acceso:** `role-restricted`

### `/character delete`

Eliminar personaje.

-   `personaje` (string, requerido)  
    **Acceso:** `role-restricted`

### `/character list`

Listar personajes.  
**Acceso:** `role-restricted`

---

# Niveles de acceso

-   `everyone`: Todos los usuarios
-   `w-only`: Dueño del bot
-   `role-restricted`: Rol especifico de administracion
-   `owner-only`: Solo dueño del servidor

---

## Contacto

Si quieres tener este bot en tu gremio o servidor de Discord, contáctanos en:

-   Correo: vladimirbesser@gmail.com
-   Discord: wysted

## Estaremos encantados de ayudarte a integrarlo y configurarlo.
