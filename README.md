# Sitio de clases Pascual Bravo 2026-02

Material docente de la **Institución Universitaria Pascual Bravo**, Facultad de Ingeniería,
semestre 2026-02. Docente: Oscar Leonel Sánchez Conde.

Sitio publicado: <https://oscarleosanchez.github.io/sitio-pascual-b-2026-02/>

## Enlaces por asignatura

Cada estudiante recibe el enlace directo de su asignatura, no el de la portada. El sitio no tiene
barra de navegación superior a propósito: cada asignatura navega por su propia barra lateral y
ninguna página enlaza a la otra.

### Herramientas de Programación I (ET0047)

Tecnología en Desarrollo de Software, nivel 5. Modalidad virtual, 4 créditos.
Programación en C# con .NET 10: entornos de desarrollo, sintaxis y estructuras de control, arreglos
y funciones, programación orientada a objetos e interfaces gráficas con Windows Forms.

- Presentación y calendario:
  <https://oscarleosanchez.github.io/sitio-pascual-b-2026-02/herramientas-programacion-1/>
- Semana 1. El IDE y tu primer programa en C#:
  <https://oscarleosanchez.github.io/sitio-pascual-b-2026-02/herramientas-programacion-1/semana-01/>

### Estadística para Analítica

Especialización en Big Data. Modalidad presencial, 192 horas.
Estadística aplicada con Python: análisis exploratorio de datos, modelos de probabilidad,
estimación, pruebas de hipótesis, ANOVA y regresión lineal, con enfoque experimental.

- Presentación y calendario:
  <https://oscarleosanchez.github.io/sitio-pascual-b-2026-02/estadistica-para-analitica/>
- Semana 1. El entorno de trabajo y tus primeras mediciones:
  <https://oscarleosanchez.github.io/sitio-pascual-b-2026-02/estadistica-para-analitica/semana-01/>

Publico las demás semanas a medida que avanza el semestre. El calendario completo de cada
asignatura vive en su página de presentación.

## Estructura de las dos asignaturas

Ambas tienen **16 semanas**, tres unidades y tres cortes evaluativos en las mismas fechas.

| Corte | Semana | Peso |
|---|:---:|:---:|
| Cierre de la Unidad 1 | 05 | 30% |
| Cierre de la Unidad 2 | 10 | 30% |
| Evaluación final de la Unidad 3 | 16 | 40% |

| | Herramientas de Programación I | Estadística para Analítica |
|---|---|---|
| Nivel | Pregrado | Posgrado |
| Modalidad | Virtual | Presencial |
| Dedicación semanal | 4 h de acompañamiento y 8 h independientes | 3 h de acompañamiento y 9 h independientes |
| Stack | C# con .NET 10 y Windows Forms | Python 3.13 con pandas, scipy y statsmodels |

## Cómo se construye

El sitio se genera con [Quarto](https://quarto.org). Los fuentes son los archivos `.qmd` y la
carpeta `docs/` guarda el HTML renderizado, que es lo que sirve GitHub Pages.

```powershell
quarto render          # regenera docs/
quarto preview         # servidor local con recarga automática
```

Cierra el preview antes de correr `quarto render`. Si lo dejas abierto, el render falla al
intentar recrear `docs/` porque el proceso mantiene la carpeta ocupada.

## Estructura del repositorio

```
_quarto.yml                          Configuración: barras laterales, tema, formato
estilos/estilo.scss                  Tema visual compartido por todas las guías
index.qmd                            Portada
herramientas-programacion-1/
    index.qmd                        Presentación y calendario de las 16 semanas
    semana-NN/index.qmd              La guía que lee el estudiante
    semana-NN/imagenes/              Capturas reales usadas por esa guía
    semana-NN/recursos/              Datasets y archivos de apoyo
estadistica-para-analitica/          Misma forma
docs/                                Salida renderizada. GitHub Pages publica desde aquí
```

Cada semana vive en su propia carpeta, con las imágenes y los recursos al lado de la guía que los
usa.

Este repositorio contiene **solo material público**. Los planes de sesión, los enunciados de
evaluación y las rúbricas viven fuera de él: GitHub Pages es público y cualquiera con el enlace
entra.

## Publicar una semana nueva

```powershell
quarto render
git add -A
git commit -m "Semana NN de <asignatura>"
git push
```

GitHub Pages actualiza el sitio en menos de un minuto. Los enlaces no cambian en todo el semestre.

Una semana nueva se registra en **dos** lugares: la barra lateral del `_quarto.yml` y la tabla del
calendario en la página de presentación de su asignatura.

## Convenciones de escritura

- Nombres de archivo sin tildes, sin eñes y sin espacios. El contenido sí lleva tildes.
- Nada de raya larga, punto medio, comillas tipográficas ni flechas. Solo ASCII, más las tildes y
  la eñe del español.
- Numeración de semanas a dos dígitos: `semana-01`, nunca `semana-1`.
- Las salidas de terminal que aparecen en las guías son reales, producidas al ejecutar el mismo
  código que se publica.

## Configuración de GitHub Pages

Settings, Pages, Source: **Deploy from a branch**, rama `main`, carpeta `/docs`.

El archivo `docs/.nojekyll` es necesario: sin él GitHub procesa el sitio con Jekyll y descarta las
carpetas que empiezan con guion bajo, que es donde Quarto pone estilos y scripts. Va declarado
como recurso en `_quarto.yml` porque cada render recrea `docs/` desde cero.
