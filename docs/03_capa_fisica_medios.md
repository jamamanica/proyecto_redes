# 9. Sistemas y Medios de Comunicación

### 9.1. Naturaleza de las Señales en la Capa Física
En el Policlínico San Gabriel, la transmisión de información a través del cableado de cobre se realiza mediante **señales digitales** representadas por variaciones discretas de voltaje eléctrico.
- **Técnica de modulación/codificación:** Para Gigabit Ethernet (1000BASE-T), se utiliza la modulación **PAM-5 (Pulse Amplitude Modulation de 5 niveles)**: $-2V, -1V, 0V, +1V, +2V$. Esto permite transmitir 2 bits de información por cada símbolo en cada uno de los 4 pares de forma bidireccional y simultánea (full-duplex) a una frecuencia de símbolo de 125 Mbaudios ($125 \times 2 \times 4 = 1000\text{ Mbps}$).

### 9.2. Conceptos Físicos Clave Aplicados
1. **Ancho de Banda Analógico vs. Digital:**
   - *Ancho de banda analógico (Frecuencia):* El cable UTP Categoría 6 certificado opera con un ancho de banda de hasta **250 MHz**, lo que determina su capacidad para transportar señales de alta frecuencia sin degradación severa.
   - *Tasa de bits (Bitrate):* Capacidad nominal máxima de transmisión, fijada en **1000 Mbps (1 Gbps)** por enlace.
   - *Throughput (Rendimiento real):* Tasa efectiva de transferencia de datos útiles entre las estaciones de trabajo y el servidor, estimada en ~940 Mbps debido al overhead de las cabeceras de protocolo.
2. **Atenuación:**
   - Es la pérdida progresiva de potencia de la señal eléctrica a medida que se propaga a lo largo del conductor de cobre, causada por la resistencia óhmica natural del cable.
   - *Mitigación:* Se respeta estrictamente el límite normativo de **90 metros de cableado horizontal** más 10 metros en patch cords (100 m de canal completo). La distancia máxima medida en el plano del policlínico es de **42 metros**, garantizando márgenes de atenuación seguros muy por debajo del límite de pérdida admisible.
3. **Ruido e Interferencia Electromagnética (EMI):**
   - Causado por campos electromagnéticos parásitos generados por fluorescentes, motores de compresores dentales y líneas eléctricas de fuerza.
   - *Mitigación:* Separación mínima de 20 cm entre las canaletas de datos y las tuberías eléctricas, además de cruces perpendiculares a 90° cuando sea inevitable.
4. **Diafonía (Crosstalk - NEXT / FEXT):**
   - Fenómeno por el cual la señal electromagnética de un par trenzado induce una corriente espuria no deseada en el par adyacente dentro del mismo cable.
   - *Mitigación de Cat 6:* El cable Categoría 6 cuenta con un **separador plástico cruciforme (spline central)** que aísla físicamente los 4 pares trenzados a lo largo de todo el cable, garantizando altos valores de margen NEXT (Near-End Crosstalk).

---

# 10. Selección y Justificación del Medio de Transmisión

### 10.1. Cuadro Comparativo de Medios Físicos

| Criterio | Cable Coaxial (RG-6 / RG-58) | Par Trenzado UTP Cat 6 | Fibra Óptica Multimodo (OM4) |
| :--- | :--- | :--- | :--- |
| **Velocidad Soportada** | Hasta 10-100 Mbps (obsoleto en LAN) | 1 Gbps (hasta 100m) / 10 Gbps (<55m) | 10 Gbps / 40 Gbps / 100 Gbps |
| **Ancho de Banda** | 10 - 350 MHz | **250 MHz** | > 4700 MHz·km |
| **Distancia Máxima** | 185m - 500m (según tipo) | **100 metros (canal)** | 550 metros (a 10 Gbps) |
| **Inmunidad a EMI** | Media (malla metálica) | Media-Alta (por trenzado y spline) | **Inmunidad Total** (haz de luz) |
| **Costo de Materiales** | Bajo | **Económico y accesible** | Alto (transceivers y cables caros) |
| **Costo de Mano de Obra** | Sencillo pero en desuso | **Bajo y herramientas estándar** | Muy alto (fusionadora de fibra) |
| **Flexibilidad de Tendido** | Rígido | **Alta flexibilidad en canaleta** | Frágil (radio de curvatura crítico) |
| **Soporte de PoE** | Nulo | **Total (PoE 802.3af/at para APs/cámaras)** | No transporta electricidad |

---

### 10.2. Justificación Técnica de la Elección del UTP Categoría 6

Para el Policlínico San Gabriel se determinó el uso exclusivo de **Cable UTP (Unshielded Twisted Pair) Categoría 6 de 4 pares trenzados (23 AWG)** con cubierta **LSZH (Low Smoke Zero Halogen)** por las siguientes razones de ingeniería:

1. **Rendimiento Óptimo para el Tráfico:** Satisface con creces el requerimiento de transferencia de imágenes de Rayos X (archivos DICOM de 15 a 50 MB) y el streaming continuo de 8 cámaras IP de alta definición a 1080p sin latencias.
2. **Soporte Nativo de Alimentación Remota (PoE+):** El cable UTP permite transportar datos y corriente eléctrica simultáneamente bajo el estándar IEEE 802.3at hacia los 4 Access Points de techo y las 8 cámaras de videovigilancia, eliminando la necesidad de costosos tomacorrientes en el cielo raso.
3. **Seguridad en Ambientes de Salud (Cubierta LSZH):** Por tratarse de un centro médico con presencia de pacientes vulnerables, la normativa hospitalaria exige cables con cubierta cero halógenos que no emitan gases tóxicos ni humos opacos en caso de incendio.
4. **Relación Costo-Beneficio frente a la Fibra:** Como el área del policlínico es de 450 m² y la distancia máxima de tendido al punto más lejano es de solo 42 metros, la fibra óptica representaría un sobrecosto innecesario en tarjetas de red y transceptores ópticos SFP sin brindar una ventaja perceptible en la capa de acceso.
