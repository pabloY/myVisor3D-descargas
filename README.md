# myVisor3D

Visor ligero de modelos 3D para Windows, de **PabloYT**. Abre archivos **FBX**, **OBJ**,
**glTF/GLB** y **USD/USDZ** con sus texturas PBR, reconoce los nombres de exportación de
**Substance Painter** (incluidos los tiles **UDIM**) y permite ver el render final con los focos del
archivo, cada mapa por separado o el mapa UV. Guarda nuevas versiones del modelo en FBX, GLB, USD o
USDZ con las correcciones, sin cambiar su topología (salvo GLB, que solo admite triángulos).
Funciona sin conexión.

## Descargar

**[⬇ Descargar la última versión](https://github.com/pabloY/myVisor3D-descargas/releases/latest)**
y, en el apartado *Assets*, elige:

- **`myVisor3D-Setup-v<versión>.exe`**: instalador (recomendado).
- `myVisor3D-v<versión>-win-x64.zip`: versión portable; descomprímela y ejecuta `myVisor3D.exe`.

**Requisitos:** Windows 10 u 11 de 64 bits y una tarjeta gráfica con WebGL 2 (cualquiera de los
últimos años). No hace falta ser administrador ni tener conexión a internet. Usa Microsoft Edge
WebView2, que ya viene con Windows 11 y con Windows 10 actualizado; si faltara, el programa lo avisa.

## Instalar

1. Descarga el instalador y ábrelo. Se instala solo para tu usuario y puedes elegir:
   - **«Abrir con myVisor3D»** en el menú contextual del Explorador para los modelos 3D (`.fbx`,
     `.obj`, `.glb`, `.gltf`, `.usd`, `.usdz`…; no cambia tu programa predeterminado);
   - accesos directos en el menú Inicio y en el escritorio.
2. **Aviso de Windows.** El instalador no tiene firma digital, así que es normal que:
   - el navegador pregunte si quieres conservar el archivo: elige **Conservar**;
   - Windows muestre «Windows protegió su PC»: pulsa **Más información → Ejecutar de todas formas**.

Para desinstalarlo: *Configuración → Aplicaciones → myVisor3D → Desinstalar*.

Si quieres comprobar que la descarga está completa, compara su huella SHA-256 (está en las notas de
cada versión) con la que da PowerShell: `Get-FileHash .\myVisor3D-Setup-v<versión>.exe`.

## Uso rápido

1. Guarda el modelo con sus texturas en una subcarpeta `texturas` (también valen `textures`, `tex`,
   `maps` o `sourceimages`):

   ```
   MiModelo/
   ├── personaje.fbx          (o .obj + .mtl, .glb, .gltf, .usd, .usdz)
   └── texturas/
       ├── Cuerpo_BaseColor.1001.png
       ├── Cuerpo_Roughness.1001.png
       └── ...
   ```

2. Abre myVisor3D y pulsa **Abrir**, arrastra el archivo a la ventana o usa *Abrir con myVisor3D*
   desde el Explorador.

Algunas cosas que puedes hacer:

- Ver el **render final** con los focos del archivo, sombras y entornos HDRI, o cada mapa por
  separado (Color base, Roughness, Normal, AO…) y el **mapa UV** con sus tiles UDIM.
- Añadir focos y cambiar el tipo, la posición y la orientación de cada uno (`W` mover, `E` girar).
- Ajustar cada mapa por material y tile UDIM, asignar otras imágenes (arrastrándolas encima o con
  el botón derecho) y quitar mapas con el botón derecho.
- Reparar la geometría (soldar vértices, normales) y desplazar la superficie con el mapa Height.
- **Guardar** (`Ctrl+S`) una nueva versión en FBX, GLB, USD o USDZ, en una subcarpeta junto al
  modelo, con las correcciones de geometría (los mismos polígonos: los quads y n-gonos no se
  triangulan, salvo en GLB, que solo admite triángulos y lo avisa), los focos y las texturas
  cambiadas, que se aplican solas al abrirla.

Los atajos de teclado están al final del panel lateral, y la sección **Versión** indica la versión
instalada.

## Historial de versiones

### 1.10.1

- El FBX guardado solo lleva datos estándar de FBX, sin propiedades propias de myVisor3D (como ya
  hacían GLB, USD y USDZ).
  - El tamaño de los focos superficiales no se guarda en FBX (no tiene una propiedad estándar): al
    abrirlo vuelven al tamaño por defecto. USD sí lo conserva.
  - Un FBX guardado desde OBJ, glTF o USD guarda el metallic del material (y una roughness por
    debajo de 0,2) como textura uniforme, para que se vea igual al abrirlo.

### 1.10.0

- Abre modelos **glTF/GLB** (también comprimidos con Draco o meshopt) y **USD, USDA, USDC y
  USDZ**, con sus texturas (también las que van dentro del archivo) y sus focos.
- **Guardar** en **FBX, GLB, USD o USDZ**, eligiendo el formato en la lista junto al botón (de entrada,
  el del archivo abierto). GLB y USDZ son un solo archivo con las texturas dentro.
  - FBX, USD y USDZ guardan los mismos polígonos (quads y n-gonos incluidos).
  - **GLB solo admite triángulos**: si el modelo tiene quads o n-gonos, avisa antes de guardar y los
    guarda triangulados.
  - GLB, USD y USDZ solo llevan datos estándar de su formato.
- **Añadir foco** y **Quitar foco** en Iluminación: focos nuevos que se ajustan como los demás y se
  guardan con la versión.
- **Asignar mapa…** con el botón derecho sobre cada mapa de la lista y sobre cada tile UDIM de la
  vista UV: elige una imagen y se asigna igual que si se arrastrara encima.
- «Abrir con myVisor3D» también para los `.glb`, `.gltf`, `.usd`, `.usda`, `.usdc` y `.usdz`.

### 1.9.0

- Botón **Guardar** junto a Abrir (`Ctrl+S`): crea una nueva versión del modelo en FBX, también si
  el original es OBJ, en una subcarpeta junto a él (`modelo_v01\modelo_v01.fbx`, `modelo_v02`…).
  El original no se modifica.
  - Correcciones de geometría **sin cambiar la topología**: los mismos polígonos, en el mismo orden
    y con los mismos vértices (quads y n-gonos incluidos); solo cambian las posiciones de los
    vértices corregidos y las normales. El archivo guardado se vuelve a leer para comprobarlo.
  - Cambios de los focos: tipo, posición, orientación, color, intensidad, tamaño y encendido.
  - Copia de las texturas y, en `texturas\cambios`, las texturas cambiadas (mapas arrastrados o
    quitados, valores de los sliders) con su nombre, para que se apliquen solas al abrir la versión.
  - El desplazamiento y el teselado no se guardan.
- Cada archivo se abre con todos los ajustes y sliders en su posición por defecto; el programa ya no
  recuerda el estado de cada modelo.
- Soldar vértices ya no puede separar vértices que estaban unidos (abría grietas con distancias
  grandes).
- Los polígonos degenerados (vértices repetidos o alineados) de un FBX conservan todas sus esquinas.
- Los spots y focos direccionales del FBX ya no aparecen desplazados una unidad.
- Sustituye al antiguo «Guardar…» en OBJ + MTL de Reparar geometría.

### 1.8.0

- Sección **Versión** en el panel, con la versión, el autor y las licencias.
- Licencia («Todos los derechos reservados») y avisos de terceros junto al programa.
- Primera versión publicada en este repositorio.

### 1.7.0

- Quitar mapas con el botón derecho: en todo el modelo (lista de mapas) o en un tile UDIM concreto
  (vista UV). Lo quitado usa el valor uniforme de su slider; **Deshacer** vuelve a los del archivo.

### 1.6.1

- Opción **Invertir** del desplazamiento (escala de grises del mapa Height invertida).

### 1.6.0

- Sliders de los mapas por material y tile UDIM, con la opción **Todos**.
- Sin mapa, el slider da un valor gris uniforme (como un mapa de ese valor).
- Slider **Metallic**.
- Un tile UDIM que falta usa los valores del material.

### 1.5.0

- Cada foco puede cambiar de tipo (direccional, puntual, spot o superficial) y moverse y girarse con
  gizmos (`W` mover, `E` girar, `Q` quitar el gizmo, `Esc` soltar).
- Slider **Intensidad sombras**.
- El slider Roughness multiplica el mapa (0 a ×10).

### 1.4.3

- Corregida la sombra en forma de anillo de algunos objetos.

### 1.4.2

- Casilla para encender o apagar cada foco de la escena.

### 1.4.1

- Los sliders de los mapas pasan a la sección Texturas.

### 1.4.0

- Sliders Height/Bump, Roughness, Specular, Emisivo y Opacidad.
- El mapa Specular se usa en el render final.
- Las texturas empaquetadas soltadas sobre Render final (ORM, MetallicRoughness, MaskMap…) se
  reparten solas en AO, Roughness y Metallic.

### 1.3.3

- Slider **AO** para suavizar o intensificar la oclusión ambiental.

### 1.3.2

- Temperatura de color e intensidad de cada foco de la escena (también la luz ambiente).
- Slider **Normal** para el relieve del mapa de normales.
- Al abrir un archivo, la cámara empieza encuadrada con un objetivo de 50°.

### 1.3.1

- Una imagen soltada en un tile de un material sin UDIM solo afecta a ese tile.

### 1.3.0

- Vistas Perspectiva, Planta, Alzado y Perfil con indicador de ejes.
- Punto de pivote con gizmo y opción de orbitar alrededor de él.
- Desplazamiento con el mapa Height y teselado.
- Guardar una nueva versión en OBJ + MTL con las correcciones.
- Soltar una imagen sobre un tile de la vista UV la aplica solo a ese tile.
- Barra superior con Información, Rejilla, Doble cara y eje vertical.

### 1.2.0

- Sección **Reparar geometría**: soldar vértices, suavizado por ángulo y normales por polígono o
  por grupo de suavizado.
- Arrastrar una imagen sobre un mapa para usarla en su lugar.
- Casillas independientes para los focos de la escena (`L`) y el HDRI (`H`).
- La rueda del ratón cambia el ángulo de visión del objetivo.
- HDRI incluidos en el instalador y en el portable.

### 1.1.0

- Iluminación con HDRI desde la carpeta `HDRI` del programa.
- Movimiento por la escena con `W` `A` `S` `D` `Q` `E`.
- Las listas desplegables se recorren con la rueda o con las flechas.

### 1.0.1

- Texturas de las mallas sin material (set `DefaultMaterial` de Substance Painter).
- Mejor elección automática del set de texturas.
- El visor no accede a la red.

### 1.0.0

- Primera versión: render final PBR con los focos del archivo, mapas individuales, texturas de
  Substance Painter con tiles UDIM, vista del mapa UV e instalador con «Abrir con myVisor3D».

## Licencia

Copyright (c) 2026 PabloYT. **Todos los derechos reservados.** Puedes instalar y usar el programa;
no está permitido copiarlo, redistribuirlo, modificarlo ni venderlo sin permiso por escrito del
autor. Consulta [LICENSE](LICENSE).

myVisor3D usa componentes de terceros con sus propias licencias: three.js (MIT), los
decodificadores Draco (Apache 2.0) y meshoptimizer (MIT), el SDK de WebView2 de Microsoft y entornos
HDRI de Poly Haven (CC0). Detalles en
[THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).

Este repositorio solo contiene las descargas; el código fuente no es público.
