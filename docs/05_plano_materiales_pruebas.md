# 12. Diseño Físico y Plano de Red

### 12.1. Distribución de Ambientes y Recorrido de Cableado
El local del Policlínico San Gabriel cuenta con una superficie de $30\text{ m} \times 15\text{ m}$ ($450\text{ m}^2$) en una sola planta.

**Ubicación Estratégica del Cuarto de Telecomunicaciones (MDF):**
- Se localiza en la zona central-posterior del edificio, equidistante a las áreas clínicas, administrativas y de recepción.
- Esta ubicación central permite que la longitud máxima de cableado horizontal hacia el punto más distante (cámara perimétrica frontal exterior) sea de apenas **42 metros**, cumpliendo ampliamente con la norma ANSI/TIA-568 que fija un límite máximo de 90 metros de enlace permanente.

### 12.2. Mapa Esquemático de Ambientes y Puntos de Red

```text
+-----------------------------------------------------------------------------------------+
|                               POLICLÍNICO SAN GABRIEL                                   |
|   (Dimensiones: 30 metros de largo x 15 metros de ancho - Altura de techo: 3 metros)    |
+------------------------------------+--------------------------+-------------------------+
| CONSULTORIOS MÉDICOS (6)           | LABORATORIO & RAYOS X    | ADMISIÓN Y TRIAJE       |
| - 6 Puntos PC Médicas              | - 3 Puntos PC Análisis   | - 4 Puntos PC Admisión  |
| - 2 Puntos Impresoras Láser        | - 1 Punto Analizador     | - 2 Puntos Imp. Tickets |
| [AP-01 Wi-Fi Techo]                | - 1 Punto Imp. Etiquetas | [AP-02 Wi-Fi Techo]     |
| (Total: 8 puntos)                  | (Total: 5 puntos)        | (Total: 6 puntos)       |
+------------------------------------+--------------------------+-------------------------+
|                                    PASADIZO CENTRAL                                     |
|    ==== Troncal de Canaletas PVC 100x50mm con cables UTP Cat 6 hacia el Rack =====     |
+------------------------------------+--------------------------+-------------------------+
| FARMACIA INSTITUCIONAL             | CUARTO TELECOM (MDF)     | ADMINISTRACIÓN          |
| - 3 Puntos POS / Ventas            | [ GABINETE RACK 24U ]    | - 5 Puntos PC Oficina   |
| - 1 Punto Impresora Fiscal         | - Patch Panel 48 puertos | - 1 Punto Impresora MF  |
| [AP-03 Wi-Fi Techo]                | - Switch 48p PoE+        | [AP-04 Wi-Fi Techo]     |
| (Total: 4 puntos)                  | - Servidor EHR + NVR     | (Total: 6 puntos)       |
+------------------------------------+--------------------------+-------------------------+
| PERÍMETRO Y CORREDORES: 8 Cámaras IP PoE fijadas en esquinas estratégicas               |
+-----------------------------------------------------------------------------------------+
```

---

# 13. Lista de Materiales y Equipos (Bill of Materials - BOM)

| Ítem | Descripción Técnica del Material / Equipo | Cantidad | Unidad | Función en la Red |
| :---: | :--- | :---: | :---: | :--- |
| **1** | Cable UTP Categoría 6, 4 pares 23 AWG, Cobre 100%, Chaqueta LSZH (Caja de 305 m) | 2 | Cajas | Tendido del cableado horizontal en todo el local |
| **2** | Gabinete Rack de piso de 19", 24U, fondo 800mm, puertas microperforadas | 1 | Unidad | Alojamiento y protección física de equipos centrales |
| **3** | Switch Administrable de 48 puertos Gigabit 10/100/1000 Mbps PoE+ (370W) | 1 | Unidad | Conmutación de red y energización de APs y cámaras |
| **4** | Patch Panel Cat 6 de 48 puertos RJ-45, 1U para Rack de 19" | 1 | Unidad | Terminación y ordenamiento del cableado horizontal |
| **5** | Módulos Jack RJ-45 Cat 6 hembra tipo Keystone (Color blanco) | 52 | Unidades | Conectores hembra en las placas de pared |
| **6** | Placas de pared (Faceplates) de 2 puertos con ventana para rotulación | 26 | Unidades | Montaje de los jacks en las áreas de trabajo |
| **7** | Patch Cords UTP Cat 6 certificados de fábrica de 1 metro (Azul) | 48 | Unidades | Interconexión entre Patch Panel y Switch en el Rack |
| **8** | Patch Cords UTP Cat 6 certificados de fábrica de 2 metros (Gris) | 44 | Unidades | Conexión de PCs, impresoras y analizador a la pared |
| **9** | Puntos de Acceso (Access Points) Wi-Fi 6 Corporativos PoE (Ceiling Mount) | 4 | Unidades | Cobertura inalámbrica para personal médico y público |
| **10** | Cámaras de seguridad IP Tipo Domo 1080p PoE antivandálicas | 8 | Unidades | Videovigilancia de accesos y corredores |
| **11** | Sistema UPS Online de 2000VA / 1800W con tarjeta SNMP (Montaje en Rack 3U) | 1 | Unidad | Respaldo eléctrico continuo y filtrado de armónicos |
| **12** | Organizadores horizontales de cableado de 1U con tapa para Rack 19" | 2 | Unidades | Ruteo prolijo de patch cords dentro del gabinete |
| **13** | Canaleta de PVC autoextinguible $100 \times 50\text{ mm}$ con división interna (2m) | 25 | Tramos | Troncal principal de distribución en pasadizos |
| **14** | Canaleta de PVC autoextinguible $40 \times 25\text{ mm}$ con adhesivo (2m) | 30 | Tramos | Bajadas verticales a los escritorios y equipos |
| **15** | Conectores RJ-45 macho Cat 6 con contactos bañados en oro (Bolsa x 100) | 1 | Bolsa | Ponchado de tramos de cámaras, APs y cable de muestra |

