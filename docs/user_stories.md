## PARTE 1 — USER STORIES
### Flujo 1: Descubrimiento de Eventos Cercanos
**US-01: Descubrir eventos cercanos relevantes**
Como Valentina Restrepo, quiero ver eventos musicales cerca de mi ubicación que coincidan con mis gustos musicales para que pueda asistir a conciertos de mi interés.
**Criterios de aceptación:**
- [ ] La app muestra eventos en un radio de 10 km desde la ubicación del usuario.
- [ ] Los eventos se filtran por género musical.
- [ ] La lista de eventos incluye información como nombre del evento, artista, venue, fecha, distancia y precio.
**Prioridad:** Alta | **Estimación:** M

**US-02: Aplicar filtros de búsqueda**
Como Valentina Restrepo, quiero aplicar filtros de búsqueda por género musical para encontrar eventos específicos de post-punk y shoegaze para satisfacer mis gustos musicales.
**Criterios de aceptación:**
- [ ] La app permite al usuario seleccionar múltiples géneros musicales para filtrar eventos.
- [ ] Los eventos se actualizan en tiempo real según los filtros aplicados.
- [ ] La app muestra una indicación clara de los filtros actuales aplicados.
**Prioridad:** Alta | **Estimación:** M

**US-03: Ver detalles del evento**
Como Valentina Restrepo, quiero ver los detalles de un evento específico, como la descripción del evento, la biografía del artista y las opciones de compra de boletos, para decidir si asistir o no al evento.
**Criterios de aceptación:**
- [ ] La app muestra una pantalla de detalles del evento con información completa.
- [ ] La pantalla de detalles incluye enlaces para comprar boletos directamente.
- [ ] La app proporciona una opción para compartir el evento en redes sociales.
**Prioridad:** Media | **Estimación:** L

### Flujo 2: Compra de Boletos
**US-04: Comprar boletos de eventos**
Como Valentina Restrepo, quiero comprar boletos para eventos de manera segura y directa para evitar intermediarios y asegurarme de que mi dinero llegue a los artistas.
**Criterios de aceptación:**
- [ ] La app ofrece un proceso de compra de boletos integrado y seguro.
- [ ] El usuario puede pagar con各种 métodos de pago.
- [ ] La app envía un correo electrónico de confirmación con los detalles del boleto después de la compra.
**Prioridad:** Alta | **Estimación:** L

**US-05: Verificar disponibilidad de boletos**
Como Valentina Restrepo, quiero verificar la disponibilidad de boletos para un evento específico para planificar con anticipación y asegurarme de obtener boletos.
**Criterios de aceptación:**
- [ ] La app muestra la cantidad de boletos disponibles para cada evento.
- [ ] El sistema actualiza en tiempo real la disponibilidad de boletos.
- [ ] La app notifica al usuario si los boletos se agotan o si hay una espera para comprar boletos.
**Prioridad:** Media | **Estimación:** M

**US-06: Recibir notificaciones de eventos**
Como Valentina Restrepo, quiero recibir notificaciones sobre eventos próximos y actualizaciones de eventos que me interesan para estar al tanto y no perderme conciertos.
**Criterios de aceptación:**
- [ ] La app permite al usuario suscribirse a notificaciones push para eventos específicos.
- [ ] El sistema envía notificaciones push con anticipación a los eventos.
- [ ] La app ofrece una opción para personalizar las preferencias de notificación.
**Prioridad:** Media | **Estimación:** M

## PARTE 2 — CASOS DE USO
### CU-01: Descubrir y comprar boletos para un concierto
- **Actor principal:** Valentina Restrepo
- **Precondición:** La app tiene acceso a la ubicación del usuario y el usuario tiene una cuenta en la app.
- **Flujo principal:**
  1. Valentina abre la app y concede permiso de ubicación.
  2. La app muestra eventos cercanos en un radio de 10 km.
  3. Valentina aplica filtros por género musical (post-punk y shoegaze).
  4. La app muestra una lista de eventos que coinciden con los filtros.
  5. Valentina selecciona un evento y ve los detalles.
  6. Valentina compra boletos para el evento a través de la app.
- **Flujo alternativo:** Si no hay eventos disponibles que coincidan con los filtros, la app sugiere eventos similares o notifica al usuario sobre eventos próximos que podrían interesarle.
- **Postcondición:** Valentina ha comprado boletos para un concierto que coinside con sus gustos musicales y ha recibido un correo electrónico de confirmación.

### CU-02: Compartir un evento en redes sociales
- **Actor principal:** Valentina Restrepo
- **Precondición:** Valentina tiene una cuenta en la app y ha encontrado un evento que desea compartir.
- **Flujo principal:**
  1. Valentina selecciona un evento en la app.
  2. Valentina elige la opción de compartir el evento.
  3. La app muestra opciones para compartir en diferentes redes sociales (Instagram, Facebook, Twitter).
  4. Valentina selecciona una red social y comparte el evento.
- **Flujo alternativo:** Si la app no puede conectarse a las redes sociales del usuario, muestra un mensaje de error y sugiere soluciones alternativas para compartir el evento.
- **Postcondición:** El evento ha sido compartido en la red social seleccionada por Valentina.

### CU-03: Recibir notificaciones de eventos
- **Actor principal:** Valentina Restrepo
- **Precondición:** Valentina tiene una cuenta en la app y ha suscrito notificaciones push para eventos específicos.
- **Flujo principal:**
  1. La app detecta que un evento para el que Valentina se ha suscrito está próximo.
  2. El sistema envía una notificación push a Valentina con los detalles del evento.
  3. Valentina ve la notificación y decide si asistir o no al evento.
- **Flujo alternativo:** Si la notificación push no se puede entregar, la app intenta enviar una notificación por correo electrónico o muestra la notificación dentro de la app la próxima vez que Valentina la abra.
- **Postcondición:** Valentina ha recibido una notificación sobre un evento próximo que le interesa y puede planificar con anticipación.