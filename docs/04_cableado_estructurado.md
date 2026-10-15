# Memoria Técnica - Unidad I: Redes de Comunicación I
## "Diseño de la infraestructura física y cableado estructurado de una red LAN para una Biblioteca"

> **Responsable:** Integrante 4  
> **Alcance de la sección:** Sección 11 de la Memoria Técnica (Normas de Cableado Estructurado, Subsistemas, Estándares T568A/B, Componentes del Rack y Procedimiento de Armado de Cable UTP para la Evaluación Práctica).

---

# 11. Cableado Estructurado

### 11.1. Marco Normativo Aplicable
El diseño se rige bajo los siguientes estándares internacionales de la industria de telecomunicaciones:
- **ANSI/TIA-568-C / ANSI/TIA-568.2-D:** Estándar de cableado de telecomunicaciones para edificios comerciales (especificaciones para componentes de par trenzado balanceado Categoría 6).
- **ANSI/TIA-569-D:** Estándar de espacios y canalizaciones de telecomunicaciones (dimensionamiento de ductos, radios de curvatura y cuarto de telecomunicaciones).
- **ANSI/TIA-606-B:** Estándar de administración y etiquetado para la infraestructura de telecomunicaciones.
- **ISO/IEC 11801:** Estándar internacional genérico de cableado para instalaciones de clientes.

---

### 11.2. Subsistemas de Cableado Estructurado Implementados

```
+-----------------------------------------------------------------------------------+
|                           SUBSISTEMAS EN LA BIBLIOTECA                             |
+-----------------------------------------------------------------------------------+
|  1. Acometida / Entrada del Proveedor (ISP)                                       |
|     Llega desde la vía pública hacia el Cuarto de Telecomunicaciones (MDF).       |
|                                                                                   |
|  2. Cuarto de Telecomunicaciones (MDF / Rack Central de 19")                      |
|     - Rack cerrado de 24U con cerradura de seguridad.                             |
|     - Patch Panels Cat 6 de 24 y 48 puertos.                                      |
|     - Switch Principal Gigabit PoE+ (48 puertos).                                 |
|     - Unidad de Respaldo Energético (UPS 1500 VA Online).                         |
|     - Organizadores de cables horizontales y verticales.                          |
|                                                                                   |
|  3. Cableado Horizontal (Tendido hacia Puntos de Datos)                           |
|     - Cables UTP Cat 6 (100% Cobre sólido 23 AWG, cubierta LSZH retardante a fuego)|
|     - Canaletas de PVC autoextinguibles de 2 vías con tabique separador.           |
|     - Distancia máxima en el proyecto: 38 metros (< 90 metros permitidos).        |
|                                                                                   |
|  4. Área de Trabajo (Work Area)                                                   |
|     - Rosetas / Faceplates de pared y suelo con Jacks Keystone Hembra RJ-45 Cat 6. |
|     - Patch cords flexibles de 1.5 m y 2.0 m hacia PCs de estudiantes y bibliotec.|
|     - Conexión directa a Access Points Wi-Fi 6 en techo.                          |
+-----------------------------------------------------------------------------------+
```

#### Regla de Distancias Máximas del Canal Horizontal (ANSI/TIA-568):
- **Enlace Permanente (Permanent Link):** Máximo **90 metros** de cable sólido entre la parte posterior del Patch Panel y el Jack Keystone del área de trabajo.
- **Cables de Parcheo (Patch Cords):** Máximo **10 metros** en total combinados (5 metros en el rack + 5 metros en el área de trabajo).
- **Longitud Total del Canal (Channel):** Máximo **100 metros**.
- *Cumplimiento en la Biblioteca:* El punto más lejano (AP-01 en el extremo de la sala de lectura) se ubica a **38 metros** de recorrido real por canaleta, cumpliendo holgadamente el estándar con más del 50% de margen de seguridad.

---

### 11.3. Estándares de Terminación: T568A vs. T568B

El estándar ANSI/TIA-568 define dos asignaciones pin/par para la conectorización de conectores y jacks RJ-45 de 8 pines:

| Pin | Estándar ANSI/TIA-568A | Estándar ANSI/TIA-568B *(Seleccionado)* | Función 1000BASE-T |
| :---: | :--- | :--- | :---: |
| **1** | Blanco / Verde | **Blanco / Naranja** | Par Bi-direccional A+ |
| **2** | Verde | **Naranja** | Par Bi-direccional A- |
| **3** | Blanco / Naranja | **Blanco / Verde** | Par Bi-direccional B+ |
| **4** | Azul | **Azul** | Par Bi-direccional C+ |
| **5** | Blanco / Azul | **Blanco / Azul** | Par Bi-direccional C- |
| **6** | Naranja | **Verde** | Par Bi-direccional B- |
| **7** | Blanco / Marrón | **Blanco / Marrón** | Par Bi-direccional D+ |
| **8** | Marrón | **Marrón** | Par Bi-direccional D- |

