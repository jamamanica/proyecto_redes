# 📊 Estructura de las Diapositivas de Exposición (10 a 12 Láminas)
> **Tiempo total:** 20 minutos de exposición (4 min por persona) + 5 min de preguntas.
> **Regla de oro del docente:** *No lean teoría; defiendan las decisiones técnicas tomadas.*

---

### Diapositiva 1: Portada y Presentación del Equipo (1 min - Todos)
- **Título:** Diseño de la Infraestructura Física y Cableado Estructurado LAN.
- **Caso:** Policlínico y Centro Médico San Gabriel (52 dispositivos).
- **Curso:** Redes I - Unidad I.
- **Integrantes y roles:** Mencionar brevemente los nombres de los 5.

---

### Diapositiva 2: La Organización y su Problemática Actual (4 min - Integrante 1)
- **Contexto:** Policlínico de atención ambulatoria (450 m², 6 consultorios, laboratorio, triaje, farmacia).
- **Problema previo:** Red informal "en telaraña", switches en cascada bajo escritorios, interferencia por compresores dentales, caídas frecuentes en el sistema de historias clínicas.
- **Objetivo:** Implementar una red Gigabit certificada bajo normas ANSI/TIA-568.

---

### Diapositiva 3: Requerimientos y Dimensionamiento de Red (Integrante 1)
- **Inventario total:** 52 tomas activas.
  - 21 PCs (médicas, triaje, farmacia, laboratorio, administración).
  - 7 Impresoras de red (térmicas, láser, etiquetas).
  - 1 Analizador bioquímico en laboratorio.
  - 4 Access Points Wi-Fi 6 corporativos.
  - 8 Cámaras IP PoE 1080p.
  - Servidor central de historias clínicas EHR + NAS + NVR.

---

### Diapositiva 4: Topología Física y Lógica Seleccionada (4 min - Integrante 2)
- **Topología física:** **Estrella centralizada** convergente en el Rack del cuarto de comunicaciones (MDF).
- **¿Por qué Estrella?:** Aislamiento de fallas (si un cable se corta, solo cae un consultorio), administración centralizada y fácil escalabilidad.
- **Topología lógica:** Ethernet IEEE 802.3 conmutada (sin dominios de colisión por puerto).

---

### Diapositiva 5: Modelos OSI / TCP-IP y Flujo de Encapsulación (Integrante 2)
- Mapeo de capas en el entorno clínico (HTTP/HTTPS $\rightarrow$ TCP $\rightarrow$ IP $\rightarrow$ Ethernet $\rightarrow$ Bits).
- **Ejemplo concreto:** Médico solicitando una historia clínica:
  - *Datos $\rightarrow$ Segmento TCP (puerto 443) $\rightarrow$ Paquete IP $\rightarrow$ Trama Ethernet (MACs + FCS) $\rightarrow$ Bits (Codificación PAM-5).*

---

### Diapositiva 6: Capa Física y Selección de Medios (4 min - Integrante 3)
- **Señales y codificación:** Señal digital PAM-5 a 250 MHz para Gigabit Ethernet (1000BASE-T).
- **Retos físicos superados:** Atenuación controlada (distancia máx. de 42 m vs límite de 90 m) y mitigación de ruido electromagnético (separación de 20 cm de líneas de fuerza).
- **Decisión:** **UTP Categoría 6 LSZH** vs Fibra Óptica vs Coaxial.
  - *¿Por qué UTP Cat 6?:* Soporta 1 Gbps, permite alimentación PoE para cámaras y APs, bajo costo relativo y chaqueta cero halógenos (LSZH) obligatoria en salud.

---

### Diapositiva 7: Cableado Estructurado y Normas (4 min - Integrante 4)
- **Estándar:** ANSI/TIA-568.2-D y TIA-569.
- **Subsistemas:**
  - *Área de trabajo:* Faceplates dobles con jacks Keystone Cat 6.
  - *Cableado horizontal:* Tuberías y canaletas de PVC autoextinguibles sin exceder 90 metros.
  - *Cuarto de telecomunicaciones:* Ubicación centralizada y climatizada.

---

### Diapositiva 8: El Gabinete de Telecomunicaciones (Rack 24U) y Norma T568B (Integrante 4)
- **Rack de 19" (24U):** Switch 48 puertos PoE+, Patch Panel 48 puertos, Servidor EHR, NVR, UPS 2000VA de respaldo.
- **Norma de terminación:** **T568B** en ambos extremos (Blanco-Naranja, Naranja, Blanco-Verde, Azul, Blanco-Azul, Verde, Blanco-Marrón, Marrón).
- **Muestra física:** Exhibir el cable ponchado por el equipo.

---

### Diapositiva 9: Diseño y Plano Físico de la Red (4 min - Integrante 5)
- **Proyección del plano:** Mostrar el plano del policlínico con:
  - Ubicación del cuarto de servidores (MDF).
  - Trazado de la troncal de canaletas por el pasadizo central.
  - Distribución de puntos de red en consultorios, triaje y farmacia.
  - Cobertura de los 4 APs y ángulos de las 8 cámaras IP.

---

### Diapositiva 10: Lista de Materiales (BOM) y Presupuesto Técnico (Integrante 5)
- Cuadro resumen de componentes principales:
  - 2 Cajas de cable UTP Cat 6 LSZH (305m).
  - 1 Switch 48p Gigabit PoE+ / 1 Patch Panel 48p / Rack 24U.
  - 52 Jacks Keystone Cat 6 + 26 Faceplates dobles.
  - 4 APs Wi-Fi 6 + 8 Cámaras IP Domo.
  - UPS Online de 2000VA con autonomía de 45 minutos.

---

### Diapositiva 11: Plan de Pruebas de Certificación (Integrante 5 / Integrante 4)
- **Inspección mecánica:** Verificación de curvaturas y destrenzado menor a 13 mm.
- **Wiremap con Tester:** Continuidad 1 al 8, ausencia de cortos, circuitos abiertos o pares invertidos.
- **Certificación de canal:** Medición de atenuación, NEXT y pérdida de retorno a 250 MHz.
- **Demostración en vivo:** Encendido secuencial de los LEDs en el tester del cable fabricado por el equipo.

---

### Diapositiva 12: Conclusiones y Ronda de Preguntas (Todos)
- Infraestructura 100% normalizada bajo TIA-568 lista para soportar la digitalización del policlínico.
- Base física preparada para el direccionamiento IP y subneteo de la Unidad II.
- **Agradecimiento y apertura a preguntas del docente.**
