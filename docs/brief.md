

# brief.md — ConcertRadar

---

## 1. Problema

### Para los fans
Los amantes de la música en Latinoamérica (18-35 años) enfrentan un ecosistema fragmentado e ineficiente para descubrir y asistir a conciertos:

- **Descubrimiento roto:** No existe una fuente única y confiable que agregue eventos mainstream *y* underground. Los conciertos de artistas independientes se promocionan en stories de Instagram, grupos de WhatsApp o flyers físicos — información efímera, dispersa y difícil de buscar.
- **Fricción en la compra:** Las plataformas dominantes (Ticketmaster, StubHub, Passline, TuBoleta, Eventbrite) cobran comisiones del 15-30%, tienen UX deficiente en móvil, y frecuentemente sufren caídas en eventos de alta demanda.
- **Falta de personalización real:** Ninguna plataforma aprende del gusto musical del usuario para recomendar eventos de forma proactiva y geolocalizada. El usuario tiene que buscar, no descubrir.

### Para los artistas independientes
- **Barrera de acceso:** Las plataformas de ticketing exigen volúmenes mínimos, contratos complejos o comisiones prohibitivas para artistas emergentes.
- **Desconexión con su audiencia:** No tienen herramientas para llegar a fans cercanos que realmente escuchan su género.
- **Sin datos:** Venden boletos en efectivo o por transferencia sin trazabilidad, sin analytics, sin posibilidad de hacer retargeting.

---

## 2. Solución

**ConcertRadar** es una app móvil (iOS + Android) que combina descubrimiento geolocalizado de conciertos, agenda personalizada por géneros y compra directa de boletos — conectando fans con música en vivo (mainstream y underground) en su ciudad, sin intermediarios costosos.

### Pilares funcionales

| Pilar | Descripción |
|---|---|
| **🗺️ Radar** | Mapa interactivo con geolocalización automática que muestra conciertos cercanos en tiempo real. Filtros por género, fecha, precio y tipo (mainstream / underground). |
| **🎵 Perfil musical** | Onboarding que conecta con Spotify/Apple Music o permite selección manual de géneros y artistas. Alimenta un motor de recomendación que mejora con cada interacción. |
| **📅 Agenda personal** | Calendario de eventos guardados con notificaciones inteligentes (recordatorios, bajadas de precio, sold-out alerts, artistas similares en la zona). |
| **🎟️ Compra directa** | Checkout nativo con pasarelas locales (PSE, OXXO, Mercado Pago, tarjeta), boleto digital con QR, y comisiones transparentes (máx. 5-8% vs. 15-30% del mercado). |
| **🎤 Portal artistas** | Dashboard self-service para artistas independientes: crear evento, fijar precio, publicar, vender y ver analytics en <5 minutos. Sin mínimos ni contratos. |

---

## 3. Mercado

### Tamaño y crecimiento

| Indicador | Dato |
|---|---|
| Mercado global de ticketing online | CAGR 3.8% (2026-2032) |
| Plataformas culturales y entretenimiento | CAGR 12.9% (2026-2033) |
| Canal principal de compra | **Mobile-first** (>60% transacciones en LATAM) |
| Tendencia regional | Alternativas locales a Ticketmaster ganan market share aceleradamente |

### Mercado objetivo (TAM → SAM → SOM)

```
TAM — Ticketing de eventos en vivo LATAM:           ~$4.2B USD (2026)
SAM — Conciertos y festivales CO/MX/AR/CL:          ~$980M USD
SOM — Captura año 1 (underground + nicho):           ~$2.4M USD
```

### Competencia

| Competidor | Fortaleza | Debilidad que ConcertRadar explota |
|---|---|---|
| **Ticketmaster / Ocesa** | Inventario mainstream, escala | Comisiones altas, cero underground, UX pobre en móvil |
| **Eventbrite** | Self-service para organizadores | No es discovery-first, sin recomendación musical, genérico |
| **Passline / TuBoleta** | Presencia local | Sin geolocalización, sin personalización, sin foco en independientes |
| **Dice** | Buen UX, anti-scalping | No opera en LATAM, no tiene ecosistema underground local |
| **Bandsintown** | Discovery + alertas | No vende boletos directamente, no tiene escena underground LATAM |
| **Instagram / WhatsApp** | Donde vive la escena underground hoy | No es buscable, no es transaccional, no escala |

