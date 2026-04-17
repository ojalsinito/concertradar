

# Flujos Principales — ConcertRadar

---

## Flujo 1: Onboarding y Configuración de Perfil Musical

**Actor:** Valentina Restrepo (usuario nuevo)
**Objetivo:** Crear cuenta y configurar preferencias musicales para recibir recomendaciones relevantes.

---

### Pasos

| # | Acción del usuario | Pantalla | Componente clave |
|---|---|---|---|
| 1 | Abre la app por primera vez | `Splash / Welcome` | Carrusel de valor (3 slides) + CTA "Comenzar" |
| 2 | Selecciona método de registro | `Registro` | Botones: Google · Apple · Email |
| 3 | Completa datos básicos (si elige email) | `Registro — Formulario` | Campos: nombre, email, contraseña, confirmación |
| 4 | Verifica email | `Verificación de correo` | Input código de 6 dígitos + "Reenviar código" |
| 5 | Conecta servicio de streaming (opcional) | `Onboarding — Conectar música` | Botones Spotify / Apple Music + "Saltar" |
| 6 | Selecciona géneros favoritos (mín. 3) | `Onboarding — Géneros` | Grid de chips seleccionables (shoegaze, math rock, cumbia experimental, etc.) |
| 7 | Define ciudad principal | `Onboarding — Ciudad` | Buscador autocompletable + opción "Usar mi ubicación" |
| 8 | Concede permisos del sistema | `Permisos` | Modales nativos: ubicación → notificaciones |
| 9 | Visualiza confirmación | `Onboarding — Completo` | Resumen de perfil + CTA "Ir al Radar" |

### Estados de error

| Código | Condición | Pantalla | Comportamiento |
|---|---|---|---|
| `ERR-01` | Email ya registrado | `Registro — Formulario` | Inline error bajo campo email: *"Este correo ya tiene cuenta. ¿Quieres iniciar sesión?"* con link a Login |
| `ERR-02` | Contraseña débil (< 8 chars, sin número) | `Registro — Formulario` | Indicador de fortaleza en rojo + lista de requisitos no cumplidos |
| `ERR-03` | Código de verificación incorrecto/expirado | `Verificación de correo` | Toast: *"Código inválido o expirado"* + botón "Reenviar" con countdown 60s |
| `ERR-04` | Falla OAuth (Google/Apple) | `Registro` | Modal: *"No pudimos conectar con [servicio]. Intenta de nuevo o usa email."* |
| `ERR-05` | Falla conexión con Spotify/Apple Music | `Onboarding — Conectar música` | Banner: *"No se pudo conectar. Puedes seleccionar géneros manualmente."* → avanza a paso 6 |
| `ERR-06` | Menos de 3 géneros seleccionados al intentar avanzar | `Onboarding — Géneros` | CTA deshabilitado + hint: *"Selecciona al menos 3 géneros para personalizar tu radar"* |
| `ERR-07` | Permiso de ubicación denegado | `Permisos` | Fallback a paso 7 (ciudad manual) + tooltip: *"Sin ubicación usaremos tu ciudad configurada"* |
| `ERR-08` | Sin conexión a internet (cualquier paso) | Pantalla activa | Fullscreen state: ilustración offline + *"Sin conexión. Revisa tu red."* + botón "Reintentar" |

### Estado de éxito

> ✅ **Perfil creado y configurado.** Valentina llega al Radar (Home) con el mapa centrado en Medellín mostrando eventos filtrados por sus géneros (shoegaze, math rock, cumbia experimental). Recibe notificación de bienvenida: *"¡Listo! Encontramos 12 eventos cerca de ti esta semana."*

---

---

## Flujo 2: Descubrimiento de Eventos en el Radar

**Actor:** Valentina Restrepo (usuario autenticado)
**Objetivo:** Encontrar conciertos underground de sus géneros favoritos cerca de su ubicación actual.

---

### Pasos

