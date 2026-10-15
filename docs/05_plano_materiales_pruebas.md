# Memoria Técnica - Unidad I: Redes de Comunicación I
## "Diseño de la infraestructura física y cableado estructurado de una red LAN para una Biblioteca"

> **Responsable:** Integrante 5  
> **Alcance de la sección:** Secciones 12 a 17 de la Memoria Técnica (Diseño Físico y Plano de Ambientes, Lista de Materiales / BOM, Plan de Pruebas de Cableado, Conclusiones, Referencias APA y Anexos).

---

# 12. Diseño Físico y Plano de Ambientes

### 12.1. Distribución Espacial de la Biblioteca (Planta de 25m x 20m = 500 m²)
La biblioteca cuenta con una distribución rectangular optimizada para el flujo de estudiantes y personal. A continuación se presenta el croquis técnico de distribución de áreas, ubicación del Rack (MDF), Access Points (APs) en techo y puestos de red cableados:

```text
+-------------------------------------------------------------------------------------------------------+
|  BIBLIOTECA CENTRAL - PLANO DE DISTRIBUCIÓN FÍSICA Y PUNTOS DE RED (500 m2)                           |
+----------------------------------------------------+--------------------------------------------------+
| [CUBÍCULOS DE ESTUDIO GRUPAL - 3 SALAS]            | [SALA DE LECTURA SILENCIOSA E INVESTIGACIÓN]    |
| (6 tomas de red dobles en mesas + 3 Smart TVs)     | (Mesas de lectura amplia para laptops / tablets) |
|                                                    |                                                  |
|  +--------------+  +--------------+  +-----------+ |       (( AP-01 ))  [En techo - Wi-Fi 6]          |
|  | Cubículo 1   |  | Cubículo 2   |  |Cubículo 3 | |                                                  |
|  | 2 Pts + TV   |  | 2 Pts + TV   |  | 2 Pts + TV| |   [Mesa 1]   [Mesa 2]   [Mesa 3]   [Mesa 4]      |
|  +--------------+  +--------------+  +-----------+ |                                                  |
|         (( AP-03 )) [En pasillo cubículos]         |   [Mesa 5]   [Mesa 6]   [Mesa 7]   [Mesa 8]      |
|                                                    |                                                  |
+====================== CANALETA DORSAL PRINCIPAL (PVC 100x50 mm) =====================================+
| [SALA DE CÓMPUTO ESTUDIANTIL]                      | [PASILLO Y ACCESO]       | [RECEPCIÓN Y PRÉST.]  |
| 16 PCs para estudiantes conectadas por Ethernet    | 4 Módulos OPAC Catálogo  | 3 Puestos Bibliotec.  |
|                                                    |                          | 1 Impresora de Red    |
| [PC 01] [PC 02] [PC 03] [PC 04]                    |   [OPAC 1]   [OPAC 2]    |                       |
| [PC 05] [PC 06] [PC 07] [PC 08]                    |                          | [Biblio 1] [Biblio 2] |
|       (( AP-02 )) [En techo Cómputo]               |   [OPAC 3]   [OPAC 4]    | [Biblio 3] [Imp Red]  |
| [PC 09] [PC 10] [PC 11] [PC 12]                    |                          |       (( AP-04 ))     |
| [PC 13] [PC 14] [PC 15] [PC 16]                    |                          |                       |
+----------------------------------------------------+--------------------------+-----------------------+
| [CUARTO TÉCNICO / MDF] (2.5 x 3.0 m)               | [DIRECCIÓN Y CATALOGAC.] | [ACCESO PRINCIPAL]    |
| +------------------------------------------------+ | 2 Puestos Administrativ. | Molinete y Seguridad  |
| | [RACK 24U]                                     | |                          | 1 Cámara IP Domo      |
| | Patch Panels, Switch PoE 48p, UPS, Servidor NAS| | [Dir 1]    [Catalog 2]   |                       |
| +------------------------------------------------+ |                          |                       |
+----------------------------------------------------+--------------------------+-----------------------+
```

### 12.2. Leyenda de Simbología y Rutas de Canalización
- **`[RACK 24U]` (Cuarto MDF):** Centro neurálgico donde convergen todos los cables UTP horizontales.
- **`(( AP-01 a 04 ))`:** Puntos de Access Point PoE montados en el cielo raso a una altura de 2.8 metros para garantizar línea de vista y evitar zonas de sombra provocadas por las estanterías de libros.
- **`[PC 01 a 16]`:** Puntos de datos dobles montados en canaleta perimetral de zócalo a 30 cm del piso en la sala de cómputo.
- **Canalización Troncal:** Canaleta plástica de PVC rígido de alto impacto (100 mm x 50 mm) de dos vías con tabique interno divisorio para aislar totalmente las rutas de datos frente a las de alimentación eléctrica de 220V.
- **Canalización Secundaria / Derivaciones:** Canaleta de PVC 40 mm x 25 mm hacia cada puesto de trabajo y tubos conduit corrugados flexibles sobre el falso techo para la bajada hacia los APs.