**Posicionamiento diferencial:** ConcertRadar es el único producto que une **discovery geolocalizado + personalización musical + transacción directa + escena underground** en LATAM.

---

## 4. Propuesta de Valor

### Para fans (usuario final)

> **"Nunca más te pierdas un concierto que te habría encantado."**

- Descubre conciertos a tu alrededor que no sabías que existían.
- Compra en 3 taps, sin comisiones abusivas.
- Tu agenda musical se arma sola según tu gusto.

### Para artistas independientes

> **"Publica, vende y llena tu show — sin pedirle permiso a nadie."**

- Crea tu evento y vende boletos en minutos.
- Llega a fans reales que escuchan tu género y están cerca.
- Comisiones justas (5-8%) y cobro directo.

### Para venues / promotores

> **"Llena tu espacio con la audiencia correcta."**

- Visibilidad ante un público segmentado y activo.
- Data de asistencia y comportamiento de compra.

---

## 5. KPIs

### North Star Metric
**Boletos vendidos por mes** — captura activación, retención y monetización en un solo indicador.

### KPIs por área

| Área | Métrica | Target MVP (6 meses) |
|---|---|---|
| **Adquisición** | Descargas totales | 50,000 |
| **Adquisición** | CAC (Costo de Adquisición) | < $1.50 USD |
| **Activación** | % usuarios que completan perfil musical | > 60% |
| **Activación** | % usuarios que guardan ≥1 evento en semana 1 | > 35% |
| **Engagement** | MAU / Descargas (tasa de actividad mensual) | > 40% |
| **Engagement** | Eventos vistos por sesión | > 3 |
| **Transacción** | Conversión vista-evento → compra | > 4% |
| **Transacción** | Boletos vendidos / mes | 5,000 (mes 6) |
| **Retención** | Retención D30 | > 25% |
| **Monetización** | GMV (Gross Merchandise Value) mensual | $75,000 USD (mes 6) |
| **Oferta** | Eventos activos en plataforma / mes | > 400 |
| **Oferta** | Artistas independientes registrados | > 300 |
| **NPS** | Net Promoter Score fans | > 50 |
| **NPS** | Net Promoter Score artistas | > 55 |

---

## 6. Roadmap MVP

### Fase 0 — Validación (Semanas 1-4)
> **Objetivo:** Confirmar demanda antes de escribir una línea de código.

| Entregable | Detalle |
|---|---|
| Landing page + waitlist | Segmentada por ciudad (Bogotá, CDMX, Buenos Aires, Santiago). Meta: 2,000 registros. |
| Entrevistas de descubrimiento | 30 fans + 15 artistas independientes. Validar dolor, disposición a pagar, flujos actuales. |
| Mapeo de oferta | Inventario manual de venues underground y calendarios de eventos en las 4 ciudades. |
| Definición de partnerships | Contacto inicial con 10 venues y 20 artistas indie por ciudad para supply del MVP. |

**Go / No-Go:** ≥1,500 registros en waitlist Y validación cualitativa del dolor en ≥80% de entrevistas.

---

### Fase 1 — MVP Core (Semanas 5-14)
> **Objetivo:** Lanzar en **1 ciudad** (Bogotá) con el loop completo: descubrir → guardar → comprar.

| Feature | Prioridad | Descripción |
|---|---|---|
| Onboarding musical | P0 | Selección de géneros + conexión opcional Spotify para semilla de gustos. |
| Mapa Radar | P0 | Vista de mapa con eventos geolocalizados. Filtros: género, fecha, precio, distancia. |
| Feed personalizado | P0 | Lista de eventos recomendados basada en perfil musical + ubicación. |
| Detalle de evento | P0 | Info completa: artista, venue, fecha, precio, mapa, fotos, enlace a música. |
| Agenda personal | P0 | Guardar eventos + notificaciones (recordatorio 24h antes, sold-out alert). |
| Checkout + boleto QR | P0 | Pasarela de pago (PSE + tarjeta vía Stripe/Wompi). Boleto digital con QR único. |
| Portal artista básico | P0 | Registro, crear evento, fijar precio, ver ventas en tiempo real. |
| Validador QR (venue) | P1 | App mínima o web para que el venue escanee y valide boletos en puerta. |
| Auth + perfil usuario | P0 | Registro email / Google / Apple. |
| Analytics artista | P1 | Dashboard: boletos vendidos, ingresos, demografía básica de compradores. |

