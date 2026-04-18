

# ConcertRadar — Product Brief

---

## 1. Problema

### Contexto del mercado

El mercado de ticketing online en Latinoamérica está en expansión acelerada, con plataformas móviles liderando el crecimiento. Sin embargo, el ecosistema actual presenta **tres fallas estructurales** que afectan directamente a nuestro segmento:

### Problemas identificados

| # | Problema | Quién lo sufre | Impacto |
|---|---------|---------------|---------|
| **P1** | **Descubrimiento fragmentado**: No existe una fuente única y confiable para encontrar conciertos cercanos, especialmente de la escena underground. Los usuarios dependen de Instagram stories, grupos de WhatsApp y flyers físicos. | Fans de música (18-35) | Pierden eventos que les interesarían; alta fricción para planificar |
| **P2** | **Monopolio de intermediarios con comisiones abusivas**: Ticketmaster y similares cobran entre 15-30% de comisión. Artistas independientes no pueden acceder a estas plataformas o no les resulta rentable. | Artistas independientes y promotores locales | Reducción de ingresos, barrera de entrada, precios inflados para fans |
| **P3** | **Experiencia de compra desconectada**: El usuario descubre un evento en una red social, busca boletos en otra plataforma, paga en un tercero. El flujo es roto, lento y genera abandono. | Fans de música | Tasas altas de abandono de compra; frustración con la experiencia |

### Dato clave

> El mercado global de ticketing online proyecta crecimiento sostenido hasta 2033, con **mobile como plataforma dominante**. México representa ~25% del mercado regional y Brasil ~40%. Colombia, Argentina y Chile son mercados emergentes con adopción digital acelerada y escenas musicales vibrantes pero desatendidas por las plataformas existentes.

---

## 2. Solución

**ConcertRadar** es una app móvil que unifica descubrimiento, personalización y compra de boletos para conciertos — tanto mainstream como underground — en una sola experiencia nativa, con geolocalización automática y venta directa sin intermediarios para artistas independientes.

### Flujo principal del usuario (fan)

```
Abre la app → Geolocalización detecta ciudad/zona
    → Feed personalizado por géneros y ubicación
        → Explora evento (lineup, venue, mapa, reviews)
            → Compra boleto en ≤3 taps (pago in-app)
                → Boleto digital en wallet + se agrega a agenda personal
                    → Recibe recordatorios y actualizaciones del evento
```

### Flujo principal del artista/promotor

```
Se registra como artista/promotor → Crea evento
    → Define precio, aforo, venue, descripción
        → Evento publicado y geolocalizado automáticamente
            → Recibe pagos directos (comisión ConcertRadar: 5-8%)
                → Dashboard con métricas de venta en tiempo real
```

### Módulos funcionales del MVP

| Módulo | Descripción | Prioridad |
|--------|------------|-----------|
| **Mapa de descubrimiento** | Vista de mapa con eventos cercanos geolocalizados, filtros por género, fecha y rango de precio | P0 — Core |
| **Feed personalizado** | Algoritmo de recomendación basado en géneros seleccionados, historial y ubicación | P0 — Core |
| **Compra directa de boletos** | Checkout in-app con pasarela de pagos local (PSE, OXXO, Mercado Pago, tarjeta) | P0 — Core |
| **Agenda personal** | Calendario con eventos guardados/comprados, sincronización con calendario del dispositivo | P0 — Core |
| **Panel de artista/promotor** | Creación de eventos, gestión de aforo, dashboard de ventas | P0 — Core |
| **Boleto digital** | QR dinámico con validación anti-fraude, integración con Apple/Google Wallet | P1 — Importante |
| **Notificaciones inteligentes** | Alertas de eventos nuevos por género/zona, recordatorios pre-evento, anuncios de artistas seguidos | P1 — Importante |
| **Social / compartir** | Compartir eventos a WhatsApp/Instagram Stories, ver qué amigos asisten | P2 — Diferenciador |

---

## 3. Mercado

### Mercado objetivo

| Dimensión | Detalle |
|-----------|---------|
| **Geografía** | Colombia, México, Argentina, Chile (lanzamiento) |
| **Demografía** | 18-35 años, usuarios de smartphone, ingresos medios y medio-altos |
| **Psicografía** | Amantes de la música en vivo, descubridores activos de nuevos artistas, participantes frecuentes de escenas locales |
| **Comportamiento** | Compran boletos online, usan apps de mapas, activos en redes sociales para descubrir música |

### Tamaño estimado

