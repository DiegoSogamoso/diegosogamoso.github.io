---
date: 2021-06-11 22:55:45
layout: post
title: Creción de indices financieros en Python
subtitle: Lorem ipsum dolor sit amet, consectetur adipisicing elit.
description: Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559821647/theme2_ylcxxz.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559821647/theme2_ylcxxz.jpg
category: code
tags:
  - python
  - finance
  - index
  - currencies
author: Diego Sogamoso
---
Cas sociis natoque penatibus et magnis <a href="#">dis parturient montes</a>, nascetur ridiculus mus. *Aenean eu leo quam.* Pellentesque ornare sem lacinia quam venenatis vestibulum. Sed posuere consectetur est at lobortis. Cras mattis consectetur purus sit amet fermentum.

> Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.

Etiam porta **sem malesuada magna** mollis euismod. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur.

## Instalación de Paquetes 

#### Paquetes Base

Para la creación de los indices financieros necesitaremos los paquetes base de Python. Dentro de estos encontramos dos principales, el primero es **Pandas Datareader**, el cual nos facilitara el manejo de bases de datos (DataFrames).

En el segundo lugar, hacemos uso de **Numpy** o Numerical Python, el cual brinda las herramientas matematicas y algebraicas que utilizaremos en la creación de nuestros indices.


```py
# Paquete Pandas Datareader
import pandas as pd

# Paquete Numerical Python
import numpy as np
```

#### Manejo de Fechas 

Para el manejo de fechas seran esenciales, las funciones timedelta (), date (), y datetime(), las cuales hacen parte del paquete datetime, el cual es uno de los paquetes preferidos  por los cientificos de datos para el tratamiento de data cronologica.

``` py
# Importando la funcion timedelta
from datetime import timedelta 

# Importando la funcion date
from datetime import date

# Importando la funcion datetime
from datetime import datetime

```


#### API Financiera

En la creación de nuestro indice es esencial tener un **API** (Application Programming Interface) o en español una interfaz de programacion de aplicaciones, la cual permitira conectarnos desde python a diferentes lugares de la web. En nuestro caso, nos permitira extraer informacion de distintos repositorios como Yahoo finance, Google Finance, etc.

De esta manera, usaremos `Y Finance` , el cual es uno de los paquetes mas usados para la extracción de datos historicos financieros directamente desde Yahoo finance. Nota que antes de importarlo debes instalarlo en tu maquina, por lo que cuando encuentres la expresión `!pip install`, significara que estas instalando un paquete que nunca antes habias corrido en tu pc o en tu interfaz. Mas adelante explicaremos como se debe usar correctamente el paquete.

```  py
# Instalando Y finance en el disco local
!pip install yfinance

# Importación del paquete
import yfinance as yf
```

#### Graficación

Python ofrece una amplia gama de herramientas para la graficación de cualquier tipo de datos, Matplotlib y Plotly son las principales a la hora del analisis grafico.

Sus diferencias radican en el tipo de grafico al cual le dan salida, mientras matplotlib arroja graficos estaticos, mediante Plotely podriamos llegar a generar graficos dinamicos, los cuales pueden llegar a ser mucho mas utiles. En este ejercicio usaremos ambas herramientas, para que el usuario final escoja cual es de su preferencia.

``` py
# Importando Matplotlib
import matplotlib.pyplot as plt

# Importando Plotly
import plotly.graph_objs as go
```
> **Nota:** Como se puede observar del paquete matplotlib importamos su subfunción ***pyplot***, la cual almacenaremos como `plt`. Mientras que para plotly usamos la subfuncion ***graph_objects*** la cual almacenamos por facilidad como `go`.


Una vez tengas instalados e importados los anteriores paquetes, podras proceder al siguiente paso!



## Selección de Activos (Security Selection) 

La seleccion de activos es el paso mas importante de nuestra estructuracion del indice, ya que en el  podremos darle rienda suelta a nuestras preferencias y escoger un set de activos que nos parezca atractivo o que preferiblemente despues de un analisis fundamental muestre señales significativas de evidenciar  el comportamiento de un sector o de un mercado en especial. 

