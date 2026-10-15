# 📚 Proyecto de Redes I: Infraestructura LAN y Cableado Estructurado para Biblioteca

> **Curso:** Redes de Comunicación I – Unidad I  
> **Título Oficial:** *"Diseño de la infraestructura física y cableado estructurado de una red LAN para una organización"*  
> **Caso de Estudio:** **Biblioteca Central "León Pinelo"**  
> **Modalidad:** Grupal (5 integrantes)  
> **Filosofía del Repositorio:** **Docs-as-Code** (Toda la documentación técnica se gestiona en Markdown bajo control de versiones Git).

---

## 📌 1. Resumen Ejecutivo del Proyecto
La Biblioteca Central presentaba una severa crisis de conectividad originada por el **monopolio de un único Access Point (AP) doméstico**, el cual colapsaba ante la concurrencia simultánea de estudiantes e investigadores, dejando además "zonas muertas" por la absorción de radiofrecuencia que provocan las estanterías de libros. Asimismo, los alumnos carecían de tomas fijas cableadas de alta velocidad.

El equipo de ingeniería diseñó una solución integral normalizada bajo estándares **ANSI/TIA-568**, **TIA-569** e **ISO/IEC 11801**:
1. **Red Inalámbrica Distribuida:** Reemplazo del único AP por **4 Access Points empresariales Wi-Fi 6** alimentados vía **PoE+**, distribuidos estratégicamente en cielo raso (Lectura silenciosa, Sala de cómputo, Cubículos y Recepción).
2. **Puestos Cableados de Alto Rendimiento:** Implementación de **16 PCs conectadas por Ethernet Gigabit Cat 6** en la sala de cómputo para estudiantes, 4 módulos de búsqueda de catálogo (OPAC) y puestos fijos de atención bibliotecaria y dirección (total de **51 puntos de red** en Patch Panels).
3. **Centro de Gestión Centralizado:** Cuarto técnico (MDF) con Rack cerrado de 24U, Switch PoE+ Gigabit de 48 puertos, Patch Panels Cat 6 y respaldo eléctrico por UPS.

---

## 👥 2. Distribución Oficial de Roles (5 Integrantes)

