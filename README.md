# Modelado estocástico de retornos financieros

Tesis de pregrado en Física — Universidad Nacional de Colombia (Ago 2024 – Jul 2025)

## El problema

Los modelos clásicos de retornos financieros (movimiento browniano, supuesto gaussiano)
subestiman sistemáticamente la probabilidad de eventos extremos en los mercados. Esto
es un problema crítico para gestión de riesgo: el VaR calculado bajo normalidad falla
justo cuando más se necesita, durante crisis y movimientos abruptos.

Este trabajo calibra un modelo estocástico no gaussiano —derivado de una ecuación de
Fokker-Planck no lineal— que captura naturalmente las **colas pesadas** observadas en
series financieras reales.

## Qué hice

- Implementé la solución analítica y la simulación numérica del modelo (proceso
  estocástico tipo q-gaussiano) en Python.
- Calibré el modelo contra series reales de tres mercados:
  - **Renta variable** de Vilnius Stock Exchange y Warsaw Stock Exchange (datos
    minuto-a-minuto, más de 2 años).
  - **COP/USD** (datos diarios, 2 años).
  - **Forex y cripto** (en extensión hacia publicación, datos minuto-a-minuto).
- Realicé análisis multiescala para identificar horizontes de convergencia y
  propiedades fractales en las series.
- Construí pipelines reproducibles end-to-end: ingesta → limpieza → simulación →
  evaluación → backtesting.

## Resultados principales

- El modelo q-gaussiano supera al supuesto gaussiano tanto en **MAPE** como en el
  ajuste al exponente de la ley de potencias que rige las colas de la distribución
  empírica.
- Se identificaron horizontes temporales óptimos en los que la dependencia de la
  serie es máxima, relevantes para diseño de estrategias y estimación de VaR.

## Stack técnico

`Python` · `NumPy` · `SciPy` · `pandas` · `Matplotlib` · `Jupyter` · procesos
estocásticos · ecuaciones de Fokker-Planck · análisis multiescala

## Contenido del repositorio

- `Simulation.ipynb` — simulación principal del modelo.
- `Simulation-q-gauss.ipynb` — variante con distribución q-gaussiana.
- `Convergence.ipynb` / `Convergence - q.ipynb` — análisis de convergencia y
  caracterización de horizontes.
- `vilnius_*.txt`, `warsaw_*.txt` — datos de cierre de varios activos en los
  mercados de Vilnius y Varsovia.
- `Trabajo_Version_final.pdf` — documento final de tesis.
- `Poster - Versión 5.pdf` — póster de presentación.

## Aplicaciones del enfoque

- Estimación de **VaR** y **CVaR** con colas pesadas.
- Modelado de eventos extremos en gestión de riesgo cuantitativo.
- Diseño de estrategias sensibles a la escala temporal.
- Caracterización de regímenes en series temporales de alta frecuencia (aplicable
  también a precios energéticos, demanda eléctrica, etc.).
