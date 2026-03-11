# ⚽ Cruz Azul Stats 2025/2026 — Web Scraping & Análisis de Datos

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python) ![Selenium](https://img.shields.io/badge/Selenium-4.x-green?logo=selenium) ![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas) ![Status](https://img.shields.io/badge/Status-Completado-brightgreen)

## 📋 Descripción

Proyecto de **Web Scraping y Análisis de Datos** de las estadísticas del equipo **Cruz Azul** en la temporada **2025/2026 de la Liga MX**. Los datos fueron extraídos de [FBref.com](https://fbref.com) utilizando Selenium para superar la protección anti-bots de Cloudflare, y analizados con Pandas y Matplotlib.

---

## 🎯 Objetivos

- Extraer automáticamente estadísticas de jugadores y resultados de partidos desde FBref
- Limpiar y estructurar los datos obtenidos
- Generar visualizaciones que comuniquen insights clave del equipo

---

## 🛠️ Herramientas y Tecnologías

| Herramienta | Uso |
|---|---|
| `Python 3.11` | Lenguaje principal |
| `Selenium + undetected-chromedriver` | Web Scraping (bypass Cloudflare) |
| `BeautifulSoup4` | Parseo de HTML |
| `Pandas` | Limpieza y análisis de datos |
| `Matplotlib + Seaborn` | Visualización de datos |

---

## 📂 Estructura del Proyecto

```
📁 Cruz-Azul-Stats-2026/
├── cruz_azul_2026.ipynb              # Notebook principal
├── cruz_azul_jugadores_2026.csv      # Dataset de jugadores
├── cruz_azul_partidos_2026.csv       # Dataset de partidos
├── top_goleadores.png                # Gráfica top 10 goleadores
├── goles_asistencias.png             # Gráfica goles vs asistencias
├── minutos_jugados.png               # Gráfica minutos por jugador
└── README.md
```

---

## 🔍 Proceso

### 1. Web Scraping
FBref utiliza protección de Cloudflare que bloquea peticiones HTTP convencionales (`requests`). La solución fue usar `undetected-chromedriver`, que simula un navegador humano real para evadir la detección.

```python
import undetected_chromedriver as uc

driver = uc.Chrome(options=options, version_main=145)
driver.get(URL)
time.sleep(15)  # Tiempo para que Cloudflare valide
```

Las tablas de estadísticas en FBref están embebidas como comentarios HTML, por lo que fue necesario extraerlas con BeautifulSoup antes de parsearlas con Pandas.

### 2. Limpieza de Datos
- Aplanamiento de columnas multi-nivel (MultiIndex)
- Eliminación de filas de totales (`Squad Total`, `Opponent Total`)
- Conversión de columnas a tipos numéricos

### 3. Análisis y Visualización
Se generaron 3 gráficas con la paleta de colores oficial de Cruz Azul (`#003087`, `#4A90D9`):

---

## 📊 Resultados

### Top 10 Goleadores
![Top Goleadores](top_goleadores.png)

### Goles y Asistencias por Jugador
![Goles y Asistencias](goles_asistencias.png)

### Minutos Jugados por Jugador
![Minutos Jugados](minutos_jugados.png)

---

## 💡 Insights Principales

- **Gabriel Fernández** es el máximo goleador con 10 goles en la temporada
- **José Paradela** lidera en participación directa (goles + asistencias)
- **Willer Ditta** es el jugador con más minutos disputados (2,362 min), siendo el más utilizado por el cuerpo técnico
- La plantilla muestra una distribución de minutos concentrada en 6-7 jugadores titulares indiscutibles

---

## ▶️ Cómo ejecutar

```bash
# 1. Clonar el repositorio
git clone https://github.com/tu-usuario/cruz-azul-stats-2026.git

# 2. Instalar dependencias
pip install undetected-chromedriver pandas matplotlib seaborn beautifulsoup4

# 3. Abrir el notebook
jupyter notebook cruz_azul_2026.ipynb
```

> ⚠️ **Nota:** Al ejecutar el scraping se abrirá una ventana de Chrome visible. No la cierres — es necesaria para pasar la validación de Cloudflare.

---

## 👤 Autor

Proyecto desarrollado como parte de un portafolio de análisis de datos.

**Fuente de datos:** [FBref.com](https://fbref.com/en/squads/632f1838/2025-2026/Cruz-Azul-Stats)
