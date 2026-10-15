# Memoria Técnica - Unidad I: Redes de Comunicación I
## "Diseño de la infraestructura física y cableado estructurado de una red LAN para una Biblioteca"

> **Responsable:** Integrante 2  
> **Alcance de la sección:** Secciones 7 y 8 de la Memoria Técnica (Tipo y Topología de Red, Modelos OSI y TCP/IP, y Flujo de Encapsulación/Desencapsulación).

---

# 7. Tipo y Topología de Red

### 7.1. Clasificación por Alcance Geográfico: Red de Área Local (LAN)
La infraestructura diseñada para la Biblioteca corresponde a una **LAN (Local Area Network)** debido a las siguientes características:
- **Ámbito Geográfico Limitado:** La cobertura se circunscribe íntegramente a las instalaciones del edificio de la biblioteca (500 m² de planta única).
- **Propiedad y Control Administrativo Privado:** Toda la infraestructura pasiva (cables, racks, tomas) y activa (switches, APs) está bajo la gestión técnica exclusiva de la administración de la biblioteca o de la institución educativa.
- **Altas Tasas de Transferencia y Baja Tasa de Errores:** Se implementa tecnología Gigabit Ethernet (1000BASE-T) que garantiza velocidades nominales de 1000 Mbps (1 Gbps) en los enlaces cableados hacia las PCs de los estudiantes y bibliotecarios, con latencias típicamente inferiores a 1 ms en la red local.

---

### 7.2. Topología Física: Estrella Extendida / Jerárquica Centralizada
Para el despliegue del cableado estructurado se ha seleccionado unánimemente una **Topología Física en Estrella**, centralizada en el Cuarto de Telecomunicaciones (MDF / Rack Principal).

```
                      +-----------------------------+
                      |   Router / Gateway WAN      |
                      +--------------+--------------+
                                     | Uplink (1 Gbps)
                      +--------------v--------------+
                      |  Switch Principal Gigabit   |
                      |   48 Puertos PoE+ (MDF)     |
                      +--+-----+-----+-----+-----+--+
                         |     |     |     |     |
         +---------------+     |     |     |     +---------------+
         |                     |     |     |                     |
+--------v--------+ +----------v--+  |  +--v----------+ +--------v--------+
| 16 PCs Sala     | | 4 Puntos    |  |  | 6 Puestos   | | 4 Access Points |
| Cómputo Alumnos | | OPAC Catál. |  |  | Bibliotec.  | | Wi-Fi 6 (PoE)   |
+-----------------+ +-------------+  |  +-------------+ +--------+--------+
                                     |                           |
                       +-------------v-------------+   +---------v---------+
                       | Servidor Local / NAS      |   | Laptops y Celul.  |
                       | e Impresoras de Red       |   | Alumnos (Inalám.) |
                       +---------------------------+   +-------------------+
```

#### Justificación Técnica de la Topología Física en Estrella:
1. **Aislamiento de Fallas:** En una topología en estrella, la avería, corte o desconexión del cable de una PC de un estudiante en la sala de lectura no afecta en absoluto a las demás terminales ni a los puestos de los bibliotecarios.
2. **Facilidad de Diagnóstico y Mantenimiento:** Cualquier problema de capa física se diagnostica directamente en el puerto correspondiente del Patch Panel o Switch en el rack.
3. **Escalabilidad y Flexibilidad:** Es sencillo incorporar nuevas tomas de red o mover terminales sin interrumpir el funcionamiento continuo de la red de la biblioteca.
4. **Cumplimiento de la Norma ANSI/TIA-568:** El estándar prohíbe taxativamente topologías físicas de bus o anillo para cableado horizontal comercial, exigiendo que cada toma de telecomunicaciones esté conectada directamente a un distribuidor central mediante un enlace individual en estrella punto a punto.

---

### 7.3. Topología Lógica: Estrella / Bus Broadcast Ethernet (IEEE 802.3) e Inalámbrica (IEEE 802.11)
- **Dominio Cableado (IEEE 802.3):** Enlaces punto a punto Full-Duplex conmutados por el Switch. No existen colisiones en los cables de par trenzado Cat 6 gracias al microsegmentado del Switch (cada puerto es un dominio de colisión independiente).
- **Dominio Inalámbrico (IEEE 802.11ax / Wi-Fi 6):** En el espacio aéreo, el medio físico de transmisión es compartido por los dispositivos inalámbricos de los estudiantes mediante el protocolo de acceso al medio CSMA/CA (*Carrier Sense Multiple Access with Collision Avoidance*).

---

# 8. Modelos de Referencia: OSI y TCP/IP

### 8.1. Comparativa y Mapeo de Capas en el Escenario de la Biblioteca

