

# ConcertRadar — Flujos Principales de Usuario

**Versión:** 1.0 | **Fecha:** Junio 2025 | **Estado:** Draft
**Persona principal de referencia:** Valentina Rojas, 24 años, CDMX

---

## Flujo 1: Registro y Onboarding de Gustos Musicales

**Actor:** Usuario nuevo (Valentina)
**Objetivo:** Crear cuenta y personalizar el feed desde el primer momento
**Pantallas involucradas:** 1.1 → 1.2 → 1.2.1 → 1.4 → 1.5 → 2.1

---

### Pasos

| # | Acción del usuario | Pantalla | Lógica / Detalle |
|---|---|---|---|
| 1 | Abre la app por primera vez | **1.1 Landing / Welcome** | Se muestran propuesta de valor y CTA: "Crear cuenta" / "Ya tengo cuenta" |
| 2 | Toca "Crear cuenta" y elige método de registro | **1.2 Registro** | Opciones: email, Google, Apple, Facebook |
| 3a | **Si elige email →** completa formulario (nombre, email, contraseña) y toca "Continuar" | **1.2 Registro** | Validación en tiempo real (formato email, contraseña mín. 8 caracteres) |
| 3b | **Si elige social login →** autoriza permisos en modal nativo del proveedor | Modal OS / OAuth | Se pre-llenan nombre y email; salta paso 4 |
| 4 | Recibe código de verificación y lo ingresa | **1.2.1 Verificación** | Código de 6 dígitos por email o SMS. Opción "Reenviar código" tras 60s |
| 5 | Selecciona géneros musicales de interés (mínimo 3) | **1.4 Onboarding de gustos** | Grid visual con géneros. Incluye nichos: shoegaze, post-punk, electrónica experimental. Barra de progreso visible |
| 6 | Selecciona artistas favoritos sugeridos según géneros elegidos (mínimo 3) | **1.4 Onboarding de gustos** | Segundo paso dentro del mismo flujo. Chips con foto + nombre de artista |
| 7 | La app solicita acceso a ubicación | **1.5 Permiso de ubicación** | Pantalla explicativa antes del prompt del sistema: "Para mostrarte conciertos cerca de ti". Opción de "Elegir ciudad manualmente" |
| 8 | Llega al feed personalizado | **2.1 Feed personalizado** | Contenido ya filtrado por gustos + ubicación |

### Estados de error

| Código | Situación | Mensaje mostrado | Pantalla | Acción de recuperación |
|---|---|---|---|---|
| E1.1 | Email ya registrado | "Este correo ya tiene una cuenta. ¿Quieres iniciar sesión?" | 1.2 | Link directo a **1.3 Login** |
| E1.2 | Contraseña no cumple requisitos | "La contraseña debe tener al menos 8 caracteres, una mayúscula y un número" | 1.2 | Validación inline en tiempo real |
| E1.3 | Código de verificación incorrecto | "Código incorrecto. Te quedan [X] intentos" | 1.2.1 | Tras 3 intentos fallidos → reenvío automático de nuevo código |
| E1.4 | Código de verificación expirado | "Este código expiró. Te enviamos uno nuevo" | 1.2.1 | Reenvío automático + nuevo timer de 60s |
| E1.5 | Fallo en autenticación social (Google/Apple/FB) | "No pudimos conectar con [Proveedor]. Intenta de nuevo o usa otro método" | 1.2 | Mostrar métodos alternativos |
| E1.6 | Menos de 3 géneros seleccionados al intentar continuar | "Selecciona al menos 3 géneros para personalizar tu experiencia" | 1.4 | Botón "Continuar" deshabilitado hasta cumplir mínimo |
| E1.7 | Ubicación denegada y no elige ciudad manual | "Sin ubicación no podemos mostrarte conciertos cerca. ¿Quieres elegir tu ciudad?" | 1.5 | Selector manual de ciudad como fallback |
| E1.8 | Sin conexión a internet | "Sin conexión. Conéctate para crear tu cuenta" | Cualquiera | Retry automático al detectar conexión |

### Estado de éxito

> ✅ **Cuenta creada, gustos guardados, ubicación configurada.**
> El usuario llega a **2.1 Feed personalizado** con un toast de bienvenida:
> *"¡Listo, Valentina! Ya estás dentro 🎶 Encontramos [X] conciertos para ti esta semana en CDMX"*

---

## Flujo 2: Descubrimiento y Exploración de Conciertos

