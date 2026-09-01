# Swiper 14.2.0 — copia auto-hospedada

Copia **vendorizada** de [Swiper](https://swiperjs.com) para servirla desde GitHub Pages y no
depender de un CDN externo en prototipos y entregables.

> Esto **no es un desarrollo propio ni un fork**. Es una redistribución sin modificar de la
> librería de Vladimir Kharlampidi, permitida por su licencia MIT. Todo el crédito es suyo.
> Si buscas el proyecto original: **https://github.com/nolimits4web/swiper**

## Demo

**https://renatopuente-ux.github.io/swiper-selfhosted/** — carrusel funcionando con los archivos
de este repo. Sirve de comprobación de que lo hospedado carga bien.

## Procedencia y verificación

| | |
|---|---|
| Versión | `14.2.0` |
| Publicada | 26 de agosto de 2026 |
| Origen | `https://registry.npmjs.org/swiper/-/swiper-14.2.0.tgz` |
| Integridad del tarball | `sha512-GsL4M9Fq7Sg22OyL3SjdNj/0bxTfIxPJJHHW394Li0u5vYtExi0a09iBUc8CuLafJi5pAlH2AHUe1PocxHl45g==` |
| Licencia | MIT — ver [`LICENSE`](LICENSE) |

Los archivos de `dist/` se extrajeron de ese tarball **sin modificar ni un byte**. El hash `sha512`
del paquete descargado se verificó contra el que publica npm antes de extraerlo.

## Cómo usarlo

### Bundle completo (todos los módulos)

```html
<link rel="stylesheet" href="https://renatopuente-ux.github.io/swiper-selfhosted/dist/swiper-bundle.min.css">
<script src="https://renatopuente-ux.github.io/swiper-selfhosted/dist/swiper-bundle.min.js"></script>

<div class="swiper">
  <div class="swiper-wrapper">
    <div class="swiper-slide">1</div>
    <div class="swiper-slide">2</div>
  </div>
  <div class="swiper-pagination"></div>
</div>

<script>
  new Swiper('.swiper', {
    loop: true,
    pagination: { el: '.swiper-pagination', clickable: true },
  });
</script>
```

### Solo el core (más liviano, sin módulos)

`swiper.min.js` + `swiper.min.css` pesan 65 KB y 4,3 KB. No traen navegación, paginación,
autoplay ni efectos: si los necesitas, usa el bundle.

### Web component

`swiper-element-bundle.min.js` registra `<swiper-container>` y `<swiper-slide>`, sin necesidad
de instanciar nada por JavaScript.

## Qué contiene `dist/`

| Archivo | Peso | Para qué |
|---|---:|---|
| `swiper-bundle.min.js` | 149 KB | **El habitual.** Core + todos los módulos, minificado |
| `swiper-bundle.min.css` | 14 KB | Estilos de todos los módulos, minificado |
| `swiper-bundle.js` | 419 KB | El mismo bundle sin minificar, para depurar |
| `swiper-bundle.css` | 20 KB | Los mismos estilos sin minificar |
| `swiper.min.js` | 65 KB | Solo el core, sin módulos |
| `swiper.min.css` | 4,3 KB | Estilos solo del core |
| `swiper-element-bundle.min.js` | 180 KB | Versión web component |
| `*.min.js.map` | — | Source maps. Van porque los `.min.js` los referencian: sin ellos, devtools tira 404 |

## Lo que NO está aquí

El paquete de npm trae 409 archivos. Aquí solo van los que sirven para hospedar y usar en el
navegador. **No** están el código fuente sin minificar, los builds de React y Vue, los tipos de
TypeScript, ni los módulos sueltos.

Si necesitas alguno de esos, o vas a **modificar** la librería, este repo no es el punto de
partida correcto: clona el original o instala el paquete con `npm i swiper@14.2.0`.

## Actualizar a una versión nueva

1. Descargar el tarball de npm de la versión que toque.
2. Verificar su `sha512` contra el que publica el registro **antes** de extraerlo.
3. Reemplazar los archivos de `dist/`.
4. Actualizar la tabla de procedencia de este README con la versión, la fecha y el hash nuevos.

El paso 2 no es ceremonia: es lo que separa una copia verificable de una copia de origen incierto.