| Capa OSI | Función Principal | Equivalente TCP/IP | Elementos en la Biblioteca | Protocolos / Tecnologías |
| :---: | :--- | :---: | :--- | :--- |
| **7. Aplicación** | Interfaz humana y servicios de red directos al usuario. | **Aplicación** | Interfaz web del catálogo de la biblioteca (OPAC), navegador web del alumno. | HTTP, HTTPS, DNS, DHCP. |
| **6. Presentación** | Formato, codificación y cifrado de los datos. | *(Englobada en Aplicación)* | Renderizado de páginas web, cifrado de credenciales de usuario. | TLS 1.3, JSON, HTML5, PDF. |
| **5. Sesión** | Control y sincronización del diálogo entre aplicaciones. | *(Englobada en Aplicación)* | Mantenimiento de la sesión de inicio de sesión del estudiante o bibliotecario. | RPC, sockets SSL/TLS. |
| **4. Transporte** | Entrega confiable extremo a extremo, control de flujo y multiplexación por puertos. | **Transporte** | Segmentación del tráfico de descarga de libros y consultas a base de datos. | TCP (puerto 443 HTTPS, 80 HTTP), UDP (puerto 53 DNS, 67/68 DHCP). |
| **3. Red** | Enrutamiento lógico y direccionamiento jerárquico. | **Internet** | Router de borde de la biblioteca, paquetes IP originados en PCs. | IPv4, ICMP, ARP. |
| **2. Enlace de Datos** | Direccionamiento físico (MAC), entramado, detección de errores (CRC) y control de acceso al medio. | **Acceso a la Red** | Tarjetas de Red (NIC) de las PCs, switches, puertos Ethernet del AP. | IEEE 802.3 (Ethernet), IEEE 802.11 (Wi-Fi), CSMA/CD / CSMA/CA. |
| **1. Física** | Transmisión de bits puros mediante señales eléctricas o radiofrecuencia sobre el medio. | *(Englobada en Acceso a la Red)* | Cables UTP Cat 6, conectores RJ-45, ondas de radio (2.4/5 GHz), jacks keystone, patch panels. | Señalización PAM-5 (1000BASE-T), modulación QAM (Wi-Fi). |

---

### 8.2. Ejemplo de Aplicación Práctica del Proceso de Encapsulación y Desencapsulación

**Escenario de estudio:** Un estudiante sentado en una de las PCs cableadas de la Sala de Cómputo realiza una búsqueda en el catálogo web local (OPAC) de la biblioteca para consultar la disponibilidad del libro *"Redes de Computadoras" de Tanenbaum*.

```
[ PC Alumno (Emisor) ]                                [ Servidor OPAC (Receptor) ]
+---------------------+                                +-------------------------+
| Capa Aplicación     |  PDU: Datos                    | Capa Aplicación         |
| (HTTP GET /opac)    |  [ Solicitud HTTP ]            | (Procesa HTTP GET)      |
+----------+----------+                                +------------^------------+
           | Encapsula                                              | Desencapsula
+----------v----------+  PDU: Segmento                 +------------+------------+
| Capa Transporte     |  [ Header TCP | Datos ]        | Capa Transporte         |
| (Agrega TCP Port)   |  (Puerto origen: 51234, Dest: 80)| (Verifica puerto 80)  |
+----------+----------+                                +------------^------------+
           | Encapsula                                              | Desencapsula
+----------v----------+  PDU: Paquete                  +------------+------------+
| Capa Red            |  [ Header IP | TCP | Datos ]   | Capa Red                |
| (Agrega IP Origen/D)|  (IP PC -> IP Servidor OPAC)   | (Verifica IP destino)   |
+----------+----------+                                +------------^------------+
           | Encapsula                                              | Desencapsula
+----------v----------+  PDU: Trama                    +------------+------------+
| Capa Enlace         |  [ MAC Dest | MAC Orig | IP... | FCS ] | Capa Enlace     |
| (Agrega MAC / FCS)  |  (Ethernet 802.3 con CRC)      | (Calcula y valida FCS)  |
+----------+----------+                                +------------^------------+
           | Codifica                                               | Decodifica
+----------v----------+  PDU: Bits (Señales Eléctricas)+------------+------------+
| Capa Física         |  0100101011000101010101010101  | Capa Física             |
| (Cable UTP Cat 6)   |  ===[ Ondas de Voltaje sobre 4 pares cobre ]===>          |
+---------------------+                                +-------------------------+
```

#### Paso a Paso del Flujo:
1. **Generación de Datos (Capa 7, 6 y 5):** El navegador web de la PC del alumno envía un requerimiento `GET /catalogo?libro=tanenbaum HTTP/1.1`.
2. **Segmentación (Capa 4 - Transporte):** La capa de transporte añade una cabecera TCP indicando un puerto de origen efímero (ej. 51234) y el puerto de destino del servicio web (puerto 80 o 443). Se genera el **Segmento**.
3. **Empaquetado (Capa 3 - Red):** Se agrega el encabezado IP con la dirección lógica del estudiante (IP origen) y la del servidor de la biblioteca (IP destino). Se genera el **Paquete**.
4. **Entramado (Capa 2 - Enlace de Datos):** La tarjeta de red (NIC) ensambla la **Trama Ethernet**, adicionando la dirección física MAC de origen de la PC del estudiante y la MAC de destino (del servidor o del gateway). Al final se inserta la secuencia de verificación de trama (**FCS / Frame Check Sequence**) con algoritmo CRC-32 para detectar posibles corrupciones de bits durante el trayecto.
5. **Transmisión de Bits (Capa 1 - Física):** La NIC convierte los ceros y unos de la trama en pulsos de voltaje eléctrico (modulación PAM-5 de 5 niveles de tensión) y los inyecta a través de los 4 pares trenzados del cable UTP Categoría 6, pasando por el jack keystone, cable horizontal, patch panel y el switch central, hasta arribar al servidor.
6. **Recepción y Desencapsulación en el Servidor:** El proceso inverso ocurre en el servidor de la biblioteca: valida el FCS de la capa 2, retira el encabezado de enlace, procesa la cabecera IP en capa 3, identifica el puerto TCP en capa 4 y finalmente entrega los datos limpios a la aplicación web del catálogo en capa 7 para retornar la respuesta al estudiante.
