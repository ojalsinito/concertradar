

# ConcertRadar — Flujos Principales de Usuario

---

## Flujo 1: Descubrimiento de Eventos Cercanos

> **Actor:** Valentina Restrepo (melómana underground, Medellín)
> **Objetivo:** Encontrar eventos relevantes cerca de su ubicación que coincidan con sus gustos musicales.
> **Pantalla de entrada:** `1.1 Feed de eventos cercanos`

### Pasos

| # | Acción del usuario | Pantalla | Sistema responde |
|---|---|---|---|
| 1 | Abre la app ConcertRadar | `Splash → 1.1 Feed de eventos cercanos` | Solicita permiso de geolocalización |
| 2 | Concede permiso de ubicación | `1.1 Feed de eventos cercanos` | Detecta coordenadas y carga eventos en radio predeterminado (10 km). Muestra vista dual mapa + lista |
| 3 | Observa el feed y hace scroll vertical por la lista | `1.1 Feed de eventos cercanos` | Carga progresiva (infinite scroll). Cada card muestra: nombre del evento, artista, venue, fecha, distancia, precio desde, género |
| 4 | Aplica filtro por género → selecciona "Post-punk" y "Shoegaze" | `1.3.1 Filtros por género musical` (bottom sheet) | Filtra en tiempo real. Actualiza lista y pines en mapa. Muestra contador de resultados |
| 5 | Aplica filtro por fecha → "Este fin de semana" | `1.3.2 Filtros por fecha` (bottom sheet) | Cruza filtro de género + fecha + ubicación. Actualiza resultados |
| 6 | Toca una card de evento que le interesa | `1.1 → 1.2 Detalle de evento` | Navega al detalle con transición de expansión. Carga info completa del evento |

### Estados de error

| Código | Error | Pantalla | Mensaje / Acción |
|---|---|---|---|
| `E1.1` | **Geolocalización denegada** | `1.1 Feed` | Empty state: "Necesitamos tu ubicación para mostrarte eventos cercanos" + botón "Activar ubicación" + opción "Ingresar ciudad manualmente" |
| `E1.2` | **Sin conexión a internet** | `1.1 Feed` | Banner persistente: "Sin conexión. Mostrando últimos eventos guardados" + caché local si existe |
| `E1.3` | **Sin resultados con filtros activos** | `1.1 Feed` | Empty state contextual: "No hay eventos de Shoegaze este fin de semana cerca de ti" + CTA "Ampliar búsqueda" (sugiere quitar un filtro o ampliar radio) + CTA "Crear alerta" |
| `E1.4` | **GPS impreciso / ubicación genérica** | `1.1 Feed` | Toast: "Ubicación aproximada. Los resultados pueden variar" + opción de ajustar pin en mapa manualmente |
| `E1.5` | **Timeout de carga del feed** | `1.1 Feed` | Skeleton loading → tras 10s: "Algo salió mal al cargar eventos" + botón "Reintentar" |

### Estado de éxito

> ✅ Valentina ve un feed personalizado de 12 eventos underground este fin de semana en Medellín, filtrados por sus géneros favoritos. Identifica un toque de post-punk en un bar a 2.3 km y toca la card para ver más detalles.

---

## Flujo 2: Evaluación de un Evento (Detalle)

> **Actor:** Valentina Restrepo
> **Objetivo:** Obtener toda la información necesaria para decidir si asistir y comprar boleto.
> **Pantalla de entrada:** `1.2 Detalle de evento`

### Pasos

| # | Acción del usuario | Pantalla | Sistema responde |
|---|---|---|---|
| 1 | Visualiza la cabecera del evento | `1.2 Detalle de evento` | Muestra: imagen/video hero, nombre del evento, artista(s), fecha y hora, venue, precio desde, etiquetas de género, contador de asistentes confirmados |
| 2 | Hace scroll para leer descripción y line-up completo | `1.2 Detalle de evento` (sección descripción) | Muestra descripción del evento, line-up con horarios por artista, links a playlists de cada artista (Spotify/Apple Music embed) |
| 3 | Toca "Cómo llegar" en la sección de venue | `1.2.2 Info del venue` | Abre ficha del venue: dirección, mapa interactivo, opciones de transporte (metro, bus, taxi estimado), fotos del lugar, capacidad, accesibilidad |
| 4 | Revisa galería multimedia | `1.2.1 Galería multimedia` | Carousel de fotos/videos de ediciones anteriores o del artista. Playlist embebida del artista |
| 5 | Lee reseñas de asistentes a ediciones anteriores | `1.2.5 Reseñas y asistentes confirmados` | Lista de reseñas con rating, texto y fecha. Avatares de amigos / personas que sigue que asistirán. Contador: "23 personas irán" |
| 6 | Toca botón "Ver boletos" (CTA sticky en footer) | `1.2 → 1.2.3 Selección de boletos` | Navega a pantalla de selección de boletos y precios |

