## PARTE 1 — USER STORIES

### US-01: Configuración de Perfil Musical
Como Valentina Restrepo, quiero seleccionar mis géneros favoritos para recibir recomendaciones de conciertos personalizadas.
**Criterios de aceptación:**
- [ ] La aplicación ofrece una lista de géneros musicales para seleccionar.
- [ ] El usuario puede seleccionar al menos 3 géneros favoritos.
- [ ] La aplicación guarda las preferencias del usuario para futuras sugerencias.
**Prioridad:** Alta | **Estimación:** M

### US-02: Registro y Autenticación
Como Valentina Restrepo, quiero registrarme y autenticarme en la aplicación para acceder a contenido exclusivo y comprar boletos de manera segura.
**Criterios de aceptación:**
- [ ] La aplicación ofrece métodos de registro como Google, Apple y correo electrónico.
- [ ] El usuario puede completar su registro y verificar su correo electrónico.
- [ ] La aplicación autentica al usuario y lo redirige a la pantalla de inicio.
**Prioridad:** Alta | **Estimación:** L

### US-03: Búsqueda de Conciertos
Como Valentina Restrepo, quiero buscar conciertos en vivo cerca de mi ubicación y filtrar por género musical para encontrar eventos que me gusten.
**Criterios de aceptación:**
- [ ] La aplicación permite al usuario buscar conciertos por ubicación y género musical.
- [ ] La aplicación muestra una lista de conciertos que coinciden con los criterios de búsqueda.
- [ ] El usuario puede filtrar la lista de conciertos por fecha y distancia.
**Prioridad:** Alta | **Estimación:** L

### US-04: Compra de Boletos
Como Valentina Restrepo, quiero comprar boletos de conciertos de manera segura y sin comisiones abusivas para apoyar a artistas independientes.
**Criterios de aceptación:**
- [ ] La aplicación ofrece un proceso de compra de boletos seguro y transparente.
- [ ] El usuario puede pagar con diferentes métodos de pago.
- [ ] La aplicación garantiza la autenticidad de los boletos y emite un comprobante de compra.
**Prioridad:** Alta | **Estimación:** M

### US-05: Descubrimiento de Nuevos Artistas
Como Valentina Restrepo, quiero descubrir nuevos artistas y géneros musicales a través de recomendaciones personalizadas para ampliar mi gusto musical.
**Criterios de aceptación:**
- [ ] La aplicación ofrece recomendaciones de artistas y géneros musicales basadas en las preferencias del usuario.
- [ ] El usuario puede explorar perfiles de artistas y escuchar muestras de su música.
- [ ] La aplicación sugiere conciertos de artistas que podrían gustar al usuario.
**Prioridad:** Media | **Estimación:** M

## PARTE 2 — CASOS DE USO

### CU-01: Registro y Configuración de Perfil Musical
- **Actor principal:** Valentina Restrepo
- **Precondición:** La aplicación está instalada y el usuario tiene acceso a internet.
- **Flujo principal:**
  1. El usuario abre la aplicación y selecciona registrar su cuenta.
  2. El usuario completa su registro y verifica su correo electrónico.
  3. El usuario selecciona sus géneros favoritos y conecta su servicio de streaming musical (opcional).
  4. La aplicación guarda las preferencias del usuario y lo redirige a la pantalla de inicio.
- **Flujo alternativo:** Si el usuario no puede verificar su correo electrónico, la aplicación le permite reenviar el código de verificación.
- **Postcondición:** El usuario tiene una cuenta configurada y puede acceder a contenido personalizado.

### CU-02: Búsqueda y Compra de Conciertos
- **Actor principal:** Valentina Restrepo
- **Precondición:** El usuario tiene una cuenta configurada y está conectado a internet.
- **Flujo principal:**
  1. El usuario abre la aplicación y selecciona buscar conciertos.
  2. El usuario selecciona su ubicación y género musical preferido.
  3. La aplicación muestra una lista de conciertos que coinciden con los criterios de búsqueda.
  4. El usuario selecciona un concierto y compra boletos de manera segura.
  5. La aplicación emite un comprobante de compra y lo guarda en la cuenta del usuario.
- **Flujo alternativo:** Si no hay conciertos disponibles que coincidan con los criterios de búsqueda, la aplicación sugiere conciertos similares.
- **Postcondición:** El usuario tiene boletos comprados y un comprobante de compra guardado en su cuenta.

### CU-03: Descubrimiento de Nuevos Artistas
- **Actor principal:** Valentina Restrepo
- **Precondición:** El usuario tiene una cuenta configurada y está conectado a internet.
- **Flujo principal:**
  1. El usuario abre la aplicación y selecciona explorar nuevos artistas.
  2. La aplicación muestra recomendaciones de artistas y géneros musicales basadas en las preferencias del usuario.
  3. El usuario selecciona un artista y escucha muestras de su música.
  4. La aplicación sugiere conciertos de artistas que podrían gustar al usuario.
- **Flujo alternativo:** Si el usuario no encuentra artistas que le gusten, la aplicación le permite buscar por género musical o ubicación.
- **Postcondición:** El usuario ha descubierto nuevos artistas y tiene recomendaciones de conciertos personalizadas.