# 📁 Carpeta de Recursos y Evidencias (`assets/`)

Este directorio centraliza todos los recursos gráficos, multimedia y evidencias técnicas del proyecto de infraestructura de red para la **Biblioteca**:

---

## 📂 Contenido y Organización Sugerida

1. **`assets/diagramas/`**
   - Diagramas de arquitectura y topología física/lógica.
   - Formatos recomendados: `.drawio`, `.drawio.svg`, `.png`, capturas de **Cisco Packet Tracer** (`.pkt`).

2. **`assets/plano/`**
   - Planos arquitectónicos de la biblioteca (distribución de ambientes: sala de cómputo para estudiantes, cubículos de estudio, recepción y préstamo bibliotecario, sala de lectura, cuarto de telecomunicaciones MDF/Rack).
   - Rutas de canaletas y canalizaciones, ubicación de tomas de datos (jacks RJ-45) y Access Points (AP) en techo.

3. **`assets/fotos_cable_utp/`**
   - Evidencias fotográficas del **cable UTP funcional** armado por el grupo bajo estándar **ANSI/TIA-568B** (requerimiento obligatorio para la exposición según la guía del docente).
   - Fotografías del pelado del cable, destrenzado, orden de colores (Blanco/Naranja, Naranja, Blanco/Verde, Azul, Blanco/Azul, Verde, Blanco/Marrón, Marrón), crimpado con la tenaza crimpadora y prueba con tester de red mostrando los 8 LEDs en secuencia correcta.

4. **`assets/fichas_tecnicas/`**
   - Hojas de datos (datasheets) de los equipos principales: Switch PoE Gigabit 24/48 puertos, Access Points Wi-Fi 6, Patch Panel Cat 6, Cable UTP Cat 6 100% cobre, Gabinete/Rack de pared o piso.

---

## 💡 Buenas Prácticas para Docs-as-Code
- Utilizar nombres de archivo en minúsculas y separados por guiones bajos (ejemplo: `plano_distribucion_biblioteca.png`, `prueba_tester_utp_t568b.jpg`).
- Mantener las imágenes optimizadas (máximo 1-2 MB por imagen) para mantener la agilidad del repositorio Git.
- Para vincular una imagen en cualquier archivo de `docs/`, usar la ruta relativa:  
  `![Descripción](../assets/plano/plano_distribucion_biblioteca.png)`