### Estados de error

| Código | Error | Pantalla | Mensaje / Acción |
|---|---|---|---|
| `E2.1` | **Evento cancelado o pospuesto** | `1.2 Detalle de evento` | Banner rojo prominente: "Este evento fue cancelado el [fecha]" o "Pospuesto — nueva fecha: [fecha]". CTA: "Ver política de reembolso" si ya compró |
| `E2.2` | **Evento agotado (sold out)** | `1.2 Detalle de evento` | Badge "AGOTADO" sobre imagen hero. CTA primario cambia a "Unirme a lista de espera" + CTA secundario "Crear alerta para eventos similares" |
| `E2.3` | **Contenido multimedia no disponible** | `1.2.1 Galería multimedia` | Placeholder: "Contenido no disponible temporalmente" con ícono ilustrativo. No bloquea el flujo |
| `E2.4` | **Venue sin información de transporte** | `1.2.2 Info del venue` | Muestra solo mapa + dirección. Enlace a Google/Apple Maps como fallback: "Abrir en Maps para indicaciones" |
| `E2.5` | **Detalle no carga (error de servidor)** | `1.2 Detalle de evento` | Full-screen error: "No pudimos cargar este evento" + "Reintentar" + "Volver al feed" |

### Estado de éxito

> ✅ Valentina revisó el line-up, escuchó 3 canciones del artista principal desde el detalle, vio que 5 personas que sigue irán, confirmó que el venue está a 15 min en metro y el cover es $35.000 COP. Toca "Ver boletos" con intención de compra.

---

## Flujo 3: Compra de Boletos

> **Actor:** Valentina Restrepo
> **Objetivo:** Comprar un boleto de forma segura sin salir de la app, evitando revendedores.
> **Pantalla de entrada:** `1.2.3 Selección de boletos y precios`

### Pasos

| # | Acción del usuario | Pantalla | Sistema responde |
|---|---|---|---|
| 1 | Visualiza opciones de boletos disponibles | `1.2.3 Selección de boletos` | Lista de tipos de boleto: General ($35.000), Early Bird ($25.000 — tachado/agotado), VIP ($80.000). Cada uno muestra: precio, beneficios, disponibilidad restante ("quedan 14") |
| 2 | Selecciona "General" y cantidad: 2 boletos | `1.2.3 Selección de boletos` | Actualiza resumen: 2× General = $70.000. Muestra fee de servicio: $4.200. **Total: $74.200 COP**. Timer de reserva inicia (10 min) |
| 3 | Toca "Continuar al pago" | `Checkout — Datos del comprador` | Formulario: nombre, email, teléfono. Si hay sesión activa, pre-rellena datos. Checkbox: "El segundo boleto es para otra persona" → campo de nombre/email adicional |
| 4 | Completa datos y toca "Ir al pago" | `Checkout — Método de pago` | Opciones: tarjeta crédito/débito (formulario inline), PSE (redirect), Nequi/Daviplata (deep link), efectivo en punto físico. Tarjetas guardadas si las hay |
| 5 | Selecciona Nequi → confirma en la app de Nequi | `Checkout — Procesando pago` (loading state) | Muestra spinner con "Procesando tu pago…" + "No cierres la app". Deep link a Nequi para autorización. Escucha webhook de confirmación |
| 6 | Pago confirmado | `Checkout — Confirmación` | Pantalla de éxito con confetti/animación. Muestra: código QR del boleto, resumen de compra, botón "Agregar al calendario", botón "Compartir con amigos", botón "Ver mis boletos" |

### Estados de error

| Código | Error | Pantalla | Mensaje / Acción |
|---|---|---|---|
| `E3.1` | **Timer de reserva expirado** | `Checkout (cualquier paso)` | Modal: "Tu reserva expiró. Los boletos fueron liberados" + CTA "Volver a seleccionar boletos" (regresa a `1.2.3`). Si aún hay disponibilidad, mantiene la selección previa |
| `E3.2` | **Boletos agotados durante el checkout** | `Checkout — Procesando pago` | Modal: "¡Lo sentimos! Los boletos General se agotaron mientras completabas la compra" + "Unirme a lista de espera" + "Ver otros tipos de boleto" (si hay VIP disponible) |
| `E3.3` | **Pago rechazado por el banco** | `Checkout — Método de pago` | Inline error: "Tu banco rechazó la transacción. Verifica tus datos o intenta con otro método de pago" + opciones alternativas visibles. No pierde la reserva (timer sigue) |
| `E3.4` | **Timeout del procesador de pago** | `Checkout — Procesando pago` | Tras 60s: "No pudimos confirmar tu pago. **No se realizó ningún cobro.**" + "Reintentar" + "Contactar soporte" + ID de referencia para seguimiento |
| `E3.5` | **Pago duplicado detectado** | `Checkout — Confirmación` | "Detectamos un posible cobro duplicado. Tu compra fue registrada correctamente. Si ves un cobro extra, será revertido en 24-48h" + enlace a soporte |
| `E3.6` | **Límite de boletos por persona excedido** | `1.2.3 Selección de boletos` | Inline: "Máximo 4 boletos por persona para este evento" + selector bloqueado en 4 |
| `E3.7` | **Sesión expirada / no autenticado** | `Checkout — Datos del comprador` | Modal: "Inicia sesión para continuar tu compra" + login/registro rápido. Al autenticarse, retorna al checkout con selección preservada |

