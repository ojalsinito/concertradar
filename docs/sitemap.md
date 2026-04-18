

# ConcertRadar — Sitemap Completo

---

## Principios de organización

| Criterio | Decisión |
|---|---|
| **Modelo mental del usuario** | Flujo circular: Descubrir → Evaluar → Comprar → Asistir → Redescubrir |
| **Navegación principal** | Tab bar con 5 secciones raíz (patrón estándar móvil) |
| **Criterio MVP (⭐)** | Pantallas necesarias para cerrar el loop mínimo: descubrir un evento cercano y comprar boleto |
| **Profundidad máxima** | 2 niveles desde cualquier tab (regla de 3 taps al contenido) |

---

## Mapa del sitio

### 1. Explorar (Tab principal — Home)

- ⭐ 1.1 Feed de eventos cercanos (mapa + lista, geolocalización automática)
- ⭐ 1.2 Detalle de evento
  - 1.2.1 Galería multimedia (fotos, videos, playlist)
  - ⭐ 1.2.2 Info del venue (ubicación, capacidad, cómo llegar)
  - ⭐ 1.2.3 Selección de boletos y precios
  - 1.2.4 Eventos relacionados ("Si te gusta esto…")
  - 1.2.5 Reseñas y asistentes confirmados
- ⭐ 1.3 Filtros y ordenamiento
  - ⭐ 1.3.1 Por género musical (incluyendo subgéneros underground)
  - ⭐ 1.3.2 Por fecha / rango de fechas
  - ⭐ 1.3.3 Por distancia / zona
  - 1.3.4 Por rango de precio
  - 1.3.5 Por tipo de venue (bar, arena, centro cultural, casa de conciertos)
- 1.4 Vista de mapa expandido (exploración geográfica)

---

### 2. Búsqueda

- ⭐ 2.1 Barra de búsqueda global (artistas, eventos, venues, géneros)
- ⭐ 2.2 Resultados de búsqueda (agrupados por categoría)
- 2.3 Búsquedas recientes y sugeridas
- 2.4 Búsqueda por fecha específica ("¿Qué hay este viernes?")
- ⭐ 2.5 Perfil de artista
  - ⭐ 2.5.1 Próximos eventos del artista
  - 2.5.2 Bio, discografía y links de streaming
  - ⭐ 2.5.3 Botón de seguir artista
- 2.6 Perfil de venue
  - 2.6.1 Calendario del venue
  - 2.6.2 Info práctica (dirección, horarios, políticas)
  - 2.6.3 Fotos y reseñas del lugar

---

### 3. Mis Boletos

- ⭐ 3.1 Boletos activos (próximos eventos)
  - ⭐ 3.1.1 Detalle de boleto (QR / código de entrada)
  - 3.1.2 Agregar a calendario del dispositivo
  - 3.1.3 Compartir boleto / invitar amigos
  - ⭐ 3.1.4 Indicaciones para llegar al venue
- 3.2 Historial de eventos asistidos
  - 3.2.1 Dejar reseña del evento
  - 3.2.2 Ver fotos del evento (post-evento)
- 3.3 Boletos transferidos / recibidos
- ⭐ 3.4 Descargar boleto offline (wallet / PDF)

---

### 4. Para Ti (Personalización)

- ⭐ 4.1 Recomendaciones personalizadas por gustos musicales
- ⭐ 4.2 Alertas de artistas seguidos ("Artista X viene a tu ciudad")
- 4.3 Eventos populares en tu zona
- 4.4 Amigos que asistirán (integración social)
- 4.5 Radar semanal (digest de eventos nuevos para ti)
- 4.6 Descubrimiento por mood / momento ("Algo tranquilo hoy", "Fiesta este sábado")

---

### 5. Perfil y Configuración

- ⭐ 5.1 Mi perfil
  - ⭐ 5.1.1 Datos personales
  - ⭐ 5.1.2 Géneros e intereses musicales (onboarding y edición)
  - 5.1.3 Artistas y venues seguidos
  - 5.1.4 Estadísticas personales (eventos asistidos, géneros, ciudades)