Para ejemplo tomaremos los activos de la tabla 1, los cuales son pares emergentes negociados en el mercado Forex (Currency Market). Sin embargo, el procedimiento sera el mismo para cualquier set diferente de activos. 

<table>
  <thead>
    <tr>
      <th>Activo</th>
      <th>Nombre</th>
      <th>Ticker</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>USDCOP</td>
      <td>Peso Colombiano</td>
      <td>USDCOP=X</td>
    </tr>
    <tr>
      <td>USDMXN</td>
      <td>Peso Mexicano</td>
      <td>MXN=X</td>
    </tr>
    <tr>
      <td>USDCLP</td>
      <td>Peso Chileno</td>
      <td>CLP=X</td>
    </tr>
    <tr>
      <td>USDBRL</td>
      <td>Real Brasilero</td>
      <td>BRL=X</td>
    </tr>
    <tr>
      <td>USDCAD</td>
      <td> Dolar Canadiense </td>
      <td>CAD=X</td>
    </tr>
    <tr>
      <td>USDRUB</td>
      <td>Rublo Ruso</td>
      <td>RUB=X</td>
    </tr>
    <tr>
      <td>USDZAR</td>
      <td>Rand Sudafricano</td>
      <td>ZAR=X</td>
    </tr>
     <tr>
      <td>USDIDR</td>
      <td>Ruphia Indonesa</td>
      <td>USDIDR=X</td>
    </tr>  
  </tbody>
</table>











HTML defines a long list of available inline tags, a complete list of which can be found on the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).

- **To bold text**, use `<strong>`.
- *To italicize text*, use `<em>`.
- Abbreviations, like <abbr title="HyperText Markup Langage">HTML</abbr> should use `<abbr>`, with an optional `title` attribute for the full phrase.
- Citations, like <cite>&mdash; Thiago Rossener</cite>, should use `<cite>`.
- <del>Deleted</del> text should use `<del>` and <ins>inserted</ins> text should use `<ins>`.
- Superscript <sup>text</sup> uses `<sup>` and subscript <sub>text</sub> uses `<sub>`.

Most of these elements are styled by browsers with few modifications on our part.

# Heading 1

## Heading 2

### Heading 3

#### Heading 4

Vivamus sagittis lacus vel augue rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Morbi leo risus, porta ac consectetur ac, vestibulum at eros.

## Code

Cum sociis natoque penatibus et magnis dis `code element` montes, nascetur ridiculus mus.

```js
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those arguments
var adder = new Function("a", "b", "return a + b");

// Call the function
adder(2, 6);
// > 8
```


```py
# Hello World!
```




Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa.

## Lists

Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.

* Praesent commodo cursus magna, vel scelerisque nisl consectetur et.
* Donec id elit non mi porta gravida at eget metus.
* Nulla vitae elit libero, a pharetra augue.

Donec ullamcorper nulla non metus auctor fringilla. Nulla vitae elit libero, a pharetra augue.

1. Vestibulum id ligula porta felis euismod semper.
2. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
3. Maecenas sed diam eget risus varius blandit sit amet non magna.

Cras mattis consectetur purus sit amet fermentum. Sed posuere consectetur est at lobortis.

Integer posuere erat a ante venenatis dapibus posuere velit aliquet. Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Nullam quis risus eget urna mollis ornare vel eu leo.

## Images

Quisque consequat sapien eget quam rhoncus, sit amet laoreet diam tempus. Aliquam aliquam metus erat, a pulvinar turpis suscipit at.

![placeholder](https://placehold.it/800x400 "Large example image")
![placeholder](https://placehold.it/400x200 "Medium example image")
![placeholder](https://placehold.it/200x200 "Small example image")

## Tables

Aenean lacinia bibendum nulla sed consectetur. Lorem ipsum dolor sit amet, consectetur adipiscing elit.



Nullam id dolor id nibh ultricies vehicula ut id elit. Sed posuere consectetur est at lobortis. Nullam quis risus eget urna mollis ornare vel eu leo.