---

# 13. Lista de Equipos y Materiales (BOM - Bill of Materials)

A continuación se detalla la lista de materiales pasivos y activos dimensionados para la instalación física:

| Ítem | Categoría | Descripción Técnica / Modelo Sugerido | Cantidad | Unidad | Justificación en el Proyecto |
| :---: | :--- | :--- | :---: | :---: | :--- |
| **1** | Cable Pasivo | Bobina Cable UTP Cat 6, 100% Cobre Sólido, 23 AWG, Chaqueta LSZH (305 metros) | **2** | Cajas | Para el tendido de los 51 puntos de red horizontales (aprox. 550 metros totales requeridos). |
| **2** | Activo Red | Switch Gestionable Gigabit 48 Puertos PoE+ (IEEE 802.3at, Budget 370W) | **1** | Unidad | Núcleo de conmutación LAN; alimenta los 4 APs y 4 Cámaras IP por PoE y conecta todas las PCs. |
| **3** | Pasivo Rack | Patch Panel Modular Cat 6 de 24 Puertos, formato 19", 1U, conexión tipo 110/IDC | **2** | Unidades | Remate ordenado de las 51 líneas sólidas de cableado horizontal en el rack. |
| **4** | Pasivo Rack | Gabinete / Rack de Piso Metálico de 19", 24U de altura, puerta frontal de cristal | **1** | Unidad | Aloja de forma segura y centralizada el equipamiento activo y pasivo en el cuarto técnico. |
| **5** | Activo Wi-Fi | Access Point Empresarial Wi-Fi 6 (Dual Band 2.4/5 GHz, PoE 802.3at) | **4** | Unidades | Despliegue de cobertura inalámbrica sectorizada (Cómputo, Lectura, Cubículos y Recepción). |
| **6** | Pasivo Toma | Conector Hembra Jack Keystone Cat 6 RJ-45 (contactos 50µm oro) | **55** | Unidades | 51 tomas activas + 4 de repuesto para las áreas de trabajo. |
| **7** | Pasivo Toma | Placa de pared (Faceplate) de 2 salidas tipo americana | **25** | Unidades | Soporte estético y mecánico para los Jacks Keystone en muros y mesas. |
| **8** | Conexión | Conector Macho RJ-45 Cat 6 con guías y capuchones protectores | **50** | Unidades | Para armado de cables de prueba y terminales de APs y cámaras. |
| **9** | Parcheo | Patch Cord de Par Trenzado Cat 6 moldeado de fábrica (1.5 m) color azul | **51** | Unidades | Conexión entre Patch Panel y Switch en el Rack. |
| **10**| Parcheo | Patch Cord de Par Trenzado Cat 6 moldeado de fábrica (2.0 m) color gris | **25** | Unidades | Conexión entre Faceplate y tarjeta de red de las PCs de estudiantes y bibliotecarios. |
| **11**| Canalización | Canaleta PVC rígido 100x50 mm con división interna (tramos de 2 m) | **30** | Tramos | Troncal principal de distribución en pasillos. |
| **12**| Canalización | Canaleta PVC rígido 40x25 mm con adhesivo y fijación mecánica (tramos de 2 m)| **40** | Tramos | Derivación a puestos individuales en sala de cómputo y módulos de atención. |
| **13**| Energía | Sistema UPS Online de 1500 VA / 900W con onda senoidal pura | **1** | Unidad | Respaldo y filtrado eléctrico para el Switch, Router y Servidor NAS del rack. |
| **14**| Energía | PDU multitoma para rack de 19" (8 tomas NEMA 5-15R con breaker térmico) | **1** | Unidad | Distribución de corriente alterna limpia dentro del gabinete. |
| **15**| Gestión | Organizador de cables horizontal de 19" 1U con tapa desmontable | **2** | Unidades | Orden y peinado de los patch cords entre patch panel y switch. |

---

# 14. Plan de Pruebas y Certificación de Cableado

Para validar la correcta operatividad física de la red instalada antes de su entrega y puesta en producción, se ejecutará el siguiente plan de pruebas secuenciales:

```
+-----------------------------------------------------------------------------------------+
|                          FLUJO DEL PLAN DE PRUEBAS DE CAPA FÍSICA                       |
+-----------------------------------------------------------------------------------------+
| [Prueba 1: Inspección Visual] ===> [Prueba 2: Mapeo de Pines] ===> [Prueba 3: Enlace]  |
|  - Radios de curvatura             - Continuidad 8 hilos            - Autonegociación   |
|  - Código de colores T568B         - Cortocircuitos                 - Tráfico 1000 Mbps |
|  - Crimpado correcto sin holguras  - Pares divididos / cruzados     - Test de Bit Errors|
+-----------------------------------------------------------------------------------------+
```