**Actor:** Usuario registrado (Valentina)
**Objetivo:** Encontrar conciertos de géneros nicho cercanos que no descubriría en redes sociales
**Pantallas involucradas:** 2.1 → 3.1 / 3.2 → 3.3 → 3.2.1 → 4.1

---

### Pasos

| # | Acción del usuario | Pantalla | Lógica / Detalle |
|---|---|---|---|
| 1 | Desde el Home, toca la pestaña "Explorar" en la navegación principal | **3.1 Mapa interactivo** | Vista mapa por defecto con pins de eventos cercanos. Toggle mapa / lista visible |
| 2a | **Ruta Mapa →** Navega por el mapa, hace zoom en su zona (Roma/Condesa, CDMX) y toca un pin | **3.1 Mapa interactivo** | El pin se expande en preview card: nombre, artista, fecha, precio, distancia |
| 2b | **Ruta Búsqueda →** Toca la barra de búsqueda y escribe "shoegaze" | **3.2 Búsqueda** | Sugerencias en tiempo real: por género, artistas, venues que coincidan |
| 3 | Aplica filtros avanzados para refinar resultados | **3.3 Filtros avanzados** | Filtros: género (shoegaze ✓), fecha (este mes), precio (< $500 MXN), distancia (< 10km), tipo (underground ✓). Contador de resultados en tiempo real |
| 4 | Revisa listado de resultados filtrados | **3.2.1 Resultados** | Cards de eventos con: cartel, artista, venue, fecha, precio, tag "underground" / etiquetas de género. Ordenar por: fecha, distancia, precio, popularidad |
| 5 | Toca un evento que le interesa | **4.1 Detalle de evento** | Información completa: cartel, artista, fecha/hora, venue, precio, descripción, lineup, tags de género |
| 6 | Explora la info del venue | **4.2 Info del venue** | Mapa embebido, dirección, capacidad, indicaciones de transporte, fotos del lugar |

### Estados de error

| Código | Situación | Mensaje mostrado | Pantalla | Acción de recuperación |
|---|---|---|---|---|
| E2.1 | Búsqueda sin resultados | "No encontramos eventos para 'shoegaze' en tu zona. Prueba ampliando la distancia o cambiando filtros" | 3.2.1 | Sugerencias: ampliar radio, quitar filtros, explorar géneros similares (post-punk, dream pop) |
| E2.2 | Mapa no carga (sin GPS o fallo de servicio) | "No pudimos cargar el mapa. Verifica tu ubicación o prueba la vista de lista" | 3.1 | Toggle automático a vista lista + botón reintentar mapa |
| E2.3 | Filtros demasiado restrictivos → 0 resultados | "0 eventos con estos filtros. Relaja alguno para ver más opciones" | 3.3 | Highlight de filtros más restrictivos + sugerencia de cuáles ampliar |
| E2.4 | Evento ya no disponible (cancelado/pasado) al tocar card | "Este evento ya no está disponible" | 4.1 | Mostrar eventos similares: "También te puede gustar..." |
| E2.5 | Error de carga del detalle del evento | "No pudimos cargar este evento. Intenta de nuevo" | 4.1 | Botón retry + caché de datos parciales si se cargó previamente |
| E2.6 | Ubicación desactualizada o imprecisa | "Tu ubicación parece imprecisa. ¿Quieres actualizarla?" | 3.1 | Prompt para reactivar GPS o seleccionar zona manualmente |

### Estado de éxito

> ✅ **Concierto descubierto.**
> Valentina encuentra un evento de shoegaze en un foro a 2km que no había visto en redes.
> Está en **4.1 Detalle de evento** con toda la información visible y CTAs claros:
> *"Comprar boleto" / "Guardar" / "Compartir" / "Me interesa"*

---

## Flujo 3: Compra de Boletos (Segura y sin Reventa)

**Actor:** Usuario registrado (Valentina)
**Objetivo:** Comprar un boleto de forma segura, sin comisiones abusivas ni riesgo de fraude
**Pantallas involucradas:** 4.1 → 4.3 → 4.4 → 4.5 → 4.6 → 5.1

> **Nota:** Las pantallas 4.3–4.6 se infieren del sitemap como parte del flujo de compra dentro de "Detalle de Evento"

---

### Pasos

