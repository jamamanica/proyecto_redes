# Memoria Técnica - Unidad I: Redes de Comunicación I
## "Diseño de la infraestructura física y cableado estructurado de una red LAN para una Biblioteca"

> **Responsable:** Integrante 3  
> **Alcance de la sección:** Secciones 9 y 10 de la Memoria Técnica (Sistemas y Medios de Comunicación, Conceptos de Capa Física y Selección Justificada de Medios de Transmisión).

---

# 9. Sistemas y Medios de Comunicación

### 9.1. Conceptos Fundamentales de la Capa Física

#### A. Señales y Naturaleza de la Transmisión
En el entorno de la Biblioteca coexisten dos tipos de medios y señales:
- **Señales Eléctricas Conducidas (Cobre - UTP Cat 6):** La información binaria se transmite como variaciones de potencial eléctrico (voltaje) sobre conductores de cobre balanceados. Bajo el estándar 1000BASE-T (Gigabit Ethernet), se utiliza la modulación **PAM-5 (Pulse Amplitude Modulation de 5 niveles)** a una frecuencia de símbolo de 125 MBaudios por par, transmitiendo simultáneamente y de forma bidireccional (full-duplex) en los 4 pares trenzados.
- **Señales Electromagnéticas No Conducidas (Radiofrecuencia - Wi-Fi 6 / IEEE 802.11ax):** Los bits modulan ondas de radio en el espectro no licenciado de **2.4 GHz y 5 GHz** mediante modulaciones avanzadas como **1024-QAM** y división de frecuencias ortogonales (**OFDMA**), permitiendo la conexión de laptops y smartphones de los estudiantes.

#### B. Ancho de Banda y Tasa de Bits (Throughput)
- **Ancho de Banda Analógico del Medio:** Capacidad espectral máxima de frecuencia que soporta el canal físico sin degradación excesiva. El cable UTP Categoría 6 certificado soporta un ancho de banda de hasta **250 MHz** (en contraste con los 100 MHz de Cat 5e).
- **Tasa de Bits Nominal:** Tasa máxima teórica de transferencia digital. En la LAN cableada de la biblioteca es de **1000 Mbps (1 Gbps)** por nodo.
- **Rendimiento Real (Throughput):** Medida neta de datos útiles transferidos por segundo, descontando la sobrecarga (overhead) de encabezados de capa de enlace, IP y TCP.

#### C. Factores de Degradación en la Biblioteca: Atenuación, Ruido y Distorsión

```
   Señal Original Emisor                Pérdida por Atenuación y Ruido              Señal Degradada Receptor
   +---+       +---+                    +--.       .--+                             +~-~.    .-~-+
   |   |       |   |      =========>    |   \     /   |   +  [ Ruido EMI/RFI ] ===> |    \  /    |
   +   +-------+   +                    +    +---+    +                             +     ++     +
```

1. **Atenuación:** Pérdida progresiva de potencia de la señal a medida que viaja por el medio.
   - *En el cable UTP:* Se debe a la resistencia óhmica natural del cobre y a pérdidas dieléctricas. La norma ANSI/TIA-568 establece un límite estricto de **90 metros de enlace permanente** para asegurar que la atenuación no supere los umbrales admisibles en 250 MHz.
   - *En el medio inalámbrico (RF en la Biblioteca):* Fenómeno crítico en el proyecto. **Las estanterías metálicas compactas y los libros de papel denso actúan como poderosos atenuadores de señal RF**, absorbiendo y reflejando las microondas. Por esta razón, el diseño reemplaza el único AP central por 4 APs distribuidos con línea de vista en cada zona funcional.
2. **Ruido e Interferencia Electromagnética (EMI) y de Radiofrecuencia (RFI):**
   - Causado por balastros de lámparas fluorescentes en techos de la biblioteca, cableado de potencia eléctrica de 220 VAC y motores de sistemas de aire acondicionado.
   - *Mitigación:* Se respeta rigurosamente una separación mínima de **20 a 30 cm** entre las canaletas de datos y los conductores de electricidad, cruzándose en ángulo recto (90°) cuando sea inevitable.