| # | Acción del usuario | Pantalla | Componente clave |
|---|---|---|---|
| 1 | Abre la app (ya logueada) | `Radar (Home / Mapa)` | Mapa centrado en ubicación actual con pins de eventos |
| 2 | Observa los pins en el mapa | `Radar — Mapa` | Pins codificados por color según género; badge de precio en cada pin |
| 3 | Abre panel de filtros | `Radar — Filtros` | Bottom sheet: género, rango de fecha, precio (slider min-max), tipo (mainstream/underground), distancia |
| 4 | Aplica filtros: underground + shoegaze + esta semana + < $50.000 COP | `Radar — Filtros` | Chips activos + CTA "Aplicar filtros (N resultados)" con preview de cantidad |
| 5 | Visualiza resultados filtrados en mapa | `Radar — Mapa (filtrado)` | Mapa actualizado; badge "3 eventos" + botón "Limpiar filtros" |
| 6 | Cambia a vista lista (toggle) | `Radar — Vista Lista` | Cards ordenables: por distancia · por fecha · por precio |
| 7 | Toca un pin o card de evento | `Radar → Preview Card` | Bottom card: nombre, artista, fecha, venue, precio, distancia + CTA "Ver detalle" |
| 8 | Navega al detalle del evento | `Detalle de Evento` | Pantalla completa del evento (→ Flujo 4) |

### Estados de error

| Código | Condición | Pantalla | Comportamiento |
|---|---|---|---|
| `ERR-09` | GPS no disponible / permisos revocados | `Radar — Mapa` | Banner superior: *"No podemos acceder a tu ubicación"* + botón "Configurar" (abre settings) + fallback a ciudad del perfil |
| `ERR-10` | Filtros sin resultados | `Radar — Mapa (filtrado)` | Empty state en mapa: *"No encontramos eventos con estos filtros en tu zona"* + sugerencias: "Ampliar distancia" · "Cambiar fechas" · "Explorar todos los géneros" |
| `ERR-11` | Error cargando eventos (API timeout) | `Radar — Mapa` | Skeleton loaders → tras 10s: *"No pudimos cargar los eventos. Revisa tu conexión."* + botón "Reintentar" |
| `ERR-12` | Evento del pin ya cancelado/eliminado | `Preview Card` | Card con estado: *"Este evento fue cancelado"* con opción "Ver similares" |
| `ERR-13` | Cambio manual de ubicación — ciudad no encontrada | `Cambiar ubicación` | Inline en buscador: *"No encontramos esa ciudad. Prueba con otro nombre."* |
| `ERR-14` | Sin conexión al hacer scroll/zoom en mapa | `Radar — Mapa` | Tiles del mapa en caché + banner: *"Estás offline. Mostrando últimos datos guardados."* |

### Estado de éxito

> ✅ **Eventos descubiertos.** Valentina encuentra 3 conciertos underground de shoegaze esta semana en Medellín a menos de 5 km, con precios dentro de su presupuesto. Toca el que más le interesa para ver detalles completos.

---

---

## Flujo 3: Visualización de Detalle de Evento y Guardado

**Actor:** Valentina Restrepo (usuario autenticado)
**Objetivo:** Evaluar un evento específico, guardarlo en favoritos y compartirlo con amigos.

---

### Pasos

| # | Acción del usuario | Pantalla | Componente clave |
|---|---|---|---|
| 1 | Llega desde Radar, Explorar o notificación | `Detalle de Evento` | Hero image/flyer + info principal (nombre, artista, fecha, hora, venue, precio) |
| 2 | Hace scroll para ver info completa | `Detalle — Sección media` | Lineup completo · descripción · reglas del evento |
| 3 | Revisa ubicación del venue | `Detalle — Mapa inline` | Mapa estático del venue + botón "Cómo llegar" (abre Google Maps / Waze / Apple Maps) |
| 4 | Consulta reseñas de ediciones anteriores | `Detalle — Reseñas` | Rating promedio (estrellas) + lista de reseñas con texto, fecha y avatar |
| 5 | Verifica si amigos asistirán | `Detalle — Social` | Avatares de amigos que van + contador total: *"12 personas van · 3 amigos"* |
| 6 | Toca botón "Guardar / Favorito" (corazón) | `Detalle de Evento` | Icono corazón → animación llenado + haptic feedback + snackbar: *"Guardado en tus favoritos"* |
| 7 | Toca botón "Compartir" | `Detalle — Share sheet` | Sheet nativo: WhatsApp · Instagram Stories · Copiar link · Más opciones |
| 8 | Comparte por WhatsApp a su grupo | `WhatsApp (externo)` | Deep link con preview: imagen + nombre evento + fecha + link a la app |
| 9 | Regresa a la app y decide comprar | `Detalle de Evento` | CTA sticky inferior: "Comprar boleto — desde $35.000" → Flujo 4 |