#### Justificación de la Elección de T568B:
Se adopta **T568B de extremo a extremo** para toda la instalación de la biblioteca (cable directo / *straight-through*). Esta decisión se sustenta en:
1. **Predominancia comercial:** Es el estándar más extendido en el mercado latinoamericano e internacional para instalaciones comerciales e institucionales.
2. **Consistencia total:** Al utilizar la misma norma (T568B) en los dos extremos (Patch Panel y Jack Keystone, así como en los Patch Cords), se garantiza una transmisión directa sin cruces y se facilita el mantenimiento a cualquier técnico externo futuro.

---

### 11.4. Guía Práctica de Armado del Cable UTP Físico (Para Evaluación y Exposición)

> ⚠️ **Requisito Obligatorio del Docente:**  
> *"Cada grupo debe mostrar un cable UTP funcional construido por los mismos integrantes, aplicando T568A o T568B. Durante la exposición se puede seleccionar aleatoriamente a un integrante para que explique el procedimiento de armado, el estándar utilizado y cómo comprobaría que el cable funciona correctamente."*

#### Herramientas y Materiales Requeridos:
- Tramo de cable UTP Categoría 6 (1.5 a 2 metros, 100% cobre).
- 2 conectores macho RJ-45 Categoría 6 (con contactos chapados en oro a 50µm).
- 2 capuchones protectores de goma para RJ-45.
- Tenaza crimpadora (crimping tool) para RJ-45 (8P8C).
- Pelacables de par trenzado o cuchilla de precisión.
- Tester probador de continuidad de cables de red RJ-45 (Master / Remote con 8 LEDs).

```
PASO A PASO PARA DEFENDER EN LA EXPOSICIÓN:
===========================================
Paso 1: Colocar los capuchones protectores en ambos extremos antes de crimpar.
Paso 2: Pelar aproximadamente 2.5 a 3 cm de la cubierta exterior de PVC con la pelacables, cuidando no mellar el cobre interior.
Paso 3: Cortar la cruceta plástica central (spline de Cat 6) al ras de la cubierta.
Paso 4: Destrenzar cuidadosamente los 4 pares y estirar cada conductor.
Paso 5: Ordenar los hilos según la norma T568B de izquierda a derecha:
        1. Blanco/Naranja
        2. Naranja
        3. Blanco/Verde
        4. Azul
        5. Blanco/Azul
        6. Verde
        7. Blanco/Marrón
        8. Marrón
Paso 6: Aplanar firmemente los hilos alineados y cortar en línea recta con la cuchilla de la crimpadora, dejando 1.2 cm a 1.4 cm expuestos.
Paso 7: Insertar los hilos en el conector RJ-45 empujando firmemente hasta que los 8 conductores toquen el fondo y se aprecien a través del plástico frontal transparente. Asegurar que la chaqueta externa de PVC entre dentro del cuerpo del conector (al menos 6 mm) para que quede trabada por la cuña de alivio de tensión.
Paso 8: Introducir el conector en la crimpadora y presionar con fuerza constante hasta escuchar el clic de compresión de las cuchillas metálicas en los pines de cobre.
Paso 9: Repetir exactamente el mismo proceso en el otro extremo (Norma T568B directa).
Paso 10: Comprobación con Tester de Red:
         Conectar un extremo en el puerto MASTER y el otro en el REMOTE.
         Encender el tester y verificar que los LEDs del 1 al 8 se enciendan uno por uno de forma secuencial y sincronizada en ambos módulos (1-1, 2-2, 3-3, 4-4, 5-5, 6-6, 7-7, 8-8).
```

---

### 11.5. Cuarto de Telecomunicaciones (MDF / Rack) y Componentes

El Rack principal de la Biblioteca se ubica en el cuarto técnico y consta de:
1. **Gabinete / Rack Metálico de 19 pulgadas y 24 Unidades de Rack (24U):** Con puerta frontal de vidrio templado, cerradura con llave y ventiladores superiores de extracción de aire.
2. **Patch Panels Cat 6 de 24 puertos (x2 unidades):** Con terminación posterior tipo 110/IDC para anclar el cableado sólido horizontal.
3. **Switch Gestionable PoE+ Gigabit de 48 Puertos:** Capaz de proveer datos a 1000 Mbps y suministrar energía eléctrica mediante IEEE 802.3at a los APs y cámaras IP.
4. **Organizadores Horizontales de 1U:** Instalados entre cada elemento activo y pasivo para peinar los patch cords y evitar peso sobre los puertos RJ-45.
5. **PDU (Unidad de Distribución de Energía) con Supresor de Picos:** 8 tomas de corriente estabilizada.
6. **Sistema UPS Online de 1500 VA / 900W:** Proporciona 30 a 45 minutos de autonomía frente a cortes eléctricos para preservar la integridad del switch, router y servidor.
7. **Barra de Puesta a Tierra (TGB - Telecommunications Grounding Busbar):** Conectada a la tierra del edificio mediante cable de cobre desnudo verde AWG #6.