Cada integrante tiene la responsabilidad directa de un archivo en la carpeta [`docs/`](file:///c:/Users/USUARIO/Desktop/PROYECTOS/proyecto-redes/docs) de acuerdo con los lineamientos del docente:

| Integrante | Rol Asignado | Archivo Asignado | Secciones del Informe a Cargo |
| :---: | :--- | :--- | :--- |
| **Integrante 1** | **Analista de Requerimientos y Organización** | [`01_introduccion_problematica.md`](file:///c:/Users/USUARIO/Desktop/PROYECTOS/proyecto-redes/docs/01_introduccion_problematica.md) | **Secciones 1 a 6:** Portada, Introducción, Descripción de la organización (Biblioteca), Problemática (el único AP colapsado), Objetivos y Requerimientos de red (30-60 nodos). |
| **Integrante 2** | **Arquitecto de Red y Modelos de Referencia** | [`02_topologia_modelos.md`](file:///c:/Users/USUARIO/Desktop/PROYECTOS/proyecto-redes/docs/02_topologia_modelos.md) | **Secciones 7 y 8:** Tipo de red (LAN), Topología física en estrella y lógica Ethernet/Wi-Fi, Modelos OSI y TCP/IP, y Flujo de Encapsulación/Desencapsulación detallado. |
| **Integrante 3** | **Especialista en Capa Física y Medios** | [`03_capa_fisica_medios.md`](file:///c:/Users/USUARIO/Desktop/PROYECTOS/proyecto-redes/docs/03_capa_fisica_medios.md) | **Secciones 9 y 10:** Señales eléctricas/RF, ancho de banda, tasa de bits, atenuación por estanterías de libros, ruido EMI, y Matriz de Selección justificada de UTP Cat 6 frente a fibra y coaxial. |
| **Integrante 4** | **Ingeniero de Cableado Estructurado** | [`04_cableado_estructurado.md`](file:///c:/Users/USUARIO/Desktop/PROYECTOS/proyecto-redes/docs/04_cableado_estructurado.md) | **Sección 11:** Normas TIA-568/569, subsistemas de cableado, Rack de 19", Patch Panels, estándar T568B y **Guía de armado y demostración del cable UTP físico**. |
| **Integrante 5** | **Diseñador de Planos, Materiales y Pruebas** | [`05_plano_materiales_pruebas.md`](file:///c:/Users/USUARIO/Desktop/PROYECTOS/proyecto-redes/docs/05_plano_materiales_pruebas.md) | **Secciones 12 a 17:** Plano físico y distribución de ambientes, Lista de Materiales (BOM), Plan de pruebas con tester, Conclusiones, Referencias APA y Anexos. |

> ⚠️ *Nota clave del docente:* **Todos los integrantes deben conocer y comprender la totalidad del proyecto.** En la ronda de preguntas se evaluará de forma individual y aleatoria.

---

## 📂 3. Estructura del Repositorio

```text
proyecto-redes/
├── assets/
│   ├── README.md                      <- Guía para guardar imágenes, planos y fotos
│   ├── diagramas/                     <- Diagramas .drawio.svg, packet tracer, esquemas
│   ├── fotos_cable_utp/               <- Fotos del cable armado y del tester con los 8 LEDs
│   └── plano/                         <- Imagen del plano arquitectónico de la biblioteca
├── docs/
│   ├── 01_introduccion_problematica.md <- Integrante 1 (Secciones 1 a 6)
│   ├── 02_topologia_modelos.md         <- Integrante 2 (Secciones 7 y 8)
│   ├── 03_capa_fisica_medios.md        <- Integrante 3 (Secciones 9 y 10)
│   ├── 04_cableado_estructurado.md     <- Integrante 4 (Sección 11)
│   ├── 05_plano_materiales_pruebas.md  <- Integrante 5 (Secciones 12 a 17)
│   └── diapositivas_exposicion.md      <- Guion para las 10 a 12 diapositivas de la expo
└── README.md                          <- Documento principal y guía del equipo
```

---

## ✅ 4. Checklist de Entregables Oficiales (Unidad I)

- [x] **Estructura base del repositorio inicializada bajo Docs-as-Code.**
- [x] **Definición del caso de estudio (Biblioteca: 51 puntos de red, 4 APs, 16 PCs de estudiantes).**
- [ ] **Completar datos personales en la Portada** (`docs/01_introduccion_problematica.md`).
- [ ] **Diseñar / Dibujar el Plano gráfico** (en Draw.io / Sweet Home 3D o AutoCAD) y guardarlo en `assets/plano/plano_biblioteca.png`.
- [ ] **Armar el Cable UTP funcional (Físico):**
  - Armar un cable de 1.5 a 2 metros con conectores RJ-45 bajo norma **T568B**.
  - Probar con tester y tomar fotografías para `assets/fotos_cable_utp/`.
  - Llevar el cable y tester el día de la exposición para la prueba en vivo.
- [ ] **Preparar las 10 a 12 diapositivas** basándose en [`docs/diapositivas_exposicion.md`](file:///c:/Users/USUARIO/Desktop/PROYECTOS/proyecto-redes/docs/diapositivas_exposicion.md).
- [ ] **Revisión cruzada y ensayo grupal de 20 minutos** (4 minutos por integrante).

---

## 🏆 5. Criterios de Evaluación y Rúbrica (Sobre 20 Puntos)

| Criterio Evaluado | Puntaje | Enfoque para asegurar la máxima nota |
| :--- | :---: | :--- |
| **1. Análisis del problema y requerimientos** | **2 pts** | Explicar con claridad por qué 1 solo AP colapsaba y justificar la necesidad de los puestos cableados de estudiantes. |
| **2. Aplicación de fundamentos, topologías y OSI/TCP-IP** | **2 pts** | Explicar el flujo de encapsulación de datos desde la PC del alumno hasta el servidor OPAC sin dudar. |
| **3. Selección y justificación de medios físicos** | **2 pts** | Justificar sólidamente por qué UTP Cat 6 (ancho de banda 250 MHz, PoE) frente a fibra óptica y coaxial. |
| **4. Diseño de cableado estructurado** | **4 pts** | Explicar el cuarto técnico, patch panel, distancias (< 90 m) y la norma T568B. *(Es el ítem con más puntaje).* |
| **5. Plano y diseño físico de la red** | **3 pts** | Mostrar el plano claro con ubicación de tomas, APs en techo y trayecto de canaletas. |
| **6. Plan de pruebas y cable UTP funcional** | **2 pts** | Mostrar el cable armado por ustedes mismos y explicar las pruebas del tester (wiremap). |
| **7. Calidad de la memoria técnica** | **2 pts** | Redacción técnica profesional, orden, coherencia y referencias en formato APA. |
| **8. Exposición y dominio individual** | **3 pts** | Responder con seguridad a las preguntas individuales aleatorias del docente. |
| **TOTAL** | **20 pts** | |

---

## 🚀 6. Guía Paso a Paso: Flujo de Trabajo con Git y GitHub

Al trabajar con la metodología **Docs-as-Code**, cada integrante trabaja en su propio archivo sin alterar los archivos de los demás:

### Paso 1: Clonar o actualizar el repositorio en su computadora local
Abrir una terminal (PowerShell o Git Bash) y ejecutar:
```bash
git pull origin main
```

### Paso 2: Editar únicamente el archivo asignado
- Integrante 1 edita: `docs/01_introduccion_problematica.md`
- Integrante 2 edita: `docs/02_topologia_modelos.md`
- Integrante 3 edita: `docs/03_capa_fisica_medios.md`
- Integrante 4 edita: `docs/04_cableado_estructurado.md`
- Integrante 5 edita: `docs/05_plano_materiales_pruebas.md`

### Paso 3: Guardar y verificar el estado
```bash
git status
```
*(Verificarás que solo tu archivo modificado aparece en color rojo).*

### Paso 4: Preparar los cambios (Stage)
```bash
git add docs/tu_archivo.md
# Si agregaste imágenes en assets:
git add assets/
```

### Paso 5: Confirmar los cambios con un mensaje claro (Commit)
Usar el prefijo `docs:` para mantener el historial profesional:
```bash
# Ejemplo Integrante 1:
git commit -m "docs: completar seccion de requerimientos y datos de la biblioteca"

# Ejemplo Integrante 4:
git commit -m "docs: detallar pasos de crimpado T568B para el cable UTP"
```

### Paso 6: Subir los cambios a GitHub (Push)
Antes de subir, es buena práctica hacer un pull para traer cambios de los compañeros:
```bash
git pull --rebase origin main
git push origin main
```

---

## 💡 7. Recomendaciones Clave para la Exposición
1. **No lean las diapositivas:** El docente evaluará que **defiendan sus decisiones** (*"Elegimos UTP Cat 6 porque..."*, *"Ubicamos 4 APs porque los libros atenuaban la señal..."*).
2. **Control estricto del tiempo:** Cada integrante tiene un promedio de **3.5 a 4 minutos**. Practiquen con cronómetro para no exceder los 20 minutos grupales.
3. **Preguntas trampa habituales del profesor:**
   - *¿Por qué no usaron fibra óptica hasta las PCs de los estudiantes?*  
     *(Respuesta: Porque para distancias menores a 40 m el UTP Cat 6 brinda 1 Gbps a una fracción del costo y no requiere tarjetas ópticas ni fusiones costosas).*
   - *¿Qué diferencia hay entre T568A y T568B?*  
     *(Respuesta: La inversión de las posiciones de los pares naranja y verde. El pin 1 y 2 en T568A son blanco/verde y verde, mientras que en T568B son blanco/naranja y naranja).*
   - *¿Por qué se usan 4 APs y no 1 con amplificador?*  
     *(Respuesta: Porque los amplificadores o repetidores reducen el ancho de banda a la mitad y aumentan la latencia. Los 4 APs cableados con PoE operan en canales independientes sin interferencia mutua y reparten la carga).*