### Estados de error

| Código | Condición | Pantalla | Comportamiento |
|---|---|---|---|
| `ERR-15` | Evento no encontrado (link roto / eliminado) | `Detalle — Error` | Fullscreen: *"Este evento ya no está disponible"* + ilustración + CTA "Explorar eventos cercanos" |
| `ERR-16` | Falla al guardar en favoritos | `Detalle de Evento` | Icono corazón revierte a vacío + toast: *"No se pudo guardar. Intenta de nuevo."* con retry inline |
| `ERR-17` | Falla al cargar reseñas | `Detalle — Reseñas` | Placeholder: *"No pudimos cargar las reseñas"* + botón "Reintentar". Resto del detalle funcional |
| `ERR-18` | Falla al generar link para compartir | `Detalle — Share sheet` | Toast: *"Error generando el enlace. Intenta de nuevo."* |
| `ERR-19` | Datos del evento incompletos (sin precio publicado) | `Detalle de Evento` | Campo precio: *"Precio por confirmar"* + CTA cambia a "Activar alerta de precio" |
| `ERR-20` | Sin conexión al abrir detalle | `Detalle de Evento` | Si está en caché: muestra datos guardados + banner *"Offline — algunos datos pueden no estar actualizados"*. Si no hay caché → `ERR-15` |

### Estado de éxito

> ✅ **Evento evaluado y guardado.** Valentina revisó toda la información del concierto de shoegaze en el venue "Sala Surterráneo", confirmó que 2 amigos van, lo guardó en favoritos y lo compartió por WhatsApp a su grupo. Procede a comprar boleto.

---

---

## Flujo 4: Compra de Boleto

**Actor:** Valentina Restrepo (usuario autenticado)
**Objetivo:** Comprar un boleto general para el concierto al menor costo posible, con seguridad de que es legítimo.

---

### Pasos

| # | Acción del usuario | Pantalla | Componente clave |
|---|---|---|---|
| 1 | Toca "Comprar boleto" desde Detalle de Evento | `Compra — Selección de boleto` | Tarjetas por tipo: General ($35.000) · VIP ($80.000) · Early Bird (agotado). Badge "Menor comisión" en general |
| 2 | Selecciona tipo "General" | `Compra — Selección de boleto` | Card seleccionada con borde activo + detalle: *qué incluye* |
| 3 | Selecciona cantidad (1 boleto) | `Compra — Cantidad` | Stepper (- 1 +) con límite máximo por transacción + subtotal actualizado en tiempo real |
| 4 | Revisa resumen de compra | `Compra — Resumen` | Desglose: subtotal + comisión de servicio + total. Sección de código promocional (input + "Aplicar") |
| 5 | Ingresa código promocional (opcional) | `Compra — Resumen` | Input: "INDIE2024" → validación → descuento aplicado con tachado en precio original |
| 6 | Selecciona método de pago | `Compra — Método de pago` | Opciones: tarjeta guardada · nueva tarjeta · PSE · Nequi · efectivo (Efecty/Baloto) |
| 7 | Confirma datos de tarjeta (o autentica con Nequi) | `Compra — Datos de pago` | Formulario seguro (PCI compliant): número, vencimiento, CVV + checkbox "Guardar para futuras compras" |
| 8 | Toca "Pagar $33.250" | `Compra — Procesando` | Loader animado: *"Procesando tu pago de forma segura..."* (no permitir back) |
| 9 | Pago exitoso | `Compra — Confirmación` | ✅ Animación de éxito + resumen + boleto digital con QR + opciones post-compra |
| 10 | Descarga / guarda boleto | `Compra — Confirmación` | Botones: "Agregar a Apple Wallet" · "Guardar en Google Wallet" · "Descargar PDF" |

