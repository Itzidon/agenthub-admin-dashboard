# AgentHub — Especificación del Panel de Administración

## Descripción del producto

AgentHub es una plataforma SaaS que permite a empresas alquilar agentes de IA preconfigurados. Estos agentes pueden tener distintas skills, como navegación web, lectura de documentos, gestión de calendarios o análisis de datos.

El usuario principal del panel es un administrador interno de AgentHub. Este administrador necesita revisar métricas generales, usuarios, agentes, skills disponibles, contrataciones y errores de ejecución.

## Stack tecnológico y restricciones

- HTML semántico.
- Tailwind CSS cargado exclusivamente vía CDN.
- JavaScript vanilla.
- Sin React, Vue, Angular ni frameworks.
- Sin jQuery.
- Sin backend ni llamadas a API.
- Todos los datos estarán hardcodeados.
- El prototipo se construirá en `index.html`.
- No se usarán archivos CSS personalizados ni estilos inline.
- El modo oscuro se implementará usando clases `dark:` de Tailwind.

## Layout general

1. El panel tendrá una barra lateral persistente visible en escritorio.
2. La barra lateral incluirá navegación a las seis secciones:
   - Dashboard
   - Gestión de usuarios
   - Gestión de agentes
   - Skills
   - Contrataciones
   - Log de errores
3. La sección activa tendrá un indicador visual destacado.
4. La parte superior tendrá un header con:
   - Título de la sección actual.
   - Toggle de modo claro/oscuro.
   - Nombre del administrador hardcodeado.
5. El contenido principal estará dentro de `main`.
6. El diseño debe ser responsive para escritorio y tablet.

---

## Sección 1: Dashboard

### Componentes

1. Cuatro tarjetas de métricas en grid 2x2 en tablet y 4 columnas en escritorio.
2. Cada tarjeta incluirá:
   - Icono.
   - Etiqueta.
   - Valor hardcodeado.
   - Color de acento distinto.
3. Las métricas serán:
   - Ingresos totales del mes.
   - Pérdidas por descuentos y cupones.
   - Agentes activos.
   - Agentes fallando.
4. Debajo de las tarjetas habrá un bloque de ancho completo representando un gráfico de actividad semanal.

### Datos hardcodeados

- Ingresos totales: 48.250 €
- Pérdidas por descuentos: 3.420 €
- Agentes activos: 128
- Agentes fallando: 7

### Comportamiento

1. El gráfico será un placeholder visual con barras o líneas simuladas.
2. No tendrá datos dinámicos.
3. Debe adaptarse al modo oscuro.

---

## Sección 2: Gestión de usuarios

### Componentes

1. Tabla con al menos 5 usuarios.
2. Columnas:
   - Nombre
   - Email
   - Plan
   - Estado
   - Acciones
3. Cada estado se mostrará como badge.
4. Cada fila tendrá un botón `⋮`.
5. El botón abrirá un dropdown con:
   - Ver detalle
   - Eliminar

### Comportamiento

1. Al hacer clic en `Ver detalle`, se abrirá un modal.
2. El modal mostrará el registro completo del usuario.
3. El modal se cerrará con botón de cierre.
4. El modal también se cerrará al hacer clic en el backdrop.
5. Los dropdowns se cerrarán al hacer clic fuera.

---

## Sección 3: Gestión de agentes

### Componentes

1. Listado con al menos 4 agentes.
2. Cada agente mostrará:
   - Nombre del agente.
   - Propietario.
   - Estado actual.
   - Lista de skills colapsada.
   - Dropdown de acciones.
3. Estados posibles:
   - Activo
   - Inactivo
   - Fallando
4. El dropdown tendrá:
   - Configurar
   - Eliminar

### Comportamiento

1. Las skills estarán ocultas por defecto.
2. Un botón expandible mostrará u ocultará las skills.
3. La apertura y cierre tendrá transición suave.
4. `Configurar` abrirá un modal.
5. El modal contendrá el prompt de sistema del agente dentro de un `textarea`.
6. El modal se cerrará con botón de cierre y backdrop.

---

## Sección 4: Skills

### Componentes

