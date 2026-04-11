

# ConcertRadar — Brief de Producto

**Versión:** 1.0
**Fecha:** Junio 2025
**Autor:** Product Management
**Estado:** Draft para validación con stakeholders

---

## 1. Problema

### Problema principal

En Latinoamérica, descubrir conciertos —especialmente de la escena underground y artistas independientes locales— es una experiencia fragmentada, frustrante e ineficiente. Los usuarios dependen de múltiples fuentes desconectadas (Instagram, grupos de WhatsApp, carteles físicos, boca a boca) para enterarse de eventos cercanos, y cuando los encuentran, la compra de boletos pasa por intermediarios que cobran comisiones excesivas (15-30%) que encarecen el precio final y perjudican económicamente al artista independiente.

### Problemas secundarios

| # | Problema | Quién lo sufre | Impacto |
|---|----------|----------------|---------|
| 1 | **Descubrimiento fragmentado:** No existe un punto único que consolide la oferta de conciertos mainstream *y* underground por ubicación geográfica. | Fan / Asistente | Pierde eventos que le interesarían; se entera tarde o nunca. |
| 2 | **Comisiones abusivas en ticketing:** Plataformas como Ticketmaster cobran service fees de hasta 30%, sin transparencia. | Fan + Artista independiente | El fan paga de más; el artista recibe menos. |
| 3 | **Invisibilidad de la escena local:** Artistas y venues underground no tienen herramientas accesibles para promocionar y vender boletos de forma profesional. | Artista independiente / Venue pequeño | Baja asistencia, ingresos limitados, crecimiento lento de audiencia. |
| 4 | **Falta de personalización:** Las plataformas existentes no filtran por gustos musicales reales del usuario ni priorizan proximidad geográfica de forma inteligente. | Fan / Asistente | Ruido informativo; fatiga de búsqueda. |
| 5 | **Desconfianza en la reventa:** Boletos falsos y reventa informal generan fraude y desconfianza. | Fan / Asistente | Pérdida de dinero, mala experiencia. |

### Validación del problema

- El mercado de ticketing en Latinoamérica está en crecimiento sostenido, con Brasil (~40%) y México (~25%) liderando en cuota regional.
- Ticketmaster enfrenta competencia creciente de Etix, Eventbrite y Tixr, lo que demuestra demanda insatisfecha.
- No existe un competidor regional enfocado simultáneamente en **descubrimiento geolocalizado + escena underground + venta directa sin intermediarios**.

---

## 2. Solución

**ConcertRadar** es una app móvil (iOS + Android) que combina descubrimiento inteligente de conciertos por geolocalización y gustos musicales con un sistema de compra directa de boletos que elimina intermediarios para artistas independientes.

### Modelo conceptual

```
┌─────────────────────────────────────────────────────┐
│                    CONCERTRADAR                      │
│                                                      │
│  ┌─────────────┐   ┌──────────────┐   ┌──────────┐ │
│  │ DESCUBRIR   │──▶│ PERSONALIZAR │──▶│ COMPRAR  │ │
│  │ Mapa + Feed │   │ Géneros +    │   │ Directo  │ │
│  │ Geolocali-  │   │ Artistas     │   │ Sin fees │ │
│  │ zado        │   │ favoritos    │   │ abusivos │ │
│  └─────────────┘   └──────────────┘   └──────────┘ │
│         │                                     │      │
│         ▼                                     ▼      │
│  ┌─────────────┐                     ┌──────────────┐│
│  │ ARTISTAS &  │                     │   AGENDA     ││
│  │ VENUES      │                     │   PERSONAL   ││
│  │ Panel de    │                     │   Calendario ││
│  │ autogestión │                     │   + Alertas  ││
│  └─────────────┘                     └──────────────┘│
└─────────────────────────────────────────────────────┘
```

### Funcionalidades core