| # | Acción del usuario | Pantalla | Lógica / Detalle |
|---|---|---|---|
| 1 | Desde el detalle del evento, toca "Comprar boleto" | **4.1 Detalle de evento** | Se muestra precio + desglose de comisión transparente antes de iniciar compra |
| 2 | Selecciona tipo y cantidad de boletos | **4.3 Selección de boletos** | Tipos: General, VIP, Early Bird (si aplica). Máximo 4 por persona (control anti-reventa). Muestra disponibilidad en tiempo real |
| 3 | Revisa resumen de compra con desglose de costos | **4.4 Resumen de compra** | Subtotal + comisión de servicio (transparente y desglosada) + total. Política de reembolso visible. Campo para código promocional |
| 4 | Selecciona o agrega método de pago | **4.5 Método de pago** | Opciones: tarjeta débito/crédito, OXXO/efectivo, Apple Pay, Google Pay. Tarjetas guardadas de compras anteriores |
| 5 | Confirma la compra (autenticación biométrica o PIN) | **4.5 Método de pago** | Verificación 3D Secure para tarjetas si aplica. Confirmación biométrica (FaceID/TouchID) como segundo factor |
| 6 | Ve pantalla de confirmación con boleto digital | **4.6 Confirmación de compra** | Animación de éxito. Boleto con QR único vinculado a su cuenta (intransferible, anti-reventa). Opción: "Agregar al calendario", "Compartir que voy" |
| 7 | El boleto aparece en su sección de boletos | **5.1 Mis boletos** | Boleto guardado con countdown al evento, QR para entrada, info del venue |

### Estados de error

| Código | Situación | Mensaje mostrado | Pantalla | Acción de recuperación |
|---|---|---|---|---|
| E3.1 | Boletos agotados al intentar comprar | "¡Se agotaron! Activa la alerta y te avisamos si se liberan lugares" | 4.3 | CTA: "Activar alerta de disponibilidad" + mostrar eventos similares |
| E3.2 | Boletos agotados durante el proceso (race condition) | "Alguien más compró los últimos boletos mientras completabas. Lo sentimos" | 4.4 / 4.5 | Misma recuperación que E3.1 + no se realiza cobro |
| E3.3 | Pago rechazado por la institución bancaria | "Tu banco rechazó el pago. Verifica tus fondos o prueba con otro método" | 4.5 | Opciones: reintentar, cambiar método de pago, pagar en efectivo (OXXO) |
| E3.4 | Error en 3D Secure / autenticación fallida | "No pudimos verificar tu identidad con el banco. Intenta de nuevo" | 4.5 | Retry de autenticación + sugerencia de otro método |
| E3.5 | Timeout de pago (conexión lenta) | "La conexión tardó demasiado. Tu tarjeta NO fue cobrada. Intenta de nuevo" | 4.5 | Verificación automática de cobro duplicado antes de permitir retry |
| E3.6 | Límite de boletos por persona alcanzado | "Máximo 4 boletos por cuenta para proteger contra la reventa" | 4.3 | Mensaje informativo sobre política anti-reventa |
| E3.7 | Código promocional inválido o expirado | "Este código no es válido o ya expiró" | 4.4 | Campo se limpia con shake animation, se puede reintentar |
| E3.8 | Evento cancelado post-compra (caso edge) | "El evento fue cancelado. Tu reembolso completo se procesará en 5-10 días hábiles" | Push notification + 5.1 | Reembolso automático + sugerencia de eventos alternativos |

### Estado de éxito

> ✅ **Boleto comprado de forma segura.**
> Valentina ve la confirmación con su boleto digital QR vinculado a su cuenta.
> *"¡Listo! Tu boleto para [Artista] en [Venue] el [Fecha] está seguro 🎫"*
> Acciones post-compra: Agregar a calendario (Google/Apple) · Compartir en redes · Ver en Mis Boletos
> **Comisión transparente:** Valentina vio exactamente cuánto fue servicio vs. precio del artista.

---

## Flujo 4: Guardar Evento y Recibir Alertas

**Actor:** Usuario registrado (Valentina)
**Objetivo:** No perderse un concierto que le interesa — resolver su frustración de enterarse tarde por stories efímeras
**Pantallas involucradas:** 4.1 → 5.2 → Push Notification → 4.1

> **Nota:** La pantalla 5.2 se infiere como "Mis eventos guardados / Favoritos" dentro de la sección de perfil/actividad

---

### Pasos