| Segmento | Estimación |
|----------|-----------|
| **TAM** (Mercado de ticketing online en LATAM) | ~$4.5B USD proyectado a 2030 |
| **SAM** (Ticketing de conciertos/música en vivo en CO, MX, AR, CL) | ~$800M - $1.2B USD |
| **SOM** (Captura realista en 24 meses — enfoque underground + mainstream emergente) | ~$15M - $25M USD en GMV |

### Landscape competitivo

| Competidor | Fortaleza | Debilidad vs. ConcertRadar |
|-----------|----------|---------------------------|
| **Ticketmaster / Live Nation** | Dominio mainstream, acuerdos de exclusividad con venues grandes | Sin cobertura underground, comisiones altas (15-30%), UX legacy, sin descubrimiento inteligente |
| **Boletia (MX)** | Enfoque en eventos independientes | Solo México, sin geolocalización ni discovery, UX básica |
| **Passline (AR/CL)** | Buena penetración en clubes y fiestas electrónicas | Nicho limitado, sin agenda personalizada, marca poco conocida fuera de electrónica |
| **Eventbrite** | Plataforma global, fácil creación de eventos | Generalista (no enfocado en música), sin experiencia de discovery, UX no optimizada para mobile-first |
| **Redes sociales (IG/WhatsApp)** | Donde realmente se descubren eventos underground hoy | No hay compra integrada, información dispersa, no hay curaduría |

### Ventaja competitiva sostenible

> **ConcertRadar es la primera plataforma mobile-first en LATAM que cierra el loop completo**: descubrimiento geolocalizado → personalización por gusto → compra directa → experiencia post-compra — tanto para mainstream como underground, con comisiones justas que atraen al supply de artistas independientes que hoy no tiene plataforma.

---

## 4. Propuesta de Valor

### Para fans de música (demanda)

> **"Nunca más te pierdas un concierto que te importa."**
> Descubre eventos cerca de ti — desde tu banda favorita hasta joyas underground que no encontrarás en ninguna otra app. Compra tus boletos en segundos, sin sorpresas de precio.

### Para artistas independientes y promotores (oferta)

> **"Vende directo a tu audiencia. Sin intermediarios abusivos."**
> Publica tu evento en minutos, llega a fans geolocalizados que buscan tu género, cobra directamente con comisiones de solo 5-8%.

### Diferenciadores clave

1. **Discovery geolocalizado e inteligente**: Mapa + algoritmo de recomendación = el "Spotify del descubrimiento de conciertos"
2. **Underground + mainstream en un solo lugar**: Rompemos la barrera artificial entre escenas
3. **Comisiones justas (5-8% vs. 15-30%)**: Creamos un flywheel — más artistas publican → más oferta → más fans → más artistas
4. **Mobile-first, LATAM-native**: Pasarelas de pago locales, UX en español, diseñado para el comportamiento real del usuario latinoamericano
5. **Experiencia end-to-end**: Del descubrimiento al boleto digital en wallet sin salir de la app

---

## 5. KPIs

### Métricas North Star

| Métrica | Definición | Target MVP (6 meses post-lanzamiento) |
|---------|-----------|---------------------------------------|
| **🌟 Boletos vendidos por mes** | Transacciones completadas a través de la plataforma | 10,000/mes al mes 6 |
| **🌟 Eventos publicados por mes** | Eventos creados por artistas/promotores | 500/mes al mes 6 |

### Métricas de adquisición

| Métrica | Target mes 6 |
|---------|-------------|
| Descargas acumuladas | 150,000 |
| Usuarios activos mensuales (MAU) | 45,000 |
| Costo de adquisición de usuario (CAC) | < $1.50 USD |
| Artistas/promotores registrados | 1,200 |

### Métricas de activación y engagement

| Métrica | Target mes 6 |
|---------|-------------|
| % de usuarios que completan onboarding (selección de géneros + geolocalización) | > 70% |
| Eventos descubiertos por sesión (promedio) | ≥ 4 |
| Tasa de conversión discovery → compra | > 3.5% |
| Sesiones por usuario por semana | ≥ 2.5 |
| Eventos guardados en agenda por usuario activo | ≥ 3/mes |

### Métricas de retención

| Métrica | Target mes 6 |
|---------|-------------|
| Retención D7 | > 40% |
| Retención D30 | > 25% |
| Retención por cohorte al mes 3 | > 18% |
| Tasa de recompra (usuarios que compran 2+ boletos) | > 30% |

### Métricas de revenue

| Métrica | Target mes 6 |
|---------|-------------|
| GMV mensual | $200,000 USD |
| Revenue mensual (comisión 5-8%) | $12,000 - $16,000 USD |
| Ticket promedio de compra | $20 USD |