3. **Diafonía (Crosstalk) y NEXT / FEXT:**
   - Interferencia inductiva entre pares adyacentes del mismo cable. En Cat 6, la presencia de una **cruceta plástica interna (spline)** mantiene físicamente separados los cuatro pares trenzados a lo largo de todo el cable, reduciendo drásticamente el NEXT (*Near-End Crosstalk*).

---

# 10. Selección y Justificación Técnica de Medios de Transmisión

### 10.1. Matriz Comparativa de Medios Físicos

| Criterio de Selección | Cable Coaxial (RG-6 / RG-58) | Fibra Óptica Monomodo/Multimodo (OM3/OM4) | Par Trenzado UTP Categoría 6 (Cobre) |
| :--- | :--- | :--- | :--- |
| **Ancho de Banda** | Bajo (hasta 10-100 MHz en redes base). | Extremadamente alto (> 10-100 GHz). | **Alto (hasta 250 MHz / 1-10 Gbps).** |
| **Distancia Máxima** | 185 m a 500 m (redes antiguas). | De 300 m (Multimodo) a más de 10-40 km. | **100 m totales (90 m permanente + 10 m patch cords).** |
| **Costo por Punto** | Bajo a medio (obsoleto en LAN). | Alto (transceivers ópticos, fusiones caras). | **Muy Económico y con máxima disponibilidad en el mercado.** |
| **Inmunidad a Ruido EMI** | Moderada (malla metálica). | Total (100% inmune, transmite fotones de luz). | **Alta si se respeta el trenzado, spline y separación de 220V.** |
| **Facilidad de Conectorización**| Fácil pero engorroso en masa. | Compleja (requiere fusionadora, corte de precisión). | **Rápida mediante crimpado RJ-45 y jacks keystone punch-down.** |
| **Soporte de PoE (Power over Ethernet)**| Nulo. | Nulo (no conduce electricidad). | **Excelente (estándar IEEE 802.3at PoE+ hasta 30W por puerto).** |

---

### 10.2. Justificación Técnica de la Elección: UTP Categoría 6 (100% Cobre)

Para la red LAN de la Biblioteca se ha elegido **Cable de Par Trenzado UTP Categoría 6 (Unshielded Twisted Pair, 100% Cobre, calibre 23 AWG)** para el 100% del cableado horizontal, sustentado en las siguientes razones de ingeniería:

1. **Rendimiento Sobrado y Garantizado (1000BASE-T a 1 Gbps):**
   - La distancia máxima requerida desde el Rack central hasta la toma de red más alejada en la biblioteca es de **38 metros**, situándose holgadamente por debajo del límite normativo de 90 metros. A esta distancia, Cat 6 entrega 1 Gbps estable a 250 MHz sin degradación.
2. **Capacidad Nativa para Alimentación PoE+ (IEEE 802.3at):**
   - Los 4 Access Points distribuidos en el techo de la biblioteca y las 4 cámaras de seguridad IP se alimentan eléctricamente a través del mismo cable de red UTP Cat 6 directamente desde el Switch PoE del rack. Esto elimina la necesidad de contratar electricistas para tender tomas de 220V en el cielo raso, reduciendo costos y riesgos de sobrecalentamiento.
3. **Costo-Beneficio frente a la Fibra Óptica:**
   - La fibra óptica se descartó para el cableado horizontal debido a su elevado costo innecesario para distancias menores a 40 metros y a la fragilidad mecánica en tomas expuestas al uso constante de estudiantes. (La fibra queda reservada únicamente para la acometida del proveedor de Internet ISP que ingresa al Rack).
4. **Descarte del Cable Coaxial:**
   - El cable coaxial es una tecnología obsoleta para redes de área local conmutadas modernas, incompatible con switches de alta densidad y estándares Gigabit Ethernet actuales.
5. **Requisito Crítico de Material: Conductor 100% Cobre (No CCA):**
   - Se especifica cable de cobre sólido puro (Bare Copper) y se prohíbe taxativamente el uso de cable CCA (*Copper Clad Aluminum* / aluminio bañado en cobre), ya que el CCA presenta alta resistencia óhmica, genera excesiva caída de tensión con PoE y tiende a quebrarse con facilidad durante el tendido en canaletas.