1. Texto introductorio explicando qué es una skill en AgentHub.
2. Catálogo con al menos 4 skills.
3. Cada skill mostrará:
   - Nombre.
   - Descripción breve.
   - Número de agentes que la tienen habilitada.
   - Dropdown de acciones.
4. Dropdown con:
   - Ver detalle
   - Eliminar

### Comportamiento

1. `Ver detalle` abrirá un modal con información ampliada de la skill.
2. El modal se cerrará con botón y backdrop.
3. Los dropdowns se cerrarán al hacer clic fuera.

---

## Sección 5: Contrataciones de agentes

### Componentes

1. Tabla con al menos 4 contratos.
2. Columnas:
   - Cliente
   - Agente alquilado
   - Skills contratadas
   - Fechas del contrato
   - Importe pagado
   - Acciones
3. Cada fila tendrá dropdown con:
   - Ver detalle
   - Eliminar

### Comportamiento

1. `Ver detalle` abrirá un modal.
2. El modal mostrará:
   - Cliente.
   - Agente.
   - Fechas.
   - Importe total.
   - Lista desglosada de skills contratadas.
   - Precio individual de cada skill.
3. El modal se cerrará con botón y backdrop.

---

## Sección 6: Log de errores

### Componentes

1. Listado con al menos 6 errores.
2. Cada error mostrará:
   - Timestamp.
   - Nombre del agente.
   - Tipo de error.
   - Badge de gravedad.
   - Descripción breve.
   - Dropdown de acciones.
3. Gravedades:
   - Baja
   - Media
   - Alta
   - Crítica

### Comportamiento

1. `Ver detalle` abrirá un modal con la traza completa del error.
2. `Marcar como resuelto` cambiará visualmente el estado del error.
3. El modal se cerrará con botón y backdrop.
4. Los badges tendrán colores distintos según gravedad.

---

## Interacciones globales

1. El toggle de modo oscuro/claro cambiará todo el panel.
2. El modo elegido se mantendrá al navegar entre secciones.
3. Todos los dropdowns se cerrarán al hacer clic fuera.
4. Solo puede haber un dropdown abierto a la vez.
5. Todos los modales se cerrarán con:
   - Botón de cierre.
   - Clic en backdrop.
6. Las secciones se mostrarán mediante navegación interna en la misma página.
7. No habrá navegación real entre páginas.

---

## Inventario de componentes reutilizables

- Sidebar.
- Header superior.
- Tarjeta de métrica.
- Badge de estado.
- Badge de gravedad.
- Dropdown de acciones.
- Modal reutilizable.
- Tabla.
- Lista colapsable de skills.
- Toggle de modo oscuro.
- Placeholder de gráfico.

---

## Criterios de aceptación

1. Existe un archivo `SPECS.md` en la raíz del repositorio.
2. `SPECS.md` está commiteado antes que `index.html`.
3. El prototipo incluye las seis secciones requeridas.
4. La navegación lateral permite acceder a todas las secciones.
5. El Dashboard muestra cuatro tarjetas de métricas y un gráfico placeholder.
6. Gestión de usuarios muestra al menos 5 usuarios.
7. Cada usuario tiene dropdown funcional.
8. `Ver detalle` de usuario abre un modal.
9. Gestión de agentes muestra al menos 4 agentes.
10. Las skills de los agentes están colapsadas por defecto.
11. Las skills se expanden y colapsan con transición.
12. `Configurar` abre un modal con textarea editable.
13. Skills muestra al menos 4 skills.
14. Contrataciones muestra al menos 4 contratos.
15. El detalle de contrato muestra skills y precios individuales.
16. Log de errores muestra al menos 6 errores.
17. Los errores tienen badges de gravedad con colores diferenciados.
18. `Marcar como resuelto` cambia el estado visual del error.
19. El modo oscuro/claro cambia todo el panel.
20. Los dropdowns se cierran al hacer clic fuera.
21. Los modales se cierran con botón y backdrop.
22. No se usa ningún framework.
23. No se usa backend.
24. Tailwind se carga únicamente vía CDN.
25. Todos los datos son hardcodeados.