### 14.1. Pruebas Básicas de Laboratorio
1. **Inspección Visual Mecánica (TIA-568.2-D):**
   - Verificar que no exista más de **13 mm (0.5 pulgadas)** de cable destrenzado en los conectores RJ-45 o jacks keystone.
   - Constatar que la chaqueta exterior de PVC ingrese adecuadamente en el conector RJ-45 quedando fijada bajo la pestaña plástica de alivio de esfuerzo.
   - Comprobar que los radios de curvatura del cable UTP Cat 6 no sean menores a **4 veces el diámetro exterior del cable** (mínimo 25 mm) en esquinas y curvas de canaleta para evitar microfracturas del conductor.
2. **Prueba de Continuidad y Mapeo de Hilos (Wiremap Test):**
   - Utilización del **Tester probador de red digital RJ-45**.
   - Conectar un extremo al transmisor (Master) y el otro al receptor (Remote).
   - *Criterio de Aceptación:* Secuencia correlativa ininterrumpida de los 8 LEDs del 1 al 8.
   - *Detección de Defectos:*
     - **Circuito Abierto (Open):** Falta de contacto en un pin (LED no enciende).
     - **Cortocircuito (Short):** Dos o más conductores se tocan (múltiples LEDs encienden a la vez).
     - **Par Cruzado (Reversal):** Inversión de hilos (ej. encendido de pines 1 y 2 invertido).
     - **Pares Divididos (Split Pairs):** Error crítico donde se mezclan hilos de distintos pares trenzados manteniendo continuidad pin a pin pero perdiendo la cancelación inductiva.
3. **Prueba de Enlace Activo y Autonegociación (Link & Speed Test):**
   - Conectar una laptop de pruebas con NIC Gigabit a la roseta del área de trabajo y el otro extremo al Switch PoE Gigabit.
   - Verificar que el LED indicador del switch y la tarjeta de red confirmen sincronización a **1000 Mbps Full-Duplex** (color ámbar o verde según el fabricante).
   - Ejecución de pruebas de envío de paquetes ICMP (`ping -t -l 1472`) hacia el router/servidor para validar 0% de pérdidas de tramas.

---

# 15. Conclusiones

1. **Resolución Integral de la Problemática:** El reemplazo del único punto de acceso doméstico por una infraestructura combinada de **4 Access Points Wi-Fi 6 empresariales (PoE)** y **16 puestos fijos Gigabit Ethernet para estudiantes** soluciona de raíz los cuellos de botella, la saturación por alta concurrencia y las zonas muertas causadas por la densidad física de las estanterías de libros.
2. **Cumplimiento Riguroso de la Capa Física y Normativas:** El proyecto se diseñó bajo las pautas de ANSI/TIA-568-C y TIA-569-D. La longitud máxima alcanzada en el recorrido más extenso es de 38 metros, respetando el límite de 90 metros del enlace permanente y asegurando un margen de atenuación óptimo a 250 MHz.
3. **Estandarización y Eficiencia de Mantenimiento:** La adopción homogénea de la norma **T568B** en todos los componentes (jacks keystone, patch panels y cables armados) garantiza consistencia técnica, reduce el tiempo de diagnóstico de incidencias y asegura compatibilidad con cualquier técnico calificado.
4. **Eficiencia de Costos mediante PoE:** La alimentación eléctrica a través del cable de datos para APs y cámaras IP redujo sustancialmente los costos de instalación al prescindir de cableado eléctrico de 220V en falso techo, elevando los niveles de seguridad contra incendios en un ambiente con alto volumen de papel inflamable.

---

# 16. Referencias Bibliográficas (Formato APA 7ma Edición)

- Telecommunications Industry Association. (2018). *Balanced Twisted-Pair Telecommunications Cabling and Components Standard* (ANSI/TIA-568.2-D). TIA Standards.
- Telecommunications Industry Association. (2015). *Telecommunications Pathways and Spaces* (ANSI/TIA-569-D). TIA Standards.
- International Organization for Standardization. (2017). *Information technology — Generic cabling for customer premises* (ISO/IEC 11801-1:2017). ISO.
- Kurose, J. F., & Ross, K. W. (2021). *Computer Networking: A Top-Down Approach* (8th ed.). Pearson.
- Tanenbaum, A. S., Feamster, N., & Wetherall, D. (2021). *Computer Networks* (6th ed.). Pearson.
- Stallings, W. (2017). *Data and Computer Communications* (10th ed.). Pearson.

---

# 17. Anexos

### Anexo A: Especificación de Canalizaciones y Factores de Llenado (TIA-569)
- El porcentaje de ocupación inicial de las canaletas principales no excede el **40% de su capacidad transversal**, dejando un 60% de holgura para futuras expansiones de cableado sin comprometer la ventilación ni ejercer presión mecánica indebida.

### Anexo B: Registro Fotográfico del Cable UTP Construido por el Grupo
*(Aquí se incluirán las fotos del cable confeccionado por los integrantes para la presentación práctica ante el docente).*
- Foto 1: Pelado y orden de colores bajo norma T568B antes del crimpado.
- Foto 2: Conector RJ-45 Cat 6 insertado en la crimpadora.
- Foto 3: Cable terminado con sus capuchones protectores.
- Foto 4: Prueba con Tester de Red mostrando la secuencia correlativa de los 8 LEDs.
