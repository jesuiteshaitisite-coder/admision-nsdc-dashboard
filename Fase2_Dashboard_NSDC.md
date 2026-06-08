FASE 2 — Prototipo HTML navegable
Objetivo: validar el diseño visual e interacción antes de conectar el Sheet real. Trabaja con datos hardcodeados que imitan la estructura del Sheet.
2.1 Estructura del archivo
Un solo index.html con CSS y JS embebidos. Sin frameworks (HTML + Tailwind por CDN + Vanilla JS + Chart.js por CDN).
2.2 Identidad visual
Paleta institucional propuesta para Colegio NSDC:
	• Primario: #1B3A5C (azul institucional sobrio)
	• Acento: #C9A961 (dorado discreto, máximo 10%)
	• Fondo: #FAFAF8 (marfil)
	• Texto: #2C2C2E (carbono)
	• Secundario: #6B6B70 (grafito)
	• Alerta: #B85450 (rojo desaturado)
	• Éxito: #5C8A6E (verde desaturado)
Tipografía:
	• Títulos: Cormorant Garamond 600
	• Cuerpo: DM Sans 300–400
	• Labels: DM Sans 500 uppercase
Esta paleta la confirmas o la cambias antes de empezar Fase 2.
2.3 Layout
Pantalla de login (primera vista):
	• Centrada, sobria, escudo o nombre del colegio arriba.
	• Campo password único.
	• Botón "Ingresar".
	• Al validar contra ColegioLM, guarda flag en sessionStorage y muestra el dashboard.
Dashboard (post-login):
	• Header fijo con: logo/nombre del colegio, selector de año (2027, 2028…), indicador de "Última actualización", botón cerrar sesión.
	• Tabs de navegación: General | Postulantes | Historial.
	• Footer mínimo.
Responsive: breakpoints PC (≥1024px) full layout, Tablet (768–1023px) columnas reducidas, Mobile (≤767px) una columna vertical. Cumple tu regla de identidad: 100vw × 100vh, sin barras laterales negras.
2.4 Vista 1 — General
Bloque KPIs (cuatro tarjetas, fila superior):
	1. Total postulantes del año
	2. Postulantes activos (en seguimiento: estados Postulación recibida / En proceso / En entrevista / Aceptado / Lista de espera)
	3. Matriculados producto del proceso del año
	4. Desistidos durante el proceso del año
Bloque Cupos (cuatro tarjetas, segunda fila):
	1. Capacidad total del colegio (suma de columna C de Capacidad)
	2. Matriculados reales hoy (suma de columna I)
	3. Vacantes disponibles (suma de columna J)
	4. Retirados en el año (suma de columna E)
Bloque Gráficos pequeños (tercera fila, dos columnas):
	• Distribución por género (barras horizontales o dona)
	• Cupos NEEP totales vs ocupados (barras apiladas)
Bloque Niveles (gráfico principal):
	• Barra horizontal por nivel (27 barras), mostrando ocupación.
	• Al pasar el mouse: tooltip con capacidad total / ocupados / retirados / vacantes / % ocupación.
	• A la derecha de cada barra, número resumen: ocupados / capacidad.
Bloque Alertas (panel destacado):
	• Lista de alertas activas con icono, nombre del postulante y nivel: 
		○ 🟡 Aceptados sin matricular hace más de 15 días
		○ 🟠 En proceso sin movimiento hace más de 30 días
		○ 🟠 En entrevista hace más de 20 días
		○ 🔴 Nivel sin vacantes con nuevos postulantes (deberían ir a lista de espera)
Tabla resumen general (al final):
	• 27 filas (niveles), columnas: capacidad / ocupado / retirados / vacantes / en proceso / aceptados / matriculados / lista de espera / alertas / estado (DISPONIBLE/OCUPADO).
2.5 Vista 2 — Postulantes
Barra de filtros superior:
	• Buscador libre por apellido/nombre
	• Filtro por estado (multi-select)
	• Filtro por nivel
	• Filtro por motivo de término
	• Filtro por NEEP (Sí/No/Todos)
	• Filtro por hermanos en el colegio
	• Botón "Limpiar filtros"
	• Botón "Exportar CSV"
Tabla principal:
	• Columnas visibles: ID, apellidos, nombres, edad al postular, nivel, estado, días en proceso, teléfono, NEEP.
	• Click en una fila → modal lateral con la ficha completa del postulante (todos los campos del Sheet, incluyendo mails, fechas, notas, historial de cambios de este postulante).
	• Indicador visual de alertas en filas relevantes.
2.6 Vista 3 — Historial
Tabla cronológica inversa:
	• Columnas: fecha y hora, postulante (apellidos, nombres), nivel, cambio (estado anterior → estado nuevo).
	• Filtros: por rango de fechas, por postulante, por estado origen, por estado destino.
	• Botón "Exportar CSV".
2.7 Datos hardcodeados en el prototipo
Para el mock, usar un objeto JS al inicio del script con ~30 postulantes ficticios y la estructura de capacidad de los 27 niveles. Esto simula lo que la fase 3 leerá del Sheet real.
Criterio de aceptación Fase 2
	• Login funciona.
	• Las 3 vistas se ven bien en PC, tablet y móvil.
	• Los gráficos renderizan, los tooltips funcionan.
	• El selector de año está visible (aunque solo tenga "2027" en el mock).
	• Exportar CSV produce archivo descargable.
	• Apruebas el diseño visual antes de pasar a la conexión real.