### Estado de éxito

> ✅ Valentina compró 2 boletos generales por $74.200 COP vía Nequi en menos de 2 minutos. Recibió su código QR instantáneamente, agregó el evento a Google Calendar y compartió el segundo boleto por WhatsApp a su amiga. Compra registrada en `Mis Boletos`.

---

## Flujo 4: Búsqueda de Artista o Evento Específico

> **Actor:** Valentina Restrepo
> **Objetivo:** Encontrar si un artista específico tiene fechas próximas en su ciudad o en ciudades cercanas.
> **Pantalla de entrada:** `2.1 Barra de búsqueda global`

### Pasos

| # | Acción del usuario | Pantalla | Sistema responde |
|---|---|---|---|
| 1 | Toca el tab "Búsqueda" en la barra de navegación | `2.1 Búsqueda` | Muestra barra de búsqueda con foco automático (teclado abierto) + búsquedas recientes + sugerencias trending en su ciudad |
| 2 | Escribe "Divino Niño" (banda indie) | `2.1 Búsqueda` (con resultados en vivo) | Autocomplete muestra sugerencias agrupadas: **Artistas** → "Divino Niño", **Eventos** → "Divino Niño en Bar X — 15 dic", **Venues** → ninguno. Resultados aparecen tras 2 caracteres con debounce de 300ms |
| 3 | Toca el resultado del artista "Divino Niño" | `Perfil de artista` (dentro de `2.2 Resultados`) | Página del artista: bio, géneros, foto, playlist embebida, lista de próximos eventos ordenados por fecha. Muestra eventos en Medellín primero (por proximidad) + otras ciudades |
| 4 | Ve que hay un evento el 15 de diciembre en Medellín | `Perfil de artista → lista de eventos` | Card del evento con: fecha, venue, precio desde, disponibilidad. CTA "Ver detalle" |
| 5 | Toca "Ver detalle" en el evento del 15 dic | `Perfil de artista → 1.2 Detalle de evento` | Navega al detalle de evento completo (misma pantalla que Flujo 2). Breadcrumb/back navega a perfil de artista |
| 6 | Toca ♡ "Seguir artista" (acción secundaria en perfil) | `Perfil de artista` | Artista agregado a favoritos. Confirmación: "Te notificaremos cuando Divino Niño tenga nuevas fechas cerca de ti" |

### Estados de error

| Código | Error | Pantalla | Mensaje / Acción |
|---|---|---|---|
| `E4.1` | **Sin resultados para la búsqueda** | `2.2 Resultados de búsqueda` | Empty state: "No encontramos resultados para 'Dvino Niño'" + **"¿Quisiste decir 'Divino Niño'?"** (corrección ortográfica) + "Sugerir que agreguemos este artista" (formulario) |
| `E4.2` | **Artista existe pero sin eventos próximos** | `Perfil de artista` | Sección de eventos: "Divino Niño no tiene eventos programados por ahora" + CTA prominente "Seguir artista para recibir alertas" + sección "Artistas similares con eventos próximos" |
| `E4.3` | **Artista sin eventos en la ciudad del usuario** | `Perfil de artista` | "No hay eventos en Medellín" + lista de eventos en otras ciudades con distancia. Toggle "Notificarme si viene a Medellín" |
| `E4.4` | **Error de conexión durante búsqueda** | `2.1 Búsqueda` | Debajo de la barra: "No pudimos buscar. Revisa tu conexión" + muestra búsquedas recientes como fallback |
| `E4.5` | **Búsqueda vacía (campo sin texto)** | `2.1 Búsqueda` | Muestra: búsquedas recientes, artistas seguidos con eventos nuevos, trending en la ciudad. No es un error, es un estado de oportunidad |

### Estado de éxito

> ✅ Valentina encontró que Divino Niño toca el 15 de diciembre en un bar de Medellín, siguió al artista para futuras alertas, y navegó directamente al detalle del evento para evaluar la compra.

---

## Flujo 5: Gestión de Boletos y Acceso al Evento

> **Actor:** Valentina Restrepo
> **Objetivo:** Acceder a sus boletos comprados el día del evento para ingresar al venue.
> **Pantalla de entrada:** `Mis Boletos` (tab en navegación principal o sección de perfil)

