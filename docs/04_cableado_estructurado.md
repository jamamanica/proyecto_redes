# 11. Sistema de Cableado Estructurado

### 11.1. Normativa y Estándares de Referencia
El diseño de la red del Policlínico San Gabriel se rige bajo los siguientes estándares de la industria de telecomunicaciones:
- **ANSI/TIA-568.2-D:** Estándar de cableado y componentes de par trenzado balanceado (especificaciones para Categoría 6).
- **ANSI/TIA-569-D:** Estándar para espacios y canalizaciones de telecomunicaciones en edificios comerciales (cuartos de telecomunicaciones, ductos y bandejas).
- **ANSI/TIA-606-B:** Estándar de administración y etiquetado para infraestructuras de telecomunicaciones (nomenclatura de puertos y cables).
- **ANSI/TIA-607-C:** Requerimientos de puesta a tierra y unión para telecomunicaciones.

---

### 11.2. Subsistemas de Cableado Estructurado Implementados

1. **Área de Trabajo (Work Area):**
   - Comprende los componentes desde la toma de pared (faceplate) hasta las computadoras, impresoras o equipos médicos.
   - Cada puesto dispone de una placa de pared (**Faceplate de 2 puertos**) con módulos **Jack RJ-45 hembra Cat 6 tipo Keystone**.
   - Conexión del equipo al jack mediante un **Patch Cord UTP Cat 6 de fábrica de 2 metros**.
2. **Cableado Horizontal (Horizontal Cabling):**
   - Tramo continuo que va desde la salida del jack en el área de trabajo hasta el Patch Panel en el cuarto de telecomunicaciones.
   - **Regla de los 90 metros:** Ningún enlace permanente excede los 90 metros (la distancia máxima medida en el plano es de 42 metros).
   - Canalización: Canaletas de PVC no propagadoras de llama de $100 \times 50\text{ mm}$ para las troncales de distribución y $40 \times 25\text{ mm}$ para las bajadas a los puestos de trabajo.
3. **Cuarto de Telecomunicaciones (MDF / Telecommunications Room):**
   - Habitación dedicada de $3.00 \times 2.50\text{ metros}$ con puerta metálica y cerradura de seguridad.
   - Sistema de ventilación y aire acondicionado independiente manteniendo temperatura constante entre 18°C y 22°C.
   - Puesta a tierra dedicada conectada a la barra principal de tierra de telecomunicaciones (TGB).

---

### 11.3. Equipamiento del Gabinete de Comunicaciones (Rack 19")
Se ha dimensionado un **Gabinete Rack de piso de 19 pulgadas y 24 Unidades de Rack (24U)** con puerta frontal de vidrio templado ventilada.

**Distribución de Unidades en el Rack (Elevación frontal de arriba hacia abajo):**
- **U23 - U24:** Unidad de ventilación superior (4 ventiladores para extracción de calor).
- **U21 - U22:** Bandeja fija para Router de borde / Firewall corporativo y módem del ISP.
- **U19:** Servidor local de Base de Datos y Sistema de Historias Clínicas (Chasis 1U).
- **U18:** Servidor de almacenamiento NAS y NVR de cámaras de seguridad (Chasis 1U).
- **U16:** Organizador horizontal de cables de 1U.
- **U15:** **Patch Panel Cat 6 de 48 puertos (1U)** donde rematan todos los cables del policlínico.
- **U14:** Organizador horizontal de cables de 1U.
- **U13:** **Switch Administrable PoE+ de 48 puertos Gigabit Ethernet** (10/100/1000 Mbps).
- **U11 - U12:** Bandeja de reserva para futura ampliación (segundo switch).
- **U01 - U03:** **Sistema de Alimentación Ininterrumpida (UPS Online de 2000VA / 1800W, 3U)** con autonomía de 45 minutos para respaldo eléctrico ante cortes de luz.

---

### 11.4. Estándares de Terminación: T568A vs. T568B

Para la terminación de los conectores RJ-45 y jacks se adoptó de forma unánime el estándar **T568B** en ambos extremos de toda la instalación (cable directo / straight-through):

```
Pin 1: Blanco - Naranja
Pin 2: Naranja
Pin 3: Blanco - Verde
Pin 4: Azul
Pin 5: Blanco - Azul
Pin 6: Verde
Pin 7: Blanco - Marrón
Pin 8: Marrón
```

| Pin | Función (10/100/1000BASE-T) | Código de Color T568B | Código de Color T568A |
| :---: | :---: | :--- | :--- |
| **1** | Par 2 (Tx+ / DA+) | **Blanco con franja Naranja** | Blanco con franja Verde |
| **2** | Par 2 (Tx- / DA-) | **Naranja sólido** | Verde sólido |
| **3** | Par 3 (Rx+ / DB+) | **Blanco con franja Verde** | Blanco con franja Naranja |
| **4** | Par 1 (Bidireccional DC+) | **Azul sólido** | Azul sólido |
| **5** | Par 1 (Bidireccional DC-) | **Blanco con franja Azul** | Blanco con franja Azul |
| **6** | Par 3 (Rx- / DB-) | **Verde sólido** | Naranja sólido |
| **7** | Par 4 (Bidireccional DD+) | **Blanco con franja Marrón** | Blanco con franja Marrón |
| **8** | Par 4 (Bidireccional DD-) | **Marrón sólido** | Marrón sólido |

*Diferencia técnica:* T568A y T568B son idénticos eléctricamente; la única diferencia es la inversión de los pares Naranja (Par 2) y Verde (Par 3). Se eligió **T568B** por ser el estándar más consolidado en Perú e Hispanoamérica para infraestructura comercial.

---

### 11.5. Procedimiento de Armado del Cable Físico (Para demostración ante el docente)

Cada integrante del equipo debe conocer y dominar este procedimiento:
1. **Preparación:** Cortar el tramo de cable UTP a la medida deseada (1.5 a 2 metros).
2. **Deschaquetado:** Con la cuchilla pelacables, retirar con sumo cuidado aproximadamente 2.5 cm de la cubierta exterior de PVC, asegurándose de no mellar el aislamiento de cobre de los hilos internos.
3. **Corte del separador (Spline):** Cortar el plástico cruciforme central y el hilo de desgarre al ras de la cubierta.
4. **Destrenzado y alineación:** Destrenzar los pares e invertir el menor tramo posible (mantener el trenzado hasta 1.2 cm del conector para no degradar el NEXT).
5. **Ordenamiento:** Alinear los 8 hilos en fila plana según el esquema **T568B** (Blanco-Naranja, Naranja, Blanco-Verde, Azul, Blanco-Azul, Verde, Blanco-Marrón, Marrón).
6. **Corte parejo:** Cortar los hilos transversalmente a 90° dejando aproximadamente 1.3 cm de hilos expuestos.
7. **Inserción en el Plug RJ-45:** Introducir los hilos firmemente en el conector hasta que hagan tope en el extremo frontal y se verifique visualmente por la parte transparente que el hilo 1 (Blanco-Naranja) esté a la izquierda con la pestaña del conector hacia abajo. La chaqueta exterior del cable debe ingresar dentro del conector para que quede prensada mecánicamente.
8. **Crimpado:** Insertar el conector en la cavidad 8P de la crimpadora y apretar firmemente hasta completar el ciclo mecánico.
9. **Repetición y Prueba:** Repetir la misma secuencia T568B en el otro extremo para obtener un cable directo. Conectar ambos extremos en el **Tester de Red RJ-45** y comprobar el encendido secuencial y continuo de las luces 1 al 8.
