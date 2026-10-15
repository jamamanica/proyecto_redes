# 1. Portada
- **Universidad:** [Completar Nombre de la Universidad]
- **Facultad:** Facultad de Ingeniería de Sistemas e Informática
- **Curso:** Redes de Comunicación I
- **Docente:** [Nombre del Docente]
- **Título del Proyecto:** Diseño de la infraestructura física y cableado estructurado de una red LAN para el Policlínico y Centro Médico San Gabriel
- **Integrantes:**
  1. [Apellidos y Nombres - Integrante 1]
  2. [Apellidos y Nombres - Integrante 2]
  3. [Apellidos y Nombres - Integrante 3]
  4. [Apellidos y Nombres - Integrante 4]
  5. [Apellidos y Nombres - Integrante 5]
- **Fecha:** Octubre, 2026

---

# 2. Introducción
En la actualidad, las instituciones prestadoras de servicios de salud dependen de manera crítica de una infraestructura de telecomunicaciones robusta, segura y de alta disponibilidad. La digitalización de la salud exige que el acceso a historias clínicas electrónicas (EHR), la transmisión de órdenes de laboratorio, la visualización de imágenes diagnósticas y la facturación médica operen en tiempo real sin interrupciones ni latencias intolerables.

El presente proyecto aborda el diseño técnico de la infraestructura física y cableado estructurado para el **Policlínico y Centro Médico San Gabriel**, una entidad de salud ambulatoria que experimenta dificultades operativas debido a una red precaria e improvisada. El alcance de este trabajo se circunscribe a los fundamentos de redes y la capa física (Unidad I), aplicando normativas internacionales como ANSI/TIA-568, ISO/IEC 11801 y TIA-569, garantizando una topología escalable, segura y normalizada para dar soporte a más de 50 dispositivos terminales.

---

# 3. Descripción de la Organización
El **Policlínico San Gabriel** es un centro médico privado de atención ambulatoria que brinda servicios de medicina general, especialidades, diagnóstico por imágenes, laboratorio clínico y farmacia.

### 3.1. Características del Local
- **Ubicación y dimensiones:** Local de una sola planta con un área total construida de 450 m² (30 metros de largo por 15 metros de ancho).
- **Ambientes físicos:**
  1. **Área de Recepción, Admisión y Triaje:** 4 puestos de atención al público y control de signos vitales.
  2. **Consultorios Médicos (6 módulos):** Medicina General, Pediatría, Ginecología, Cardiología, Traumatología y Odontología.
  3. **Área de Diagnóstico y Laboratorio:** Toma de muestras, procesamiento analítico y sala de Rayos X digital.
  4. **Farmacia Institucional:** Atención al público y almacén de medicamentos.
  5. **Área Administrativa y Facturación:** Gerencia médica, contabilidad y facturación a aseguradoras.
  6. **Sala de Espera y Corredores:** Zona de libre circulación de pacientes.
  7. **Cuarto de Telecomunicaciones (MDF / Rack Room):** Ambiente técnico cerrado y climatizado (3 x 2.5 m) ubicado estratégicamente para no superar el límite de 90 metros de cableado horizontal hacia ningún extremo del inmueble.

---

# 4. Problemática
El Policlínico San Gabriel cuenta en la actualidad con una red informática deficiente caracterizada por los siguientes problemas críticos:
1. **Cableado informal ("en telaraña"):** Cables UTP tendidos por el suelo y sobre marcos de puertas sin canaletas ni protección, provocando daños mecánicos y desconexiones físicas frecuentes.
2. **Alta interferencia electromagnética (EMI):** Los cables de red transcurren en paralelo y pegados a las líneas eléctricas de 220V de alta potencia y cerca de equipos electromédicos (compresores dentales y centrífugas de laboratorio), generando pérdidas masivas de tramas por ruido.
3. **Puntos de falla no centralizados:** Empleo de mini-switches genéricos de 5 y 8 puertos en cascada escondidos bajo los escritorios, lo que genera cuellos de botella severos y dificulta aislar caídas de red.
4. **Falta de cobertura inalámbrica segura:** Empleo de routers caseros en modo Access Point que sufren saturación constante ante la presencia de pacientes y no cuentan con separación física de tráfico.
5. **Inseguridad física:** Servidor de base de datos médica y grabador de cámaras (NVR) expuestos en el escritorio de administración sin control de acceso ni sistema de respaldo energético (UPS).

---

# 5. Objetivos
### 5.1. Objetivo General
Diseñar y dimensionar técnicamente la infraestructura física y el sistema de cableado estructurado para la red de área local (LAN) del Policlínico San Gabriel, bajo las normativas ANSI/TIA-568 y TIA-569, garantizando un rendimiento Gigabit Ethernet, escalabilidad y alta fiabilidad en la transmisión de datos.

### 5.2. Objetivos Específicos
1. Identificar e inventariar la totalidad de equipos terminales y requerimientos de conectividad en cada ambiente del policlínico.
2. Seleccionar la topología física y los medios de transmisión más adecuados justificando técnicamente su resistencia a atenuación y ruido electromagnético.
3. Diseñar la distribución de cableado horizontal, áreas de trabajo y cuarto de comunicaciones respetando los límites de distancia y radios de curvatura normados.
4. Elaborar el plano de distribución física con rutas de canalización y ubicación precisa de tomas de datos, access points y rack central.
5. Definir la lista de materiales (BOM) y el plan de pruebas de certificación física para garantizar la operatividad de los enlaces instalados.

---

# 6. Requerimientos de Red
Se realizó el levantamiento de carga para dimensionar un total de **52 dispositivos activos y terminales** conectados a la infraestructura:

| Ambiente / Área | Dispositivos Terminales | Tipo de Conexión | Cantidad Puntos RJ-45 |
| :--- | :--- | :--- | :---: |
| **Admisión y Triaje** | 4 Computadoras de escritorio<br>2 Impresoras térmicas de tickets | Cableada (UTP Cat 6) | 6 |
| **Consultorios (6 salas)** | 6 Computadoras médicas (1 por sala)<br>2 Impresoras láser de red compartidas | Cableada (UTP Cat 6) | 8 |
| **Laboratorio y Rayos X** | 3 Computadoras de análisis<br>1 Analizador bioquímico con interfaz LAN<br>1 Impresora de código de barras | Cableada (UTP Cat 6) | 5 |
| **Farmacia** | 3 Computadoras de punto de venta (POS)<br>1 Impresora fiscal de red | Cableada (UTP Cat 6) | 4 |
| **Administración** | 5 Computadoras administrativas<br>1 Impresora multifuncional departamental | Cableada (UTP Cat 6) | 6 |
| **Vigilancia y Seguridad** | 8 Cámaras de seguridad IP (Alimentación PoE) | Cableada (UTP Cat 6 PoE) | 8 |
| **Puntos de Acceso Wi-Fi** | 4 Access Points de techo (MIMO corporativos) | Cableada (UTP Cat 6 PoE) | 4 |
| **Cuarto de Servidores** | 1 Servidor principal de Base de Datos / EHR<br>1 Servidor de respaldo NAS<br>1 Grabador de video NVR (16 canales) | Cableada (UTP Cat 6 directo) | 4 (con redundancia) |
| **Reserva / Crecimiento** | Previsión para futuras expansiones (15%) | Tomas ciegas en faceplates | 7 |
| **TOTAL PUNTOS DE RED** | **52 dispositivos operativos + reservas** | - | **52 tomas activas** |