**Stack sugerido:** React Native (cross-platform) · Node.js/Python backend · PostgreSQL + PostGIS · Stripe / Wompi pagos · Firebase push notifications · Mapbox o Google Maps SDK.

**Equipo mínimo:** 2 mobile devs, 1 backend dev, 1 diseñador producto, 1 PM, 1 ops/partnerships (part-time).

---

### Fase 2 — Iteración + Segunda ciudad (Semanas 15-22)
> **Objetivo:** Iterar con datos reales de Bogotá, lanzar en CDMX.

| Feature / Acción | Prioridad | Descripción |
|---|---|---|
| Motor de recomendación v2 | P0 | Incorporar señales de comportamiento (eventos vistos, comprados, guardados) al algoritmo. |
| Integración Spotify/Apple Music | P1 | Importar artistas top del usuario para mejorar recomendaciones automáticamente. |
| Social proof | P1 | "X amigos van a este evento" (conexión contactos opcional). |
| Notificaciones inteligentes | P1 | "Artista que escuchas tocará a 3km" / "Últimos boletos para [evento guardado]". |
| Reviews post-evento | P2 | Rating del evento para alimentar calidad de recomendaciones. |
| Expansión CDMX | P0 | Replicar playbook de partnerships + onboarding de venues y artistas. |
| Pasarela OXXO | P0 | Pago en efectivo para México (crítico para conversión). |

---

### Fase 3 — Escala + Monetización (Semanas 23-30)
> **Objetivo:** 4 ciudades activas, modelo de monetización validado.

| Feature / Acción | Prioridad |
|---|---|
| Expansión Buenos Aires + Santiago | P0 |
| Mercado Pago como pasarela (AR) | P0 |
| Promoted Events (artistas/venues pagan por visibilidad) | P1 |
| Planes premium artistas (analytics avanzados, badges verificados) | P2 |
| Anti-scalping (boleto intransferible vinculado a identidad) | P1 |
| API para venues (sincronizar calendario propio con ConcertRadar) | P2 |
| Programa de embajadores (influencers de escena local por ciudad) | P1 |

---

## Modelo de Monetización

| Fuente | Descripción | Target |
|---|---|---|
| **Comisión por boleto** | 5-8% sobre precio de venta (cobra al comprador o split con artista) | 70% del revenue |
| **Promoted Events** | Artistas/venues pagan por posicionamiento destacado en Radar y Feed | 20% del revenue |
| **Planes artista Pro** | Suscripción mensual para analytics avanzados, herramientas de CRM, prioridad en recomendaciones | 10% del revenue |

---

## Riesgos y Mitigaciones

| Riesgo | Impacto | Probabilidad | Mitigación |
|---|---|---|---|
| **Supply insuficiente** (pocos eventos listados) | Alto | Alta | Curación manual inicial, partnerships con venues, equipo de ops dedicado por ciudad. Onboarding white-glove para primeros 50 artistas. |
| **Cold start de recomendaciones** | Medio | Alta | Onboarding musical robusto + curación editorial ("Lo mejor esta semana en Bogotá"). |
| **Regulación de ticketing** por país | Medio | Media | Due diligence legal por mercado antes de lanzar. Estructura de comisiones adaptable. |
| **Fraude / boletos falsos** | Alto | Baja | QR dinámico vinculado a cuenta, boleto intransferible en MVP. |
| **Competidor grande copia el modelo** | Medio | Media | Velocidad de ejecución + profundidad en underground (moat de comunidad y supply difícil de replicar). |
| **Dependencia de pasarelas de pago** | Medio | Baja | Integrar ≥2 pasarelas por mercado desde fase 2. |

---

## Criterios de Éxito del MVP (Mes 6 — Go / No-Go para Serie Seed)

| Criterio | Umbral mínimo |
|---|---|
| Boletos vendidos acumulados | ≥ 15,000 |
| Artistas independientes activos (≥1 evento publicado) | ≥ 150 |
| Retención D30 | ≥ 25% |
| NPS fans | ≥ 45 |
| GMV acumulado | ≥ $200,000 USD |
| Ciudades operativas | ≥ 2 |

---

*Documento vivo. Última actualización: junio 2025. Owner: Product Lead, ConcertRadar.*