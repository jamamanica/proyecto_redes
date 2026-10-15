# 📊 Estructura y Guion de Diapositivas para la Exposición (10 a 12 Láminas)
> **Tiempo total:** 20 minutos de exposición (4 min por persona) + 5 min de preguntas individuales (25 min total).  
> **Regla de oro del docente:** *No lean teoría abstracta; defiendan con convicción las decisiones técnicas de ingeniería.*

---

### Diapositiva 1: Portada y Presentación del Equipo (1 min - Presentador General / Integrante 1)
- **Título:** Diseño de la Infraestructura Física y Cableado Estructurado LAN.
- **Caso de Estudio:** Biblioteca Central "León Pinelo" (51 puntos cableados + cobertura Wi-Fi distribuida).
- **Curso:** Redes de Comunicación I - Unidad I.
- **Equipo Consultor:** Presentación de los 5 integrantes y asignación de roles técnicos.

---

### Diapositiva 2: La Organización y Problemática Actual (4 min - Integrante 1)
- **Contexto:** Biblioteca de 500 m² con salas de lectura, cubículos grupales, cómputo y módulos de atención.
- **Problemática Principal:** 
  - Monopolio de **un único Access Point doméstico** que colapsaba ante la concurrencia simultánea.
  - Zonas muertas por atenuación severa provocada por la densidad de estanterías metálicas y libros de papel.
  - Inexistencia de puestos Ethernet cableados fijos para los estudiantes en las salas de consulta e investigación.
- **Objetivo del Proyecto:** Diseñar una red LAN Gigabit normalizada (ANSI/TIA-568) con segmentación de puestos fijos y Wi-Fi multi-AP.

---

### Diapositiva 3: Matriz de Requerimientos y Dimensionamiento (Integrante 1)
- **Censo de Dispositivos (51 puntos totales):**
  - 16 PCs en Sala de Cómputo para estudiantes.
  - 4 Terminales táctiles OPAC para búsqueda de libros.
  - 6 Puestos de trabajo en cubículos grupales + 3 Smart TVs interactivas.
  - 3 PCs para bibliotecarios en recepción y circulación + 1 Impresora multifuncional de red.
  - 2 PCs en dirección y catalogación técnica.
  - 4 Access Points empresariales Wi-Fi 6 alimentados por PoE.
  - 4 Cámaras IP perimetrales + Servidor local NAS de catálogo.
  - 7 Puntos de reserva y proyección futura (15%).

---

### Diapositiva 4: Topología Física y Lógica Seleccionada (4 min - Integrante 2)
- **Topología Física:** **Estrella Centralizada** en el Cuarto de Telecomunicaciones (MDF / Rack 24U).
- **Defensa Técnica:**
  - Tolerancia a fallas: El corte de un cable en una mesa de lectura no afecta al resto de la biblioteca.
  - Mantenimiento y certificación centralizados en el Patch Panel.
  - Exigencia estricta de la norma ANSI/TIA-568 (prohibición de buses y cascadas en cableado horizontal).
- **Topología Lógica:** Ethernet conmutada (IEEE 802.3) para los enlaces fijos y CSMA/CA (IEEE 802.11ax) para el espectro inalámbrico.

---

### Diapositiva 5: Modelos OSI / TCP-IP y Flujo de Encapsulación (Integrante 2)
- Mapeo de capas en la biblioteca: Aplicación (OPAC web) $\rightarrow$ Transporte (TCP) $\rightarrow$ Red (IP) $\rightarrow$ Enlace (Ethernet MAC) $\rightarrow$ Física (Bits).
- **Caso Práctico:** Alumno buscando un libro en el catálogo digital:
  - *Generación de datos HTTP $\rightarrow$ Creación de Segmento TCP (puerto destino 80/443) $\rightarrow$ Paquete IP con direcciones lógicas $\rightarrow$ Trama Ethernet con MAC y verificación CRC-32 (FCS) $\rightarrow$ Codificación eléctrica PAM-5 sobre los 4 pares de cobre.*

---

