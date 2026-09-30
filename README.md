# Plantilla de tesis en LaTeX

Base modular para escribir una tesis de seis capítulos. La presentación vive en
`estilos/tesis.sty`, los datos variables en `configuracion.tex` y el contenido en
un archivo independiente por capítulo.

## Estructura

```text
.
├── main.tex
├── configuracion.tex
├── estilos/tesis.sty
├── preliminares/
│   ├── resumen.tex
│   └── agradecimientos.tex
├── capitulos/
│   ├── 01-introduccion/contenido.tex
│   ├── 02-marco-teorico/contenido.tex
│   ├── 03-metodologia/contenido.tex
│   ├── 04-resultados/contenido.tex
│   ├── 05-discusion/contenido.tex
│   └── 06-conclusiones/contenido.tex
└── referencias/referencias.bib
```

## Compilación

La plantilla usa `biblatex` y Biber. La forma recomendada de compilar es:

```bash
latexmk -pdf main.tex
```

También se puede ejecutar manualmente:

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

El artefacto resultante es `main.pdf`. Para borrar archivos auxiliares, use
`make clean`.

## Personalización

Los cambios habituales no requieren editar el documento principal:

- **Datos de portada:** modifique los comandos de `configuracion.tex`.
- **Márgenes:** ajuste `\ConfiguracionMargenes{superior}{inferior}{interior}{exterior}`.
- **Colores:** use `\colorlet{ColorPrincipal}{...}` y
  `\colorlet{ColorSecundario}{...}` después de cargar el estilo.
- **Encabezados y pies:** cambie `\EncabezadoTesis` y `\PieTesis`.
- **Viñetas:** el primer nivel se configura con `\EstiloVinetaPrimerNivel`.
- **Títulos y bloques:** son parámetros centralizados en `estilos/tesis.sty`.

El estilo proporciona los entornos `bloque`, `definicion`, `advertencia` y
`citaacademica`; en `capitulos/01-introduccion/contenido.tex` hay ejemplos
listos para adaptar.