- ⭐ 5.2 Métodos de pago
  - ⭐ 5.2.1 Agregar / editar tarjeta
  - 5.2.2 Otros métodos (PSE, OXXO, Mercado Pago, según país)
- 5.3 Notificaciones
  - 5.3.1 Preferencias de alertas (artistas, precio, cercanía)
  - 5.3.2 Frecuencia y canales (push, email)
- 5.4 Configuración general
  - 5.4.1 Idioma y región
  - 5.4.2 Permisos de ubicación
  - 5.4.3 Privacidad y datos
  - 5.4.4 Tema (claro / oscuro)
- 5.5 Centro de ayuda y soporte
  - 5.5.1 FAQs
  - 5.5.2 Chat de soporte
  - 5.5.3 Reportar un problema con boleto
- 5.6 Legal
  - 5.6.1 Términos y condiciones
  - 5.6.2 Política de privacidad
  - 5.6.3 Política de reembolsos
- ⭐ 5.7 Cerrar sesión / eliminar cuenta

---

### 6. Flujo de Compra (transversal — se accede desde cualquier detalle de evento)

- ⭐ 6.1 Selección de tipo y cantidad de boletos
- ⭐ 6.2 Resumen de orden (desglose de precio + comisión transparente)
- ⭐ 6.3 Selección / confirmación de método de pago
- ⭐ 6.4 Confirmación de compra exitosa
  - ⭐ 6.4.1 Boleto generado (QR)
  - 6.4.2 Compartir compra
  - 6.4.3 Agregar a calendario
- 6.5 Error de pago / reintentar

---

### 7. Onboarding (flujo inicial — una sola vez)

- ⭐ 7.1 Pantallas de bienvenida (propuesta de valor, 3 slides)
- ⭐ 7.2 Registro / Login (email, Google, Apple)
- ⭐ 7.3 Permiso de ubicación
- ⭐ 7.4 Selección de géneros musicales favoritos
- 7.5 Conectar con Spotify / Apple Music (importar gustos)
- 7.6 Seguir artistas sugeridos

---

### 8. Portal de Artistas / Promotores (flujo secundario)

- 8.1 Registro como organizador
- 8.2 Dashboard del organizador
  - 8.2.1 Crear evento
  - 8.2.2 Configurar boletos y precios
  - 8.2.3 Métricas de ventas en tiempo real
  - 8.2.4 Lista de asistentes / check-in
- 8.3 Gestión de perfil de artista / venue
- 8.4 Historial de pagos y liquidaciones
- 8.5 Soporte para organizadores

---

## Resumen cuantitativo

| Métrica | Total | MVP (⭐) |
|---|---|---|
| **Secciones raíz** | 8 | 5 (tabs) + 2 flujos transversales |
| **Pantallas totales** | 68 | 30 |
| **Taps máximos al contenido clave** | 3 | 2 |

---

## Mapa visual de navegación principal

```
┌──────────────────────────────────────────────────┐
│                   Tab Bar                         │
├──────────┬──────────┬──────────┬────────┬────────┤
│ Explorar │ Búsqueda │  Boletos │Para Ti │ Perfil │
│  (Home)  │          │          │        │        │
└────┬─────┴────┬─────┴────┬─────┴───┬────┴───┬────┘
     │          │          │         │        │
     ▼          ▼          ▼         ▼        ▼
   Feed +    Buscar     Boletos   Recos    Config
   Mapa     artista/    activos/  person.  pagos
   Filtros   venue/     historial alertas  gustos
     │       género        │
     ▼                     ▼
  Detalle ──────────► Flujo de ──► Boleto
  Evento               Compra      generado
```

---

> **Nota para diseño:** Las secciones 7 (Onboarding) y 8 (Portal de artistas) viven fuera de la navegación principal por tabs. El onboarding es un flujo lineal pre-autenticación. El portal de artistas es un modo alternativo de la app accesible desde Perfil.