### Diapositiva 6: Capa Física y Selección Justificada de Medios (4 min - Integrante 3)
- **Desafíos Físicos Superados:**
  - Atenuación de RF: Cálculo de pérdidas por barreras de estanterías resuelto mediante distribución de 4 APs.
  - Ruido electromagnético (EMI): Separación de 20-30 cm entre canaletas de datos y cables de fuerza 220V.
- **Matriz de Decisión: ¿Por qué UTP Cat 6 y no Fibra ni Coaxial?:**
  - *Coaxial:* Obsoleto y sin capacidad Gigabit.
  - *Fibra Óptica:* Costo excesivo e innecesario para distancias menores a 40 metros; fragilidad mecánica en puestos estudiantiles.
  - *UTP Cat 6 100% Cobre:* Soporta 1 Gbps a 250 MHz, permite alimentación **PoE+ (IEEE 802.3at)** para alimentar los APs sin cables eléctricos en el techo, y bajo costo por punto.

---

### Diapositiva 7: Cableado Estructurado y Normativas (4 min - Integrante 4)
- **Normas Aplicadas:** ANSI/TIA-568.2-D, TIA-569-D (Canalizaciones) y TIA-606-B (Etiquetado).
- **Subsistemas Implementados:**
  - Área de trabajo (Faceplates y jacks Keystone Cat 6).
  - Cableado horizontal (Tendido en canaletas PVC con tabique separador; distancia máxima en la biblioteca: 38 m < 90 m permitidos).
  - Cuarto de telecomunicaciones (Rack cerrado 24U, Patch Panels, Switch PoE 48p, PDU y UPS 1500VA).
- **Estándar de Terminación:** Elección de **T568B** homogéneo en ambos extremos (consistencia industrial y facilidad de mantenimiento).

---

### Diapositiva 8: Demostración Práctica del Cable UTP (Integrante 4)
- **Presentación en Vivo del Cable Físico:** Explicación del procedimiento de armado:
  - Pelado cuidadoso sin mellar conductores, corte de cruceta interna (spline), destrenzado mínimo (< 13 mm).
  - Código de colores T568B (Blanco/Naranja, Naranja, Blanco/Verde, Azul, Blanco/Azul, Verde, Blanco/Marrón, Marrón).
  - Crimpado con compresión homogénea y alojamiento de chaqueta PVC dentro del conector RJ-45.
- **Demostración de Funcionamiento:** Prueba en vivo con el Tester de Red verificando el encendido secuencial de los 8 LEDs.

---

### Diapositiva 9: Plano de Distribución Física y Rutas (4 min - Integrante 5)
- **Visualización del Plano Arquitectónico (500 m²):**
  - Ubicación estratégica del Rack (MDF) en posición equidistante.
  - Dispersión de los 4 APs en cielo raso para cobertura 100% libre de sombras de estanterías.
  - Distribución de las 16 PCs en la Sala de Cómputo y los módulos OPAC en pasillos.
  - Rutas de canaleta troncal dorsal (100x50 mm) y derivaciones hacia puestos de lectura.

---

### Diapositiva 10: Presupuesto de Materiales (BOM) y Plan de Pruebas (Integrante 5)
- **Resumen Cuantitativo:** 2 bobinas UTP Cat 6 cobre sólido (610 m), 1 Switch PoE 48 puertos, 2 Patch Panels 24 puertos, 1 Rack 24U, 4 APs Wi-Fi 6, 55 jacks Keystone, canaletas y UPS.
- **Protocolo de Pruebas de Certificación:**
  1. Inspección visual y radios de curvatura.
  2. Wiremap test (verificación de continuidad y descarte de pares cruzados/divididos).
  3. Enlace activo a 1000 Mbps con 0% pérdida de paquetes ICMP.

---

### Diapositiva 11: Conclusiones y Defensa Técnica (Todos)
- Se sustituyó un esquema informal e ineficiente por una infraestructura LAN corporativa que garantiza 1 Gbps para estudiantes e investigadores.
- La solución es escalable, modular y cumple al 100% la normativa ANSI/TIA para proyectos de ingeniería.

---

### Diapositiva 12: Ronda de Preguntas y Respuestas (5 min - Todos)
- Preparación del equipo para responder las preguntas individuales y aleatorias del docente sobre cualquier sección del proyecto.