---

# 14. Plan de Pruebas y Certificación de Cableado

Para validar la correcta instalación física antes de energizar los equipos se ejecutarán tres niveles de prueba:

### 14.1. Inspección Visual y Mecánica
- Verificación del radio de curvatura del cable UTP (mínimo 4 veces el diámetro exterior, ~25 mm) para evitar deformación del trenzado.
- Comprobación de la fijación de canaletas y ausencia de compresión excesiva con abrazaderas plásticas.
- Inspección del destrenzado en los jacks y conectores: no debe superar los **13 mm (0.5 pulgadas)** de acuerdo con ANSI/TIA-568.

### 14.2. Prueba de Mapa de Cables (Wiremap) con Tester Básico
Se probarán el 100% de los 52 enlaces utilizando un probador digital de continuidad RJ-45:
- **Verificación de continuidad:** Encendido correlativo de los pines del 1 al 8.
- **Detección de fallas comunes:**
  - *Circuito abierto:* Uno o más hilos desconectados o no prensados por el pin del RJ-45.
  - *Cortocircuito:* Dos hilos en contacto accidental por rebaba de cobre.
  - *Pares cruzados:* Inversión accidental de pines (por ejemplo conectar T568A en un extremo y T568B en el otro creando un cable cruzado).
  - *Pares divididos (Split pairs):* Error de ponchado donde se mezclan hilos de distintos pares afectando drásticamente el trenzado y la cancelación de ruido.

### 14.3. Prueba de Certificación de Canal Permanente (Certificador de Campo)
Se contempla el escaneo de enlaces con un analizador de cables de red (tipo Fluke DSX CableAnalyzer) para medir:
- **Longitud física real:** Cálculo mediante reflectometría en el dominio del tiempo (TDR).
- **Pérdida de inserción (Atenuación):** Pérdida de potencia en dB a 250 MHz (debe ser inferior a los límites de Cat 6).
- **NEXT (Near-End Crosstalk):** Nivel de ruido inducido en el extremo cercano entre pares (debe superar el umbral mínimo exigido).
- **Pérdida de retorno (Return Loss):** Reflexiones de señal provocadas por desajustes de impedancia característica ($100\ \Omega \pm 15\%$).

---

# 15. Conclusiones
1. **Cumplimiento de estándares internacionales:** El diseño basado en la norma ANSI/TIA-568 garantiza una infraestructura de categoría 6 con vida útil proyectada superior a 10 años, capaz de soportar tecnologías de red actuales y futuras.
2. **Topología física robusta:** La adopción de una topología en estrella con centro de cableado único en el MDF elimina los cuellos de botella y puntos únicos de fallo que sufría la clínica con su red anterior.
3. **Optimización de costos y recursos:** La selección de cable UTP Cat 6 frente a la fibra óptica multimodo resultó ser la solución óptima, ya que cubrió holgadamente las distancias requeridas (máximo 42 metros) permitiendo alimentar simultáneamente los puntos de acceso y cámaras vía PoE+.
4. **Seguridad y continuidad del servicio:** La inclusión de un gabinete cerrado bajo llave y un sistema UPS online garantiza la integridad física de los servidores de historias clínicas y la operación ininterrumpida ante eventuales cortes eléctricos.

---

# 16. Referencias Bibliográficas (Formato APA 7ma Ed.)
- Telecommunications Industry Association. (2018). *Balanced Twisted-Pair Telecommunications Cabling and Components Standard* (ANSI/TIA-568.2-D). TIA.
- Telecommunications Industry Association. (2019). *Telecommunications Pathways and Spaces* (ANSI/TIA-569-D). TIA.
- Tanenbaum, A. S., & Wetherall, D. J. (2012). *Redes de computadoras* (5.ª ed.). Pearson Educación.
- Kurose, J. F., & Ross, K. W. (2017). *Redes de computadores: Un enfoque descendente* (7.ª ed.). Pearson Educación.
- Stallings, W. (2014). *Comunicaciones y Redes de Computadores* (7.ª ed.). Prentice Hall.
- Cisco Systems. (2020). *Ethernet Technologies and Structured Cabling Systems*. Cisco Press.

---

# 17. Anexos
- **Anexo A:** Diagrama lógico de bloques y flujo de encapsulación.
- **Anexo B:** Ficha técnica (Datasheet) de referencia del Cable UTP Cat 6 LSZH y Switch PoE+.
- **Anexo C:** Evidencia fotográfica del armado y verificación del cable UTP bajo norma T568B elaborado por el equipo.
