# S8--Explorando-factores-de-comportamiento-en-NovaRetail-

## 📌 Descripción del Proyecto
**NovaRetail+** es una plataforma de comercio electrónico líder en Latinoamérica con millones de usuarios activos. Este proyecto realiza un **análisis exploratorio y correlacional** enfocado en el área de **Crecimiento y Retención** para responder a la siguiente pregunta estratégica de negocio:

> **¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?**

> ⚠️ **Nota metodológica:** Este estudio identifica asociaciones estadísticamente significativas entre variables, pero **no implica ni prueba relación de causalidad** (*Correlación ≠ Causalidad*).

---

## 🛠️ Tecnologías y Librerías Utilizadas
El análisis se desarrolló en Python utilizando el siguiente *stack* analítico:

* **Manipulación de Datos:** `pandas`, `numpy`
* **Visualización de Datos:** `seaborn`, `matplotlib`
* **Análisis Estadístico:** `scipy.stats` (`chi2_contingency`, `pointbiserialr`)

---

## 📂 Estructura del Dataset
El dataset consta de **15,000 registros** y **12 variables** sin valores nulos:

| Columna | Tipo | Descripción |
| :--- | :--- | :--- |
| `id_cliente` | Categoría (Object) | Identificador único del cliente. |
| `edad` | Numérica (Int) | Edad del cliente (18 a 75 años). |
| `nivel_ingreso` | Numérica (Float) | Ingreso anual estimado del usuario. |
| `visitas_mes` | Numérica (Int) | Frecuencia de visitas mensuales a la app o sitio web. |
| `compras_mes` | Numérica (Int) | Compras realizadas en el último mes. |
| `gasto_publicidad_dirigida` | Numérica (Float) | Presupuesto publicitario asignado al usuario. |
| `satisfaccion` | Numérica (Float) | Calificación de satisfacción del cliente (Escala 1 al 5). |
| `miembro_premium` | Binaria (0/1) | Suscripción activa a membrecía premium. |
| `abandono` | Binaria (0/1) | Indicador de Churn / Abandono de la plataforma. |
| `tipo_dispositivo` | Categoría | Dispositivo de acceso (`móvil`, `escritorio`, `tablet`). |
| `region` | Categoría | Zona geográfica (`norte`, `sur`, `este`, `oeste`). |
| `ingreso_anual` | Numérica (Float) | **Variable Objetivo:** Ingreso anual generado para NovaRetail+. |

---

## 🔬 Metodología Estadística y Supuestos

Para evaluar las relaciones entre las distintas variables y el `ingreso_anual`, se aplicaron coeficientes específicos según la naturaleza de las variables:

1. **Pearson:** Relaciones lineales entre variables numéricas continuas/discretas.
2. **Spearman:** Evaluaciones monótonas no paramétricas.
3. **Correlación Punto Biserial:** Asociación entre variables continuas e dicotómicas/binarias (`miembro_premium`, `abandono`).
4. **V de Cramér / Chi-Cuadrada:** Asociación entre variables puramente categóricas.

---

📈 Conclusiones Clave
### Hallazgo 1 — Correlacion fuerte entre gastos de publicidad y visitas al mes

**Evidencia visual:**  
Revisar grafico_1 en apartado 3.3
   
**Evidencia numérica:**  
Correlacion Pearson para Visitas Mensuales/Gasto de publicidad:  0.5789472719412827  
Correlacion Spearman para Visitas Mensuales/Gasto de publicidad:  0.5592673242622609

**Interpretación**  
Se observa una correlacion fuerte entre gastos de publicidad y visitas al mes. Lo que nos dice que probablemente la tienda es mas visitada en los meses que se llevo acabo inversion en publicidad.

**No podemos afirmar**  
Que efectivamente las visitas hayan incrementado a causa de la publicidad. pudiendo haber alguna otra variable oculta que este influyendo en el incremento de visitas

**Implicación de negocio**  
Realizando la investigacion pertinente se pudiera encontrar fectivamente la relacion que existe entre la publicidad y el incremento de visitas

### Hallazgo 2 — Correlacion moderada entre visitas al mes e ingresos anuales

**Evidencia visual:**  
Revisat grafico_2 en apartado 3.3

**Evidencia numérica:**  
Correlacion Pearson para Visitas Mensuales/Ingreso Anual:  0.3371466432498745  
Correlacion Spearman para Visitas Mensuales/Ingreso Anual:  0.32095369737696483

**Interpretación**   
Se observa una correlacion moderada entre visitas al mes e ingresos anuales. Lo que nos dice que los meses donde la tienda fue visitada con mayor frecuencia los clientes compraron mas y beneficiaron al ingreso_anual

**No podemos afirmar**  
Que regiones fueron las mas visitadas y cuales fueron las que tuvieron una mayor aportacion al ingreso anual

**Implicación de negocio**  
Incrementando las visitas beneficia las compras mensuales y por consiguiente el ingreso anual