### Estados de error

| Código | Condición | Pantalla | Comportamiento |
|---|---|---|---|
| `ERR-21` | Tipo de boleto agotado al intentar seleccionar | `Compra — Selección` | Card deshabilitada con badge "Agotado" + CTA "Activar alerta si se liberan boletos" |
| `ERR-22` | Cantidad excede disponibilidad | `Compra — Cantidad` | Stepper bloqueado en máx + tooltip: *"Solo quedan N boletos disponibles"* |
| `ERR-23` | Código promocional inválido/expirado | `Compra — Resumen` | Inline error bajo input: *"Código no válido o expirado"* + campo resaltado en rojo |
| `ERR-24` | Tarjeta rechazada por el banco | `Compra — Datos de pago` | Modal: *"Tu banco rechazó la transacción. Verifica los datos o usa otro método."* + botones "Reintentar" · "Cambiar método" |
| `ERR-25` | Timeout en procesamiento de pago (> 30s) | `Compra — Procesando` | Modal: *"El pago está tardando más de lo normal. No cierres la app."* → tras 60s: *"No pudimos confirmar el pago. Revisa tu email o historial bancario antes de reintentar."* + link a soporte |
| `ERR-26` | Pago duplicado detectado | `Compra — Procesando` | Modal: *"Detectamos un intento de pago previo para este evento. Revisa 'Mis boletos' antes de continuar."* + CTA "Ir a Mis boletos" |
| `ERR-27` | Boletos se agotan durante el checkout (race condition) | `Compra — Procesando` | Modal: *"¡Lo sentimos! Los boletos se agotaron mientras procesábamos tu compra. No se realizó ningún cargo."* + CTA "Ver eventos similares" |
| `ERR-28` | Sesión expirada durante checkout | `Compra — Datos de pago` | Modal: *"Tu sesión expiró por seguridad. Inicia sesión para continuar."* → Login → regresa al resumen con datos preservados |
| `ERR-29` | Falla al generar boleto digital post-pago | `Compra — Confirmación` | Banner: *"Tu pago fue exitoso pero el boleto tardará unos minutos. Lo recibirás por email y en 'Mis boletos'."* |

### Estado de éxito

> ✅ **Compra completada.** Valentina adquirió 1 boleto general a $33.250 COP (con descuento del código INDIE2024, comisión incluida). Recibe boleto digital con QR en la app, lo agrega a Apple Wallet y le llega confirmación por email. El evento aparece automáticamente en su calendario dentro de la app.

---

---

## Flujo 5: Gestión de Eventos Guardados y Notificaciones

**Actor:** Valentina Restrepo (usuario autenticado)
**Objetivo:** Revisar eventos guardados, gestionar sus boletos comprados y recibir alertas relevantes sin perderse conciertos.

---

### Pasos

| # | Acción del usuario | Pantalla | Componente clave |
|---|---|---|---|
| 1 | Navega a su perfil desde tab bar | `Perfil / Mi cuenta` | Avatar, nombre, ciudad, géneros + accesos: Mis boletos · Favoritos · Configuración |
| 2 | Toca "Favoritos" | `Mis Favoritos` | Lista de eventos guardados con cards (imagen, nombre, fecha, venue, estado de disponibilidad) |
| 3 | Filtra favoritos por fecha (próximos primero) | `Mis Favoritos` | Tabs: "Próximos" · "Pasados" + ordenamiento |
| 4 | Ve que un evento guardado tiene alerta de precio | `Mis Favoritos — Card` | Badge: *"⚡ Early bird disponible — quedan 2 días"* |
| 5 | Navega a "Mis Boletos" | `Mis Boletos` | Lista: boletos activos (con QR) arriba · pasados abajo. Card con estado: Activo / Usado / Cancelado |
| 6 | Abre boleto del concierto de shoegaze | `Detalle de Boleto` | QR code grande + info del evento + hora de apertura de puertas + botón "Agregar a calendario" |
| 7 | Agrega al calendario del dispositivo | `Detalle de Boleto` | Permiso calendario → evento creado con dirección + recordatorio 2h antes |
| 8 | Configura preferencias de notificaciones | `Configuración — Notificaciones` | Toggles: nuevos eventos de tus géneros · precios especiales · recordatorios de eventos guardados · amigos que van · artistas seguidos |
| 9 | Recibe push notification 24h antes del evento | `Notificación push (sistema)` | *"🎸 Mañana: [Evento] a las 8PM en Sala Surterráneo. Tu boleto está listo."* → abre `Detalle de Boleto` |
| 10 | Recibe notificación de nuevo evento relevante | `Notificación push (sistema)` | *"Nuevo en Medellín: [Artista de shoegaze] toca este sábado 🎶"* → abre `Detalle de Evento` |

