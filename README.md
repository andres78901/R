 # 📊 Proyecto de Análisis de Datos en R

## 🚀 Descripción

Este proyecto tiene como objetivo consumir datos desde una API externa, procesarlos y generar visualizaciones para el análisis exploratorio. Se trabajan indicadores económicos (como PIB per cápita) organizados por país y año.

---

## 🧰 Tecnologías utilizadas

* **R**
* **tidyverse** (dplyr, ggplot2)
* **httr / jsonlite** (consumo de APIs)
* **ggplot2** (visualización de datos)

---

## 📡 Fuente de datos

Los datos son obtenidos desde una API pública (por ejemplo: World Bank API), lo que permite trabajar con información real y actualizada.

---

## ⚙️ Instalación

1. Clonar el repositorio:

```bash
git clone git@github.com:tu_usuario/tu_repositorio.git
```

2. Abrir el proyecto en RStudio

3. Instalar dependencias:

```r
install.packages(c("tidyverse", "httr", "jsonlite"))
```

---

## 🧪 Uso

### 1. Consumo de API

Se realiza la consulta a la API y se almacenan los datos en una lista:

```r
library(httr)
library(jsonlite)

response <- GET("URL_DE_LA_API")
data_list <- fromJSON(content(response, "text"))
```

---

### 2. Limpieza de datos

Transformación a dataframe y filtrado:

```r
library(dplyr)

data <- data_list[[2]]

df <- data %>%
  select(
    country = country.value,
    year = date,
    gdp_per_capita = value
  ) %>%
  filter(!is.na(gdp_per_capita)) %>%
  mutate(year = as.numeric(year))
```

---

### 3. Visualizaciones

#### 📌 Heatmap

Permite observar patrones por país y año:

```r
library(ggplot2)

ggplot(df, aes(x = year, y = country, fill = gdp_per_capita)) +
  geom_tile() +
  theme_minimal()
```

---

#### 📌 Gráfico polar

Ideal para representar distribuciones:

```r
ggplot(df, aes(x = factor(year), y = gdp_per_capita, fill = country)) +
  geom_bar(stat = "identity") +
  coord_polar()
```

---

## 📁 Estructura del proyecto

```
├── data/           # Datos procesados
├── scripts/        # Scripts en R
├── outputs/        # Gráficos generados
├── README.md
```

---

## 📈 Objetivos

* Consumir datos desde APIs
* Limpiar y transformar datos
* Generar visualizaciones útiles
* Aplicar buenas prácticas en R

---

## 🧠 Posibles mejoras

* Agregar más indicadores económicos
* Implementar dashboards con Shiny
* Automatizar la actualización de datos
* Exportar resultados a CSV o Excel

---

## 👨‍💻 Autor

**Andres Lopez**

---

## 📄 Licencia

Este proyecto es de uso educativo y libre para modificación.

---
