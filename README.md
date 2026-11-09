# myVisor3D

Visor ligero de modelos 3D para Windows, de **PabloYT**. Abre archivos **FBX** y **OBJ** con sus
texturas PBR, reconoce los nombres de exportación de **Substance Painter** (incluidos los tiles
**UDIM**) y permite ver el render final con los focos del archivo, cada mapa por separado o el
mapa UV. Funciona sin conexión.

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
   - **«Abrir con myVisor3D»** en el menú contextual del Explorador para los `.fbx` y `.obj`
     (no cambia tu programa predeterminado);
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
   ├── personaje.fbx          (o .obj + .mtl)
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
- Cambiar el tipo, la posición y la orientación de cada foco (`W` mover, `E` girar).
- Ajustar cada mapa por material y tile UDIM, arrastrar imágenes encima para probar otras texturas
  y quitar mapas con el botón derecho.
- Reparar normales, desplazar la superficie con el mapa Height y guardar una copia en OBJ + MTL.

Los atajos de teclado están al final del panel lateral, y la sección **Versión** indica la versión
instalada.

## Licencia

Copyright (c) 2026 PabloYT. **Todos los derechos reservados.** Puedes instalar y usar el programa;
no está permitido copiarlo, redistribuirlo, modificarlo ni venderlo sin permiso por escrito del
autor. Consulta [LICENSE](LICENSE).

myVisor3D usa componentes de terceros con sus propias licencias: three.js (MIT), el SDK de
WebView2 de Microsoft y entornos HDRI de Poly Haven (CC0). Detalles en
[THIRD-PARTY-NOTICES.txt](THIRD-PARTY-NOTICES.txt).

Este repositorio solo contiene las descargas; el código fuente no es público.