| Funcionalidad | Descripción | Diferenciador |
|---------------|-------------|---------------|
| **Mapa de conciertos en vivo** | Visualización de eventos cercanos en mapa interactivo con filtros por género, fecha, precio y tipo (mainstream/underground). | Geolocalización automática + cobertura underground. |
| **Feed personalizado** | Algoritmo que prioriza eventos según géneros preferidos, artistas seguidos, historial de asistencia y proximidad. | No solo mainstream: entiende la escena local. |
| **Compra directa de boletos** | Checkout integrado in-app con pasarela de pago local (PSE, OXXO, Mercado Pago, tarjetas). Boleto digital con QR único. | Comisión fija baja (5-8%) vs. 15-30% de incumbentes. |
| **Panel de artista/venue** | Herramienta self-service para crear eventos, definir precios, gestionar aforos y recibir pagos directos. | Democratiza el acceso: cualquier artista puede vender. |
| **Agenda personal** | Calendario de eventos confirmados, recordatorios inteligentes, y opción de compartir planes con amigos. | Integración con calendario del dispositivo. |
| **Alertas de proximidad** | Notificación push cuando hay un concierto relevante cerca del usuario en tiempo real (ej: "Hay un show de jazz a 3 cuadras en 2 horas"). | Descubrimiento serendípico — nadie más lo hace. |

---

## 3. Mercado

### Mercado objetivo

| Dimensión | Detalle |
|-----------|---------|
| **Geografía inicial** | Colombia, México, Argentina, Chile |
| **Demografía** | 18-35 años, urbanos, smartphone con datos móviles |
| **Psicografía** | Amantes de la música en vivo. Asisten a ≥3 eventos/año. Valoran descubrir artistas nuevos y apoyar la escena local. Digitalmente nativos. |
| **Tamaño estimado** | ~45M de personas en el rango etario en los 4 países × ~35% que asisten a conciertos regularmente = **~15.7M usuarios potenciales** |

### Segmentos de usuario

```
                    MAINSTREAM ◀──────────▶ UNDERGROUND
                         │                      │
           ┌─────────────┤                      ├─────────────┐
           │             │                      │             │
     ┌─────▼─────┐ ┌────▼──────┐ ┌─────────────▼┐ ┌─────────▼────────┐
     │ CASUAL    │ │ ENTUSIASTA│ │ EXPLORADOR    │ │ SCENE INSIDER    │
     │ FAN       │ │ MAINSTREAM│ │ MUSICAL       │ │                  │
     │           │ │           │ │               │ │                  │
     │ 3-5       │ │ 6-12      │ │ 8-15+         │ │ 15-30+           │
     │ shows/año │ │ shows/año │ │ shows/año     │ │ shows/año        │
     │           │ │           │ │ Mezcla ambos  │ │ Underground core │
     │ Compra    │ │ Busca     │ │ Descubre por  │ │ Ya conoce la     │
     │ tickets   │ │ mejores   │ │ algoritmo     │ │ escena, necesita │
     │ donde sea │ │ precios   │ │               │ │ herramienta      │
     └───────────┘ └───────────┘ └───────────────┘ └──────────────────┘
         20%           30%             35%               15%
     (volumen)     (revenue)      (engagement)       (evangelistas)
```

**Segmento prioritario MVP:** Explorador Musical — mayor propensión a probar una nueva app, alta frecuencia, genera contenido y recomendaciones orgánicas.

### Landscape competitivo

| Competidor | Fortaleza | Debilidad vs. ConcertRadar |
|------------|-----------|----------------------------|
| **Ticketmaster (Live Nation)** | Catálogo mainstream masivo, partnerships con venues grandes | Comisiones altas, cero cobertura underground, sin descubrimiento personalizado |
| **Eventbrite** | Fácil de usar para organizadores, presencia global | Generalista (no solo música), sin geolocalización en tiempo real, sin foco underground |
| **Tixr** | Diseño premium, white-label para venues | No tiene discovery del lado del fan, limitada presencia LATAM |
| **Songkick / Bandsintown** | Buen tracking de artistas, alertas | No venden boletos directamente en LATAM, catálogo underground limitado |
| **Boletia (MX)** | Fuerte en México, self-service | Solo México, sin mapa ni discovery inteligente |
| **Passline (CL/AR)** | Buena presencia local | Sin personalización, sin foco en underground |

### Oportunidad estratégica

> Ningún jugador actual combina **descubrimiento geolocalizado + personalización por género + ticketing directo para independientes** en un solo producto diseñado para Latinoamérica. ConcertRadar ocupa un espacio blanco en la intersección de estos tres ejes.

---

## 4. Propuesta de Valor

### Por segmento

**Para el fan/asistente:**
> *"Descubre conciertos que amas cerca de ti —de Dua Lipa al bar de jazz de tu barrio— y compra boletos sin pagar comisiones ridículas. Todo en una app."*

**Para el artista independiente / venue:**
> *"Publica tu evento, vende boletos directamente a tu audiencia y quédate con lo que mereces. Sin gatekeepers, sin comisiones abusivas."*

