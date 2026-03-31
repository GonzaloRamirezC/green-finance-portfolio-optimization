# Descarbonización de Portafolios: Maximizando la Eficiencia Financiera bajo Mandatos WACI

Este repositorio está diseñado como material educativo para cursos de finanzas sostenibles a nivel de pregrado. Contiene la implementación en Python de un modelo cuantitativo para la optimización de portafolios de inversión bajo criterios ESG. Específicamente, el modelo **maximiza el Ratio de Sharpe** de una cartera de renta variable sujeta a una restricción estricta de intensidad de carbono (Weighted Average Carbon Intensity - WACI)

## Características del Proyecto

* **Mandato de Carbono Activo:** Implementa una restricción superior para el WACI del portafolio, forzando la reasignación de capital hacia activos menos intensivos en carbono.
* **Análisis de Trade-off:** Calcula y compara las métricas de riesgo/retorno (Retorno Esperado, Volatilidad, Ratio de Sharpe) entre el portafolio *Constrained* (Verde) y el *Unconstrained* (Tradicional).
* **Visualización de Pesos:** Genera gráficos comparativos para ilustrar la reasignación de capital necesaria para cumplir con el mandato ambiental.
* **Optimización:** Utiliza el algoritmo `SLSQP` (Sequential Least SQuares Programming) de la librería `SciPy`.

## Marco Matemático

El problema se define como la maximización de la eficiencia financiera (Ratio de Sharpe), sujeto a restricciones de inversión total y límites de emisiones de Gases de Efecto Invernadero (GEI):

$$\max_{\mathbf{w}} \quad \frac{\mathbf{w}^\top \boldsymbol{\mu} - R_f}{\sqrt{\mathbf{w}^\top \boldsymbol{\Sigma} \mathbf{w}}}$$

**Sujeto a:**
1.  **Restricción de presupuesto (fully invested):** $\sum_{i=1}^{n} w_i = 1$
2.  **Restricción Long-Only:** $0 \leq w_i \leq 1 \quad \forall i$
3.  **Mandato de Carbono (ESG):** $\mathbf{w}^\top \mathbf{c} \leq \text{WACI}_{\text{target}}$

Donde:
* $\mathbf{w}$: Vector de pesos del portafolio.
* $\boldsymbol{\mu}$: Vector de retornos esperados.
* $\boldsymbol{\Sigma}$: Matriz de varianzas y covarianzas.
* $R_f$: Tasa libre de riesgo (fijada en 4.33%).
* $\mathbf{c}$: Vector de intensidades de carbono de cada activo.

## Resultados Clave

El modelo demuestra que es posible descarbonizar significativamente un portafolio manteniendo un perfil de rentabilidad/riesgo altamente competitivo. La diferencia en el Ratio de Sharpe entre el portafolio óptimo sin restricciones y el portafolio alineado al mandato verde representa el **costo cuantitativo de la sostenibilidad**, el cual, según los datos de este análisis, resulta ser, en este ejercicio, un trade-off marginal y potencialmente asumible para inversores institucionales.

## Tecnologías y Librerías

* `Python 3.x`
* `NumPy` (Álgebra lineal y operaciones vectoriales)
* `Pandas` (Manipulación de datos financieros)
* `SciPy` (Optimización matemática `scipy.optimize.minimize`)
* `Matplotlib` (Visualización de datos)

## Autor

**Gonzalo Ramírez-Carrillo**
* Quantitative Researcher | AI & Climate Finance | Structural Value Investing

## Citación

Si utilizas este código o te inspiras en esta metodología para tu investigación, por favor cita este repositorio utilizando el siguiente formato BibTeX:

```bibtex
@misc{ramirez_carrillo_2026_portafolio,
  author       = {Ramírez-Carrillo, Gonzalo},
  title        = {Green Finance Portfolio Optimization with Carbon Constraint},
  year         = {2026},
  howpublished = {\url{https://github.com/GonzaloRamirezC/green-finance-portfolio-optimization}},
  note         = {GitHub repository}
}
