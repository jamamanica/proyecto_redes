# Memoria Técnica - Unidad I: Redes de Comunicación I
## "Diseño de la infraestructura física y cableado estructurado de una red LAN para una Biblioteca"

> **Responsable:** Integrante 1  
> **Alcance de la sección:** Secciones 1 a 6 de la Memoria Técnica (Portada, Introducción, Descripción de la Organización, Problemática, Objetivos y Requerimientos de Red).

---

# 1. Portada
- **Universidad:** [Completar Nombre de la Universidad]
- **Facultad:** Facultad de Ingeniería de Sistemas e Informática / Computación
- **Curso:** Redes de Comunicación I
- **Docente:** [Nombre del Docente]
- **Título del Proyecto:** Diseño de la infraestructura física y cableado estructurado de una red LAN para la Biblioteca Central "León Pinelo"
- **Integrantes (Grupo de 5):**
  1. **Integrante 1:** [Apellidos y Nombres] - *Análisis de la organización, problemática, requerimientos y objetivos*
  2. **Integrante 2:** [Apellidos y Nombres] - *Fundamentos, topologías, OSI/TCP-IP y encapsulación*
  3. **Integrante 3:** [Apellidos y Nombres] - *Capa física, señales y selección de medios de transmisión*
  4. **Integrante 4:** [Apellidos y Nombres] - *Cableado estructurado, normas, T568A/B, rack y componentes*
  5. **Integrante 5:** [Apellidos y Nombres] - *Plano físico, materiales, pruebas y consolidación de documentación*
- **Fecha:** Octubre, 2026

---

# 2. Introducción
Las bibliotecas modernas han evolucionado de ser simples repositorios pasivos de libros impresos a transformarse en centros dinámicos de recursos para el aprendizaje y la investigación (CRAI). En este entorno contemporáneo, el acceso instantáneo a catálogos en línea (OPAC), repositorios institucionales, bases de datos científicas internacionales, libros digitales y aulas virtuales es un servicio de primera necesidad tanto para estudiantes como para el personal bibliotecario.

Para posibilitar esta interacción digital, la infraestructura de telecomunicaciones física constituye los cimientos indispensables. Una red de área local (LAN) deficiente genera interrupciones constantes, frustración en los usuarios y cuellos de botella en la administración del patrimonio bibliográfico.

El presente proyecto técnico aborda el diseño integral de la infraestructura física y el sistema de cableado estructurado para la **Biblioteca**, una entidad educativa/cultural de mediana escala que atiende a cientos de usuarios diarios. Con base en los lineamientos de la Unidad I del curso Redes I, el diseño se fundamenta rigurosamente en la capa física y de enlace (modelos OSI y TCP/IP), así como en las normativas internacionales de telecomunicaciones **ANSI/TIA-568**, **TIA-569** e **ISO/IEC 11801**, garantizando una solución robusta, escalable, ordenada y de alto rendimiento para soportar entre 30 y 60 dispositivos simultáneos.

---

# 3. Descripción de la Organización
La entidad seleccionada para el proyecto es la **Biblioteca Central "León Pinelo"**, una institución de carácter académico y comunitario dedicada a la gestión de información, lectura, investigación y apoyo al aprendizaje.

### 3.1. Actividad y Servicios
- Préstamo y devolución automatizada de material bibliográfico físico.
- Consulta de catálogos en línea (OPAC) y préstamo de libros electrónicos.
- Zona de estudio silencioso individual e investigación especializada.
- Módulos de estudio grupal interactivo para trabajo colaborativo.
- Sala de cómputo y alfabetización digital con computadoras conectadas a Internet de alta velocidad.
- Servicios de reprografía, impresión en red y digitalización de documentos.