### Pasos

| # | Acción del usuario | Pantalla | Sistema responde |
|---|---|---|---|
| 1 | Toca tab "Mis Boletos" el día del evento | `Mis Boletos` (lista) | Muestra boletos organizados: **Próximos** (ordenados por fecha, el más cercano arriba) y **Pasados** (historial). El boleto de hoy tiene badge "HOY" con highlight visual |
| 2 | Toca el boleto del evento de hoy | `Detalle de boleto` | Muestra: código QR grande y luminoso (brillo de pantalla al máximo automáticamente), nombre del evento, fecha/hora, venue, tipo de boleto, nombre del asistente, número de orden |
| 3 | Activa "Modo presentación" (opcional) | `Detalle de boleto — Modo QR` | Pantalla fullscreen con QR, fondo oscuro, brillo máximo bloqueado, sin timeout de pantalla. Optimizado para escaneo rápido en la puerta |
| 4 | Personal del venue escanea el QR | `Detalle de boleto` | El QR se valida server-side. El boleto cambia a estado "✓ Utilizado" con timestamp. Animación de check verde |
| 5 | Toca "Cómo llegar" (shortcut en el boleto) | `Detalle de boleto → 1.2.2 Info del venue` | Abre ficha del venue con navegación (mismo componente que Flujo 2, paso 3) |
| 6 | Después del evento, recibe prompt de reseña | `Notificación push → Escribir reseña` (al día siguiente) | "¿Cómo estuvo Divino Niño anoche?" → Rating (1-5) + texto opcional + ¿Lo recomendarías? → Publica en `1.2.5 Reseñas` |

### Estados de error

| Código | Error | Pantalla | Mensaje / Acción |
|---|---|---|---|
| `E5.1` | **Sin conexión en el venue (QR offline)** | `Detalle de boleto` | El QR se genera y **cachea localmente** al momento de la compra. Banner: "Estás offline, pero tu boleto está disponible" — funcionalidad completa sin internet |
| `E5.2` | **QR ya fue escaneado (duplicado)** | `Detalle de boleto` | Estado cambia a "⚠️ Este boleto ya fue utilizado a las [hora]". Si el usuario cree que es un error: botón "Reportar problema" → chat con soporte + ID de transacción |
| `E5.3` | **Boleto transferido y ya no pertenece al usuario** | `Mis Boletos` | El boleto desaparece de "Próximos". Si busca acceder por deep link: "Este boleto fue transferido a [nombre] el [fecha]" + "Contactar soporte" |
| `E5.4` | **Evento cancelado después de la compra** | `Mis Boletos → Detalle de boleto` | Badge rojo "CANCELADO". Info: "Este evento fue cancelado. Tu reembolso de $74.200 será procesado en 5-10 días hábiles al método de pago original" + estado del reembolso (pendiente/procesado/completado) |
| `E5.5` | **App no instalada / sesión cerrada el día del evento** | `Fuera de la app` | Email de recordatorio 4h antes con: enlace al boleto web (fallback sin app), instrucciones para re-descargar, PDF adjunto con QR como último recurso |
| `E5.6` | **Brillo de pantalla bajo impide escaneo** | `Detalle de boleto — Modo QR` | Auto-detecta brillo bajo: "Subimos el brillo para facilitar el escaneo" (ajuste automático con permiso) + botón manual "Maximizar brillo" |

### Estado de éxito

> ✅ Valentina llegó al venue, abrió la app, su boleto de hoy estaba destacado como primero en la lista. Activó modo presentación, el staff escaneó su QR en 2 segundos, ingresó sin problemas. Al día siguiente, dejó una reseña de 5 estrellas que ayudará a otros usuarios a descubrir el evento en futuras ediciones.

---

## Resumen de cobertura

| Flujo | Loop del usuario | Pantallas MVP tocadas | Errores definidos |
|---|---|---|---|
| **1. Descubrimiento** | Descubrir | `1.1` `1.3.1` `1.3.2` | 5 |
| **2. Evaluación** | Evaluar | `1.2` `1.2.1` `1.2.2` `1.2.5` | 5 |
| **3. Compra** | Comprar | `1.2.3` `Checkout ×4` | 7 |
| **4. Búsqueda** | Descubrir (dirigido) | `2.1` `2.2` `Perfil artista` | 5 |
| **5. Acceso** | Asistir + Redescubrir | `Mis Boletos` `Detalle boleto` `Reseña` | 6 |
| | | **Total: 16 pantallas únicas** | **28 estados de error** |

> **Nota de diseño:** Todos los estados de error siguen el principio de **recuperación asistida** — ningún error es un callejón sin salida. Cada uno ofrece al menos una acción concreta para que el usuario avance o resuelva el problema.