### Value Proposition Canvas (resumen)

| | Fan / Asistente | Artista / Venue |
|---|---|---|
| **Jobs-to-be-done** | Encontrar eventos que me gusten cerca. Comprar boletos fácil y barato. Planificar mi agenda cultural. | Llenar mi evento. Vender boletos sin perder margen. Llegar a audiencias nuevas. |
| **Pains** | Fragmentación de info. Fees altos. Se entera tarde. Boletos falsos. | Invisibilidad. Comisiones 15-30%. Herramientas complejas/caras. Sin data de su audiencia. |
| **Gains** | Descubrir artistas nuevos. Ahorrar dinero. Experiencia social (ir con amigos). | Más asistentes. Más ingreso neto. Data para tomar decisiones. Profesionalizar su marca. |

### Modelo de negocio

| Flujo de ingreso | Descripción | Target |
|------------------|-------------|--------|
| **Comisión por boleto** | 5-8% por transacción (vs. 15-30% de incumbentes) | Principal — escala con volumen |
| **Promoción destacada** | Artistas/venues pagan por posicionamiento premium en el feed y mapa | Secundario — monetización de oferta |
| **ConcertRadar Pro (artista)** | Suscripción mensual con analytics avanzados, herramientas de CRM de audiencia, y prioridad en discovery | Terciario — recurrente |
| **Partnerships con marcas** | Patrocinio de experiencias in-app (ej: "Presentado por Spotify" / marcas de bebidas) | Futuro — post product-market fit |

---

## 5. KPIs

### North Star Metric

> **Boletos comprados por mes a través de la plataforma**
>
> Refleja simultáneamente: adopción del fan, valor para el artista/venue, y revenue directo.

### KPIs por área

#### Adquisición
| KPI | Definición | Meta MVP (6 meses post-launch) |
|-----|------------|-------------------------------|
| Descargas totales | Instalaciones de la app | 100K |
| CAC | Costo de adquisición por usuario registrado | < $1.50 USD |
| Tasa de registro | Descargas → Registro completado | > 60% |
| Artistas/venues registrados | Cuentas activas del lado oferta | 500+ |

#### Activación
| KPI | Definición | Meta MVP |
|-----|------------|----------|
| Onboarding completado | Usuario seleccionó ≥3 géneros + habilitó ubicación | > 70% de registrados |
| Primer evento guardado | Usuario agregó un evento a su agenda en la primera sesión | > 40% |
| Primer boleto comprado | Conversión a compra en los primeros 30 días | > 8% |

#### Engagement
| KPI | Definición | Meta MVP |
|-----|------------|----------|
| MAU / DAU ratio | Stickiness de la app | > 25% DAU/MAU |
| Sesiones/semana por usuario activo | Frecuencia de uso | ≥ 2.5 |
| Eventos vistos por sesión | Profundidad de descubrimiento | ≥ 4 |
| Tasa de interacción con alertas push | Opens de notificaciones de eventos | > 12% |

#### Revenue
| KPI | Definición | Meta MVP |
|-----|------------|----------|
| GMV (Gross Merchandise Value) | Valor total de boletos vendidos | $500K USD |
| Revenue neto | Comisiones cobradas | $35K USD |
| Ticket promedio | Precio medio del boleto vendido | $15-25 USD |
| Boletos/mes | North star metric | 5,000+ en mes 6 |

#### Retención
| KPI | Definición | Meta MVP |
|-----|------------|----------|
| Retención D7 | % usuarios que regresan a los 7 días | > 35% |
| Retención D30 | % usuarios que regresan a los 30 días | > 20% |
| Repeat purchase rate | % de compradores que compran un segundo boleto | > 25% en 90 días |
| Churn de artistas | % de artistas que dejan de publicar eventos | < 15% mensual |

---

## 6. Roadmap MVP

### Principios del MVP

1. **Primero descubrimiento, luego transacción.** Si el usuario no encuentra eventos relevantes, no hay compra.
2. **Supply antes que demand.** Sin eventos listados, la app está vacía. Priorizar onboarding de artistas/venues.
3. **Un país primero.** Lanzar en Colombia como mercado piloto antes de expandir.
4. **Mobile-first, web-second.** La experiencia core es móvil; el panel de artista puede ser web responsive.

### Fases

```
  FASE 0          FASE 1            FASE 2              FASE 3
  PRE-MVP         MVP               CRECIMIENTO         ESCALA
  
  Sem 1-4         Sem 5-14          Sem 