# Proyectos Python DCAO

## Descripción

En este repositorio se presentan algunos ejemplos de código desarrollados en el marco de un proyecto del *Departamento de Ciencias de la Atmósfera y los Océanos* (DCAO) perteneciente a la Facultad de Ciencias Exactas y Naturales de la Universidad de Buenos Aires.

En este proyecto se trabajó con herramientas provistas de forma libre por Unidata y se avanzó en la unificación de diversas fuentes de información para generar productos de utilidad para el personal docente y el alumnado en las clases.

Algunas de las herramientas de Unidata utilizadas fueron:
- [python-awips](http://unidata.github.io/python-awips/)
- [Servidor EDEX basado en la nube](https://www.unidata.ucar.edu/blogs/news/entry/awips-tips-get-to-know)
- [Metpy](https://unidata.github.io/MetPy/latest/index.html)
- [THREDDS](https://thredds.ucar.edu/thredds/catalog/catalog.html) y [Siphon](https://unidata.github.io/siphon/latest/index.html)

Todos ellos son provistos por Unidata de forma gratuita con el propósito de ser utilizados en entornos educativos.

## Forma de utilización

### Ejecución en la nube

#### Instalación de librerías

En la carpeta `ejemplos` se presentan algunas *notebook* de *Jupyter/IPython* que se recomienda ejecutar en [Google Colab](https://colab.research.google.com/) dada la practicidad de esta herramienta para ejecutar código en la nube.

Como primer paso se deben instalar las librerías/bibliotecas necesarias que no se encuentran instaladas por defecto en la máquina virtual de Colab. **Aclaración**: Estas líneas se ejecutan dentro de la *notebook* pero se dejan aquí por completitud.

```bash
!pip install python-awips
!pip install metpy
!pip install siphon
```

Luego es necesario instalar librerías/bibliotecas adicionales para realizar gráficos georeferenciados. *Aclaración:* Shapely puede ser instalada a través del gestor `pip` aunque puede ser necesario previamente instalar GDAL y Proj a través del gestor del sistema `apt`.

```bash
#!apt-get install -qq libgdal-dev libproj-dev
!pip install --no-binary shapely shapely --force
!pip install cartopy
```

**IMPORTANTE**

No se testeó la capacidad de ejecutar este código en una instancia local (por ejemplo, descargando Anaconda y utilizando su gestor de librerías para [instalar las necesarias](http://unidata.github.io/python-awips/#conda-install) y adicionales). En ese caso los bloques de código anteriores deben ejecutarse antes de correr el resto de la notebook.

#### Código en Python para generar figuras georeferenciadas

Luego en cada notebook se muestra la forma para descargar los datos de las distintas fuentes de información que incluyen, entre otros:

- Datos del ABI/GOES-16
- METAR de lugares seleccionados
- Datos de GFS (versión 0,25°)

### Trabajos futuros

Es posible a través de Siphon acceder a datos de radiosondeos de la base de datos de la Universidad de Wyoming. Combinando esta información con Metpy puede obtenerse un diagrama aerológico de muy bajo costo computacional. Esto puede, además, combinarse con la utilización de los catálogos THREDDS para obtener los mismos diagramas pero con información del modelo GFS. Además, existen en algunos catálogos de THREDDS información del ensamble del GFS.