### 3.2. Características del Local y Ambientes Físicos
El local de la biblioteca comprende un piso de 500 m² (25 metros de fondo por 20 metros de ancho), con muros perimetrales de ladrillo y tabiquería interna de yeso (drywall) y vidrio templado en los cubículos de estudio. Los ambientes definidos son:
1. **Recepción, Préstamo y Módulo de Circulación (Área Administrativa):** 3 puestos de bibliotecarios encargados del registro y control.
2. **Sala de Cómputo e Investigación Estudiantil:** Espacio acondicionado con 16 computadoras de escritorio (PCs) destinadas al acceso a bases de datos y desarrollo de tareas académicas.
3. **Módulos de Consulta Rápida (Catálogo OPAC):** 4 terminales táctiles/PCs de consulta en pasillos principales.
4. **Sala de Lectura General y Silenciosa:** Área abierta con mesas de trabajo donde los estudiantes conectan sus laptops y dispositivos móviles.
5. **Cubículos de Estudio Grupal (3 salas):** Espacios cerrados con pantalla interactiva y puntos de red para trabajo en equipo.
6. **Oficina de Dirección Bibliotecaria y Procesos Técnicos:** 2 puestos para clasificación, catalogación y gestión general.
7. **Cuarto de Telecomunicaciones (MDF / Rack Room):** Ambiente técnico cerrado y seguro de 2.5 x 3.0 m, ubicado de manera equidistante para garantizar que ningún tiro de cable horizontal supere los 90 metros normados.

### 3.3. Población y Usuarios
- **Personal Bibliotecario y Administrativo:** 6 personas permanentes.
- **Estudiantes e Investigadores Concurrentes:** Aforo de hasta 70 personas en horas pico.

---

# 4. Problemática
Actualmente, la Biblioteca opera bajo una infraestructura improvisada que ha colapsado ante la creciente demanda digital. La situación actual se resume en los siguientes puntos críticos:

1. **Monopolio y saturación de un único Access Point (AP) doméstico:**
   - La biblioteca dispone de **un único router inalámbrico/AP doméstico** instalado en la recepción.
   - Dicho AP intenta brindar cobertura a todo el piso (500 m²). Cuando más de 10 a 15 personas intentan conectarse simultáneamente, el dispositivo se satura, provoca caídas masivas de la señal Wi-Fi, cortes en la conexión y pérdidas de paquetes severas.
2. **"Zonas muertas" y atenuación extrema por estanterías de libros:**
   - Las estanterías metálicas densamente cargadas de libros impresos actúan como pantallas atenuadoras de radiofrecuencia (absorción y dispersión de señal electromagnética en 2.4 GHz y 5 GHz). Los cubículos de estudio y la sala de cómputo no reciben prácticamente cobertura del único AP existente.
3. **Inexistencia de puestos fijos cableados para estudiantes:**
   - Los estudiantes que asisten a investigar no cuentan con tomas de red cableada confiables, dependiendo exclusivamente del Wi-Fi inestable.
   - La sala de cómputo para estudiantes cuenta con equipos aislados o conectados mediante mini-switches caseros en cascada, lo que produce una navegación extremadamente lenta y fallos de enlace constantes.
4. **Interferencia entre tráfico administrativo y tráfico de estudiantes:**
   - Todo el tráfico (préstamo de libros del bibliotecario, búsquedas de catálogo, descargas de estudiantes e invitados) compite en el mismo medio físico y de transmisión, sin priorización ni segmentación física de puertos.
5. **Riesgo físico y desorden en el cableado:**
   - Los pocos cables existentes están tendidos por el zócalo o cruzando pasillos con cinta adhesiva, representando un peligro de tropiezo para los usuarios y riesgo de daño mecánico al cable UTP.

---

# 5. Objetivos
### 5.1. Objetivo General
Diseñar y dimensionar técnicamente la infraestructura física y el sistema de cableado estructurado de una red de área local (LAN) para la **Biblioteca Central**, cumpliendo los estándares internacionales **ANSI/TIA-568**, **TIA-569** e **ISO/IEC 11801**, asegurando conectividad Gigabit cableada de alta confiabilidad y una distribución estratégica de múltiples Access Points para abastecer con eficiencia a estudiantes y bibliotecarios.

### 5.2. Objetivos Específicos
1. **Relevar y clasificar los requerimientos de conectividad:** Inventariar los dispositivos finales (PCs de estudiantes, puestos de bibliotecarios, terminales OPAC, impresoras, servidores y APs) para un total proyectado de entre 30 y 60 nodos activos.
2. **Distribuir la cobertura inalámbrica:** Reemplazar el único AP doméstico mediante la distribución estratégica de 4 Access Points empresariales de doble banda con alimentación PoE (*Power over Ethernet*), cubriendo equitativamente la sala de lectura, cubículos y área administrativa.
3. **Dotar de infraestructura Gigabit Ethernet cableada a los puestos estudiantiles:** Diseñar el cableado horizontal en Categoría 6 para 16 PCs en la sala de cómputo y 4 módulos OPAC, eliminando switches en cascada.
4. **Diseñar el subsistema de cuarto de telecomunicaciones y cableado horizontal:** Centralizar las conexiones en un Rack estándar de 19 pulgadas provisto de Patch Panels, Switch PoE gestionable y organizadores de cables.
5. **Elaborar los planos físicos y la lista de materiales (BOM):** Detallar la ubicación física de rosetas RJ-45, canaletas, bandejas portacables, rack y metrado de cable UTP.
6. **Definir el plan de pruebas físicas:** Establecer el protocolo de verificación de continuidad, mapa de cables (T568B), atenuación y certificación del enlace físico permanente.