| # | Acción del usuario | Pantalla | Lógica / Detalle |
|---|---|---|---|
| 1 | Desde el detalle de un evento, toca el ícono "Guardar" (bookmark) | **4.1 Detalle de evento** | Micro-interacción: ícono se llena con animación. Toast: "Evento guardado ✓". También puede tocar "Me interesa" para señal social |
| 2 | El sistema le pregunta qué alertas quiere activar | **4.1 Detalle de evento** (bottom sheet) | Opciones: "Avísame cuando salgan boletos" · "Recordatorio 1 semana antes" · "Recordatorio 1 día antes" · "Últimos boletos disponibles" · Todas activadas por defecto |
| 3 | Valentina personaliza sus alertas y confirma | **4.1 Detalle de evento** (bottom sheet) | Selección guardada. Badge de campana visible en el evento |
| 4 | Accede a su lista de eventos guardados desde el perfil | **5.2 Mis eventos guardados** | Lista organizada cronológicamente con tabs: "Próximos" / "Pasados". Cada card muestra: countdown, estado (boletos disponibles / agotados / último día), acceso rápido a compra |
| 5 | Recibe push notification según configuración | **Push notification** | Ej: "🎶 ¡Boletos a la venta! [Artista] en [Venue] — Los primeros 100 tienen 20% off" |
| 6 | Toca la notificación y llega directo a compra | **4.1 Detalle de evento** | Deep link directo al evento con CTA de compra prominente |

### Estados de error

| Código | Situación | Mensaje mostrado | Pantalla | Acción de recuperación |
|---|---|---|---|---|
| E4.1 | Notificaciones push desactivadas en el sistema | "Activa las notificaciones para no perderte este concierto" | 4.1 (bottom sheet) | Botón que abre Settings del OS directamente. Alternativa: "Enviar recordatorio por email" |
| E4.2 | Evento cancelado después de guardarlo | "El evento [Nombre] fue cancelado por el organizador" | Push + 5.2 | Notificación + badge en eventos guardados + sugerencias de eventos similares |
| E4.3 | Evento cambió de fecha/hora/venue | "¡Atención! [Evento] cambió al [nueva fecha] en [nuevo venue]" | Push + 5.2 | Notificación clara con cambios resaltados + opción de "Ya no me interesa" |
| E4.4 | Error al guardar (fallo de red) | "No pudimos guardar. ¿Intentamos de nuevo?" | 4.1 | Retry automático cuando se recupere conexión + cola offline |
| E4.5 | Push entregada tarde (boletos ya agotados al abrir) | "Los boletos se agotaron, pero activamos la alerta de disponibilidad automáticamente" | 4.1 | Waitlist automática + mostrar eventos similares |

### Estado de éxito

> ✅ **Evento guardado con alertas activas.**
> Valentina nunca más se pierde un concierto por enterarse tarde.
> En **5.2 Mis eventos guardados** ve su lista curada con countdowns.
> *"Tienes 3 conciertos guardados este mes. ¡El de [Artista] es en 2 días!"*
> **Problema resuelto:** Ya no depende de stories efímeras de Instagram para enterarse.

---

## Flujo 5: Búsqueda por Mapa y Filtro de Género Nicho

**Actor:** Usuario registrado (Valentina)
**Objetivo:** Encontrar conciertos underground de géneros específicos (shoegaze, post-punk) en su zona geográfica exacta
**Pantallas involucradas:** 2.1 → 3.1 → 3.3 → 3.2.1 → 4.1 → 4.2

> **Justificación:** Este flujo aborda directamente la frustración #3 de Valentina: *"No existe un solo lugar donde pueda filtrar eventos por género específico como shoegaze, post-punk o electrónica experimental en su zona"*

---

### Pasos

| # | Acción del usuario | Pantalla | Lógica / Detalle |
|---|---|---|---|
| 1 | Desde Home, toca "Explorar" en la barra de navegación | **3.1 Mapa interactivo** | Mapa centrado en su ubicación actual (Roma Norte, CDMX). Pins de colores por género. Leyenda de colores visible |
| 2 | Toca el botón de filtros (ícono sliders) sobre el mapa | **3.3 Filtros avanzados** (overlay/modal) | Panel de filtros se desliza desde abajo sobre el mapa |
| 3 | En "Género", despliega la categoría y selecciona géneros nicho | **3.3 Filtros avanzados** | Taxonomía jerárquica: Rock → Post-punk ✓, Shoegaze ✓ · Electrónica → Experimental ✓. Chips seleccionables. Contador actualiza: "12 eventos encontrados" |
| 4 | En "Tipo", selecciona "Underground" | **3.3 Filtros avanzados** | Toggle: Mainstream / Underground / Todos. Selecciona Underground |
| 5 | Ajusta rango de distancia con slider (ej: 15 km) | **3.3 Filtros avanzados** | Slider visual con radio reflejado en el mapa en tiempo real (círculo que se expande/contrae) |
| 6 | Ajusta rango de precio (ej: $0 – $500 MXN) | **3.3 Filtros avanzados** | Slider dual (min-max). Aborda frustración de comisiones excesivas al ver precio final |
| 7 | Toca "Aplicar filtros" | **3.3 → 3.1 Mapa actualizado** | El mapa se actualiza mostrando solo los pins que coinciden. Transición animada. Chips de filtros activos visibles arriba del mapa para edición rápida |
| 8 | Alterna a vista lista para comparar eventos | **3.2.1 Resultados** | Toggle mapa ↔ lista. Cards con: nombre, artista, venue, fecha, precio final, distancia, tags (shoegaze, underground). Ordenar por: fecha / distancia / precio |
| 9 | Toca un evento que le interesa | **4.1 Detalle de evento** | Tags de género visibles y prominentes. Sección "Artistas similares con eventos próximos" |
| 10 | Revisa cómo llegar al venue | **4.2 Info del venue** | Mapa con ruta desde su ubicación, opciones de transporte (Metro, Uber, bici), fotos del lugar, reseñas de asistentes |

