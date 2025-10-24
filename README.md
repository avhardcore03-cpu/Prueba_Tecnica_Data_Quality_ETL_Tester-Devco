# Prueba Técnica: Data Quality ETL Tester

Este repositorio contiene el script de un Jupyter Notebook desarrollado como parte de la prueba técnica para el rol de **Data Quality ETL Tester**.

El objetivo de este script es demostrar un framework de pruebas en Python, usando la librería **Pandas**, para validar la calidad e integridad de los datos en un proceso ETL simulado.

---

## 🚀 Habilidades y Pruebas Demostradas

El notebook `Validacion_ETL_Data_Quality.ipynb` ejecuta un conjunto de pruebas de calidad de datos que simulan las validaciones más comunes en un entorno de QA de datos:

### 1. Pruebas de Completitud
* **Qué hace:** Verifica que los campos obligatorios no contengan valores nulos (`np.nan`).
* **Comando clave:** `.isnull().sum()`

### 2. Pruebas de Unicidad
* **Qué hace:** Asegura que no existan valores duplicados en columnas clave (ej. `email`), excluyendo los nulos de la validación.
* **Comando clave:** `.dropna()` y `.duplicated(keep=False)`

### 3. Pruebas de Integridad Referencial
* **Qué hace:** Identifica registros "huérfanos" (ej. transacciones sin un cliente válido) simulando un `LEFT JOIN` de SQL.
* **Comando clave:** `pd.merge(how='left', indicator=True)` y filtrando por `left_only`.

### 4. Pruebas de Reconciliación
* **Qué hace:** Compara totales agregados entre los datos de origen (transformados) y los datos de destino (limpios) para encontrar discrepancias. Simula un `FULL OUTER JOIN` con `COALESCE`.
* **Comando clave:** `pd.merge(how='outer')`, `.fillna(0)` y cálculo de diferencias.

---

## 🛠️ Tecnologías Utilizadas

* **Python**
* **Pandas**
* **Jupyter Notebook**