---

# 6. Requerimientos de Red
Para garantizar un dimensionamiento preciso acorde a la pauta del docente (entre 30 y 60 dispositivos conectados), se ha elaborado la siguiente matriz de requerimientos de puntos de red (nodos físicos y nodos Wi-Fi concurrentes):

### 6.1. Inventario de Dispositivos y Nodos de Conexión

| Ambiente | Dispositivo / Elemento | Tipo de Conexión | Cantidad | Descripción Técnica |
| :--- | :--- | :--- | :---: | :--- |
| **Sala de Cómputo Estudiantil** | PCs de Escritorio para Estudiantes | Cableado UTP Cat 6 | **16** | Búsqueda académica, redacción y tareas. |
| **Pasillos / Entrada** | Terminales de Consulta OPAC | Cableado UTP Cat 6 | **4** | Búsqueda rápida de libros en catálogo digital. |
| **Cubículos Grupales (3)** | Puntos de Red en Mesa de Trabajo | Cableado UTP Cat 6 | **6** | 2 puntos dobles por cubículo para laptops de estudiantes. |
| **Cubículos Grupales (3)** | Pantallas Interactivas / Smart TVs | Cableado UTP Cat 6 | **3** | Presentaciones y exposiciones colaborativas. |
| **Recepción y Circulación** | PCs de Bibliotecarios | Cableado UTP Cat 6 | **3** | Control de préstamos, altas y bajas de material. |
| **Recepción y Circulación** | Impresora / Multifuncional de Red | Cableado UTP Cat 6 | **1** | Impresión de fichas, carnés y documentos. |
| **Dirección y Procesos** | PCs Administrativas | Cableado UTP Cat 6 | **2** | Catalogación técnica y gerencia bibliotecaria. |
| **Cuarto de Telecomunicaciones** | Servidor Local Catálogo / NAS | Cableado UTP Cat 6 | **1** | Servidor de base de datos bibliográfica y almacenamiento. |
| **Techo / Muros Distribuidos** | Access Points Empresariales (Wi-Fi) | Cableado UTP Cat 6 (PoE) | **4** | AP-01 (Lectura), AP-02 (Cómputo), AP-03 (Cubículos), AP-04 (Recepción). |
| **Seguridad Perimetral** | Cámaras de Seguridad IP | Cableado UTP Cat 6 (PoE) | **4** | Vigilancia en accesos, pasillos y sala de lectura. |
| **Reserva / Crecimiento Futuro** | Puntos adicionales en Patch Panel | Cableado UTP Cat 6 | **7** | Proyección del 15% para ampliaciones. |
| **TOTAL PUNTOS CABLEADOS (PATCH PANEL)** | - | - | **51** | **Distribuidos en 2 Patch Panels de 24 y 48 puertos.** |

### 6.2. Usuarios Inalámbricos Concurrentes (Capacidad de los APs)
- **AP-01 (Sala de Lectura Silenciosa):** Capacidad para 30-40 conexiones simultáneas (estudiantes con laptops y tablets).
- **AP-02 (Sala de Cómputo):** Capacidad para 20 dispositivos concurrentes (smartphones y laptops complementarias).
- **AP-03 (Cubículos de Estudio):** Capacidad para 20 conexiones simultáneas.
- **AP-04 (Recepción y Sala de Espera):** Capacidad para 15 conexiones simultáneas (personal y usuarios en tránsito).

### 6.3. Condiciones Ambientales y Físicas
- Alimentación eléctrica estabilizada con sistema de puesta a tierra (< 5 Ohmios).
- Respaldo energético mediante Sistema de Alimentación Ininterrumpida (UPS) en el rack principal.
- Canalizaciones no compartidas con líneas eléctricas de alta tensión, respetando la distancia mínima de 20 cm para mitigar la inducción electromagnética.