### Estados de error

| Código | Situación | Mensaje mostrado | Pantalla | Acción de recuperación |
|---|---|---|---|---|
| E5.1 | Sin resultados para combinación de filtros nicho | "No hay eventos de shoegaze + post-punk underground en 15 km este mes" | 3.1 / 3.2.1 | Sugerencias inteligentes: "Amplía a 30 km → 3 resultados" · "Incluye dream pop → 5 resultados" · "Activa alerta para este filtro" |
| E5.2 | GPS impreciso, mapa muestra zona incorrecta | "Te estamos ubicando en [zona]. ¿Es correcto?" | 3.1 | Opción de recentrar manualmente con búsqueda de dirección o barrio |
| E5.3 | Mapa no renderiza (fallo del servicio de mapas) | "El mapa no está disponible. Usa la vista de lista mientras tanto" | 3.1 | Fallback automático a vista lista con distancias calculadas. Retry silencioso del mapa |
| E5.4 | Filtro de género no tiene eventos en la plataforma aún | "Aún no tenemos eventos de 'noise' en CDMX. ¡Ayúdanos a crecer!" | 3.2.1 | CTA: "Sugerir un evento" + "Activar alerta cuando haya eventos de noise" |
| E5.5 | Carga lenta de resultados en mapa (muchos pins) | Skeleton loading en pins + "Cargando eventos..." | 3.1 | Carga progresiva: primero los más cercanos, luego el resto. Clustering de pins en zoom out |
| E5.6 | Venue sin información de transporte | "Aún no tenemos info de cómo llegar. Aquí está la dirección para tu GPS" | 4.2 | Dirección copyable + botón "Abrir en Google Maps / Waze / Apple Maps" |

### Estado de éxito

> ✅ **Conciertos nicho descubiertos en su zona.**
> Valentina tiene una vista filtrada de **12 eventos de shoegaze y post-punk underground** en un radio de 15 km en CDMX, todos dentro de su presupuesto.
> El mapa muestra pins claros y la lista permite comparar rápidamente.
> *"Encontramos 12 eventos de shoegaze, post-punk y electrónica experimental cerca de ti 🎯"*
>
> **Problema resuelto:** Por primera vez, Valentina tiene un lugar centralizado para descubrir eventos de sus géneros nicho sin depender de stories de Instagram ni algoritmos genéricos.

---

## Resumen de Cobertura

| Flujo | Frustración de Valentina que resuelve | Pantallas MVP utilizadas |
|---|---|---|
| **F1 — Registro y Onboarding** | Base para personalización por gustos nicho | 1.1, 1.2, 1.2.1, 1.4, 1.5, 2.1 |
| **F2 — Descubrimiento** | No existe un lugar para descubrir eventos underground | 2.1, 3.1, 3.2, 3.2.1, 3.3, 4.1, 4.2 |
| **F3 — Compra segura** | Comisiones abusivas + fraude en reventa | 4.1, 4.3–4.6, 5.1 |
| **F4 — Guardar + Alertas** | Se entera tarde por stories efímeras | 4.1, 5.2, Push |
| **F5 — Mapa + Filtro nicho** | No puede filtrar por género específico en su zona | 3.1, 3.2.1, 3.3, 4.1, 4.2 |

> **Total de estados de error documentados:** 33
> **Cobertura de pantallas MVP (⭐):** 100% de las pantallas marcadas como MVP aparecen en al menos un flujo