### Estados de error

| Código | Condición | Pantalla | Comportamiento |
|---|---|---|---|
| `ERR-30` | Lista de favoritos vacía | `Mis Favoritos` | Empty state: ilustración + *"Aún no has guardado eventos"* + CTA "Explorar el radar" |
| `ERR-31` | Evento favorito fue cancelado | `Mis Favoritos — Card` | Card con overlay semitransparente + badge "Cancelado" + toast automático: *"Un evento guardado fue cancelado"* + opción "Ver similares" |
| `ERR-32` | Lista de boletos vacía | `Mis Boletos` | Empty state: *"No tienes boletos aún. ¡Tu próximo concierto te espera!"* + CTA "Descubrir eventos" |
| `ERR-33` | QR del boleto no carga (sin conexión) | `Detalle de Boleto` | Muestra QR desde caché local (generado al momento de compra). Si no hay caché: *"Activa tu conexión para mostrar el QR"* + código alfanumérico de respaldo |
| `ERR-34` | Falla al agregar evento al calendario | `Detalle de Boleto` | Toast: *"No se pudo agregar al calendario. Verifica los permisos en Ajustes."* + link a settings |
| `ERR-35` | Notificaciones deshabilitadas a nivel sistema | `Configuración — Notificaciones` | Banner informativo: *"Las notificaciones están desactivadas en tu dispositivo"* + botón "Abrir ajustes del sistema" |
| `ERR-36` | Error cargando historial de boletos | `Mis Boletos` | Skeleton → error: *"No pudimos cargar tus boletos"* + botón "Reintentar". Nota: *"Si compraste recientemente, revisa tu email de confirmación"* |
| `ERR-37` | Evento pasado desaparece de favoritos | `Mis Favoritos — Pasados` | Card en gris con fecha pasada + opción "Dejar reseña" → vincula a sistema de reseñas |

### Estado de éxito

> ✅ **Eventos bajo control.** Valentina tiene 5 eventos en favoritos organizados por fecha, 1 boleto activo con QR accesible offline, recordatorio en su calendario para mañana a las 6PM y notificaciones configuradas para enterarse de nuevos eventos de shoegaze y math rock en Medellín en tiempo real. No se volverá a perder un concierto underground.

---

---

## Mapa de Relación entre Flujos

```
┌──────────────┐     ┌──────────────────┐     ┌──────────────────┐
│   FLUJO 1    │     │     FLUJO 2       │     │     FLUJO 3       │
│  Onboarding  │────▶│  Descubrimiento   │────▶│  Detalle + Guardar│
│              │     │  en el Radar       │     │                   │
└──────────────┘     └──────────────────┘     └────────┬──────────┘
                                                        │
                                              ┌────────▼──────────┐
                                              │     FLUJO 4       │
                                              │  Compra de Boleto  │
                                              └────────┬──────────┘
                                                        │
                                              ┌────────▼──────────┐
                                              │     FLUJO 5       │
                                              │  Favoritos, Boletos│
                                              │  y Notificaciones  │
                                              └───────────────────┘
```

> **Nota sobre la persona:** Todos los flujos están diseñados considerando las frustraciones de Valentina: el Flujo 2 resuelve la información dispersa con un radar centralizado; el Flujo 4 aborda las comisiones abusivas mostrando desglose transparente; los Flujos 2-3 permiten filtrar por géneros nicho; y el Flujo 4 garantiza autenticidad de boletos eliminando la reventa no verificada.