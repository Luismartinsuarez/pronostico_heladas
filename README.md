# Pronóstico de heladas en la estación J2 El Mantaro

Análisis y pronóstico de heladas de corto plazo (1 a 6 horas) en la estación automática J2 El Mantaro (Junín, Perú, 3314 m), con datos horarios de 2022 a 2026, un sensor de humedad de hoja y la nubosidad pronosticada por Open-Meteo.

## Estructura

```
data/
  external/   pronósticos de Open-Meteo (nubosidad, GFS, ECMWF) y altitud
  indices/    índices diarios, mensuales y por campaña
  raw/        datos crudos de las estaciones (no incluidos)
  processed/  series horarias y diarias procesadas (no incluidas)
notebooks/    análisis y modelos (ver abajo)
resultados/   métricas y tablas en CSV
  modelos/    modelos entrenados .joblib (no incluidos; se generan con los notebooks)
```

## Notebooks

| Notebook | Contenido |
|---|---|
| `el_mantaro_analisis_heladas.ipynb` | Climatología de las heladas de J2: temporada, intensidad, rachas |
| `heladas_humedad_hoja.ipynb` | Exploración del sensor de humedad de hoja |
| `el_mantaro_heladas_hoja.ipynb` | Tipo de helada (blanca/negra) con el sensor de hoja y modelo con variables de hoja |
| `el_mantaro_heladas_nubosidad.ipynb` | **Modelo operativo (v2)**: gradient boosting + nubosidad, calibración de Platt, tipo de helada con regresión logística; guarda el modelo y define `pronosticar()` |
| `el_mantaro_comparacion_modelos.ipynb` | Comparación con Random Forest y regresión logística; prueba de calibración |
| `el_mantaro_comparacion_gfs_ecmwf.ipynb` | Comparación con GFS y ECMWF, crudos y corregidos |
| `el_mantaro_heladas_ecmwf.ipynb` | Prueba de ECMWF como variable del modelo |
| `pronostico_heladas_1a6h.ipynb` | Primera versión: modelo regional para 9 estaciones |

## Requisitos

Python 3.11 con `pandas`, `numpy`, `scikit-learn` (1.9), `matplotlib` y `joblib`. Los notebooks necesitan los datos de `data/processed/`, que no se incluyen en el repositorio.
