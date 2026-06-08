# Estado del Proyecto — Dashboard Admisión NSDC
Última actualización: 2026-05-29

---

## ✅ Fase 2 completada — Prototipo navegable con datos mock

### Qué se construyó

Un único archivo `index.html` autocontenido con:

**Login**
- Pantalla centrada, 100vw × 100vh, fondo marfil
- Logo institucional embebido en base64 (autocontenido, sin dependencia de ruta)
- Campo password → valida contra `ColegioNSDC` → guarda flag en `sessionStorage`

**Header fijo**
- Fondo blanco con logo institucional (44px alto)
- Selector de año (solo 2027 en mock)
- Indicador de última actualización
- Botón "Cerrar sesión"

**3 Vistas (tabs)**

1. **General**
   - 4 KPIs de postulantes: total, activos, matriculados, desistidos
   - 4 KPIs de cupos: capacidad total, matriculados reales, vacantes, retirados
   - Gráfico dona: distribución por género (Chart.js)
   - Gráfico barras apiladas: cupos NEEP total vs ocupados (Chart.js)
   - Barras horizontales por nivel (14 niveles) con tooltip al hover
   - Panel de alertas activas (generadas automáticamente por lógica de negocio)
   - Tabla resumen por nivel (capacidad, ocupados, retirados, vacantes, en proceso, aceptados, matriculados, lista espera, estado)

2. **Postulantes**
   - Filtros: buscador libre, estado, nivel, NEEP, hermanos
   - Botones: limpiar filtros, exportar CSV
   - Tabla con 9 columnas (algunas ocultas en mobile/tablet)
   - Filas con alerta marcadas con borde izquierdo rojo
   - Click en fila → modal lateral con ficha completa + alertas del postulante + historial individual

3. **Historial**
   - Tabla cronológica inversa de cambios de estado
   - Filtros: rango fechas, buscador, estado origen, estado destino
   - Exportar CSV

**Datos mock**
- 20 postulantes ficticios distribuidos en 8 niveles, todos los 7 estados representados
- 14 niveles con capacidad, matriculados, retirados, cupos NEEP
- 25 entradas de historial de cambios de estado
- Alertas generadas dinámicamente (aceptados +15 días, en proceso +30 días, en entrevista +20 días, niveles sin vacantes con lista de espera)

**Responsive**
- PC ≥1024px: grids de 4 columnas, tabla completa
- Tablet 768–1023px: grids 2×2, columnas teléfono ocultas
- Mobile ≤767px: 1 columna, tabla con scroll horizontal, modal pantalla completa

---

## 🎨 Paleta aplicada

| Variable | Color | Uso |
|----------|-------|-----|
| `--c-primario` | `#1B2D6B` | Azul marino del logo (ajustado en sesión) |
| `--c-acento` | `#C9A961` | Dorado institucional |
| `--c-fondo` | `#FAFAF8` | Marfil de fondo |
| `--c-texto` | `#2C2C2E` | Carbono |
| `--c-sec` | `#6B6B70` | Grafito |
| `--c-alerta` | `#B85450` | Rojo desaturado |
| `--c-exito` | `#5C8A6E` | Verde desaturado |

Tipografía: Cormorant Garamond 600 (títulos) + DM Sans 300/400/500 (cuerpo)

---

## 🔧 Aprendizajes técnicos de la sesión

1. **Logo embebido en base64** es indispensable para que el HTML funcione como archivo standalone (OneDrive móvil, WhatsApp, correo). Las rutas relativas no funcionan cuando se abre el HTML directamente desde el explorador de archivos del cel.

2. **El color primario del logo** es `#1B2D6B` (azul marino puro), más azul-índigo que el `#1B3A5C` original (que era más teal). Verificar con el cliente si prefiere ajuste fino.

3. **El header debe ser blanco** cuando se usa el logo institucional completo (escudo + texto en azul oscuro). Header oscuro hace invisible el texto del logo.

4. **Las líneas de alerta** (`border-left: 3px solid var(--c-alerta)`) en la tabla de postulantes se ven como líneas café/terracota. El cliente las notó — evaluar si cambiar a icono en columna o color diferente.

5. **`npx serve`** es suficiente para levantar el prototipo localmente en `localhost:3000`. El `.claude/launch.json` ya está configurado.

6. **La compresión de imagen** con Pillow (600px ancho, PNG optimize) redujo el logo de 1.156 KB a ~150 KB base64 — aceptable para embeberlo.

---

## ⏭️ Pendiente para Fase 3 — Conexión con Google Sheet real

- Leer datos del Sheet público (ID: `1sWTl_hyJ3X7Dg5qcHkyj6ve92nVcy8XLpUH9z8DBMJ4`)
- URL publicada: `https://docs.google.com/spreadsheets/d/e/2PACX-1vSkmQlRtxmJjkdPQzDCmnYQDdcWca5h1q59mtaJLRBrjVMqFio7pN2wCIOrUuSxBe72MtLdKyGgV-A6/pubhtml`
- Reemplazar objeto `MOCK` por fetch al Sheet (CSV export o pubhtml parsing)
- Manejo de errores de red y loading states
- Botón "Actualizar datos" en el header

## 🛠️ Ajustes visuales pendientes (antes de Fase 3)

- [ ] Definir cómo mostrar alertas en tabla (borde actual vs icono)
- [ ] Aprobar paleta final con cliente
- [ ] Revisar vista en mobile real (cel del cliente)
- [ ] Decidir si mostrar solo 14 niveles actuales o los 27 del spec original

---

## 📁 Archivos del proyecto

```
admision-nsdc-dashboard/
├── index.html              ← archivo principal (todo embebido)
├── CLAUDE.md               ← instrucciones del proyecto para Claude
├── Fase2_Dashboard_NSDC.md ← spec completo de Fase 2
├── ESTADO_PROYECTO.md      ← este archivo
├── .claude/
│   └── launch.json         ← config servidor local (npx serve, puerto 3000)
└── Gemini_Generated_Image_9ne9gh9ne9gh9ne9.png  ← logo original (ya embebido en HTML)
```
