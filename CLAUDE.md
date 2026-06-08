# Proyecto: Dashboard Admisión NSDC

## Contexto
Sistema de admisión del Colegio Nuestra Señora del Camino (La Reina, Santiago).
Dashboard HTML que lee datos de un Google Sheet público y muestra el estado del proceso de admisión.

## Stack
- HTML + CSS + Vanilla JS (un solo archivo index.html)
- Tailwind CSS por CDN
- Chart.js por CDN
- Fuentes: Cormorant Garamond (títulos), DM Sans (cuerpo)

## Fase actual
Fase 2 — Prototipo navegable con datos hardcodeados (mock). NO conectar al Sheet todavía.

## Datos del Sheet (para Fase 3, no usar todavía)
- ID: 1sWTl_hyJ3X7Dg5qcHkyj6ve92nVcy8XLpUH9z8DBMJ4
- URL pública: https://docs.google.com/spreadsheets/d/e/2PACX-1vSkmQlRtxmJjkdPQzDCmnYQDdcWca5h1q59mtaJLRBrjVMqFio7pN2wCIOrUuSxBe72MtLdKyGgV-A6/pubhtml
- Password dashboard: ColegioNSDC
- Año activo: 2027

## Paleta institucional
- Primario: #1B3A5C (azul institucional)
- Acento: #C9A961 (dorado, máx 10%)
- Fondo: #FAFAF8 (marfil)
- Texto: #2C2C2E (carbono)
- Secundario: #6B6B70 (grafito)
- Alerta: #B85450
- Éxito: #5C8A6E

## Reglas de trabajo
- Español de Chile, registro informal tú, fechas DD-MM-AAAA, separador decimal coma.
- Lenguaje conciso. Evita "crucial", "clave", "esencial", tono preachy.
- Antes de ejecutar cambios grandes, presenta plan y espera confirmación.
- Responsive obligatorio: PC ≥1024, Tablet 768–1023, Mobile ≤767. Sin barras laterales negras. 100vw × 100vh en pantalla de login.