### Métricas de oferta (supply side)

| Métrica | Target mes 6 |
|---------|-------------|
| % de eventos que venden ≥50% de aforo vía ConcertRadar | > 25% |
| NPS de artistas/promotores | > 50 |
| Tiempo promedio de creación de evento | < 5 minutos |

---

## 6. Roadmap MVP

### Fase 0 — Validación (Semanas 1–4)

**Objetivo**: Confirmar demanda real antes de construir.

| Entregable | Detalle | Owner |
|-----------|---------|-------|
| Landing page con waitlist | Segmentada por ciudad (Bogotá, CDMX, Buenos Aires, Santiago) | Marketing + Design |
| 40 entrevistas de descubrimiento | 20 fans + 20 artistas/promotores independientes | Product + Research |
| Prototipo clickeable (Figma) | Flujo completo: discovery → detalle → compra → wallet | Design + Product |
| Test de prototipo con 15 usuarios | Validar comprensión del flujo y propuesta de valor | Research |
| Partnership exploratoria con 10 venues | Carta de intención para alimentar catálogo inicial | Business Dev |

**Go/No-Go Gate**: ≥2,000 registros en waitlist + validación cualitativa positiva en ≥75% de entrevistas.

---

### Fase 1 — MVP Build (Semanas 5–14)

**Objetivo**: Construir el producto mínimo funcional para un piloto controlado en 2 ciudades.

#### Sprint 1-2 (Semanas 5-8): Foundation

| Feature | Alcance MVP | Plataforma |
|---------|------------|------------|
| Autenticación | Email + Google/Apple sign-in | iOS + Android (React Native) |
| Onboarding | Selección de géneros (mín. 3), permiso de geolocalización, ciudad | Mobile |
| Backend de eventos | CRUD de eventos, modelo de datos, API REST | Backend (Node.js/Python) |
| Panel de artista (v1) | Crear evento: nombre, fecha, venue, precio, género, aforo, imagen | Web responsive |

#### Sprint 3-4 (Semanas 9-12): Core Experience

| Feature | Alcance MVP | Plataforma |
|---------|------------|------------|
| Mapa de discovery | Mapa interactivo con pins de eventos, filtros: género, fecha, rango km | Mobile |
| Feed personalizado | Lista rankeada por match (género + cercanía + fecha), cards con info clave | Mobile |
| Detalle de evento | Info completa, ubicación en mapa, link a venue, lineup, precio | Mobile |
| Compra de boleto | Checkout en ≤3 pasos, integración con pasarela (Mercado Pago + tarjeta) | Mobile |
| Boleto digital | QR estático en app + opción de agregar a Apple/Google Wallet | Mobile |
| Agenda personal | Lista de eventos comprados + guardados, ordenados por fecha | Mobile |

#### Sprint 5 (Semanas 13-14): Polish + QA

| Actividad | Detalle |
|----------|---------|
| QA integral | Testing funcional, de pagos (sandbox), de geolocalización |
| Performance | Optimización de carga de mapa, tiempos de respuesta API <500ms |
| Seguridad | Auditoría de flujo de pagos, protección de datos personales |
| Contenido inicial | Carga de ≥100 eventos reales en ciudades piloto |

**Stack técnico propuesto**:
- **Mobile**: React Native (Expo)
- **Backend**: Node.js + PostgreSQL + PostGIS (geolocalización)
- **Pagos**: Mercado Pago (AR, MX, CL, CO) + Stripe como fallback
- **Maps**: Mapbox (mejor pricing que Google Maps a escala)
- **Infra**: AWS (ECS + RDS + S3 + CloudFront)

---

### Fase 2 — Piloto Controlado (Semanas 15–20)

**Objetivo**: Lanzamiento soft en **Bogotá + CDMX** con cohorte controlada.

| Acción | Meta | Métrica de éxito |
|--------|------|------------------|
| Onboarding de 50 artistas/promotores en cada ciudad | 100 artistas activos | ≥200 eventos publicados |
| Invitación a 5,000 usuarios de waitlist | Activación de early adopters | ≥60% completan onboarding |
| Alianza con 5 venues por ciudad | Eventos verificados con experiencia presencial | 10 venues activos |
| Primer ciclo de compra real | Validar flujo end-to-end con dinero real | ≥500 boletos vendidos |
| Feedback loops semanales | Encuestas in-app + entrevistas 1:1 | NPS ≥ 40 |
| Iteración rápida | 2 releases por semana basados en feedback | Bug resolution <48h |

**Go/No-Go Gate para escalar**: ≥500