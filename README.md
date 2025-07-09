
# Análisis de Evasión de Clientes (Churn) en TelecomuX (Challenge de Alura Latam)

Este proyecto realiza un análisis exploratorio de datos (EDA) para identificar los factores que influyen en la evasión de clientes (churn) en una empresa de telecomunicaciones. El objetivo es comprender las razones detrás de la decisión de un cliente de abandonar la empresa y utilizar estos insights para desarrollar estrategias de retención efectivas.

## Contenido

- [Introducción](#introducción)
- [Fuente de Datos](#fuente-de-datos)
- [Limpieza y Tratamiento de Datos](#limpieza-y-tratamiento-de-datos)
- [Análisis Exploratorio de Datos](#análisis-exploratorio-de-datos)
    - [Distribución de Churn](#distribución-de-churn)
    - [Análisis de Churn por Variables Categóricas](#análisis-de-churn-por-variables-categóricas)
    - [Análisis de Churn por Variables Numéricas](#análisis-de-churn-por-variables-numéricas)
- [Conclusiones e Insights](#conclusiones-e-insights)
- [Recomendaciones](#recomendaciones)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)

## Introducción

La evasión de clientes (churn) es un desafío crítico en la industria de las telecomunicaciones. Este proyecto busca analizar un conjunto de datos de clientes para identificar patrones y variables que están fuertemente correlacionadas con la decisión de un cliente de darse de baja.

## Fuente de Datos

El conjunto de datos utilizado es `TelecomX_Data.json`, disponible en un repositorio de GitHub. Contiene información sobre los clientes, sus servicios de teléfono e internet, detalles de la cuenta y su estado de evasión (Churn).

## Limpieza y Tratamiento de Datos

El proceso de limpieza y tratamiento de datos incluyó los siguientes pasos:

1.  **Carga de Datos:** Los datos se cargaron directamente desde la URL del archivo JSON.
2.  **Normalización de Datos JSON:** La estructura anidada del JSON se aplanó utilizando `pd.json_normalize()` para crear un DataFrame plano.
3.  **Renombrado de Columnas:** Se renombraron las columnas para mejorar la legibilidad y el manejo.
4.  **Manejo de Valores Nulos:** Se identificaron los valores nulos, particularmente en la columna `Charges_Total`.
5.  **Verificación de Duplicados:** Se verificó la unicidad de los clientes usando `customerID`.
6.  **Conversión de Tipos de Datos:** La columna `Charges_Total` se convirtió de tipo 'object' a numérico, manejando errores de conversión.
7.  **Creación de Nuevas Características:** Se calculó una nueva columna `Cuentas_Diarias` (Cargos Mensuales / 30).

## Análisis Exploratorio de Datos

Se realizó un análisis exhaustivo utilizando visualizaciones para comprender las relaciones entre las variables y el Churn.

### Distribución de Churn

Se analizó la proporción de clientes que han cancelado su servicio (Churn) en comparación con los que permanecen.

### Análisis de Churn por Variables Categóricas

Se examinó cómo diferentes características categóricas se relacionan con la tasa de Churn, incluyendo:

- Género
- Senior Citizen
- Partner
- Dependents
- Phone Service
- Multiple Lines
- Internet Service (identificando 'Fiber optic' como de alto riesgo)
- Online Security, Online Backup, Device Protection, Tech Support (identificando la ausencia como factor de riesgo)
- Contract (identificando 'Month-to-month' como de alto riesgo)
- Paperless Billing
- Payment Method (identificando 'Electronic check' como asociado a mayor Churn)

### Análisis de Churn por Variables Numéricas

Se analizaron las distribuciones de variables numéricas (`tenure`, `Charges_Monthly`, `Charges_Total`) para los grupos de clientes que cancelaron y los que no, encontrando que:

- Clientes con menor `tenure` (antigüedad) son más propensos a cancelar.
- Clientes con `Charges_Monthly` y `Charges_Total` más altos (especialmente asociados con fibra óptica) tienden a tener una mayor tasa de Churn.

## Conclusiones e Insights

Los hallazgos clave del análisis exploratorio incluyen:

- La antigüedad del cliente (`tenure`) es un fuerte predictor de Churn.
- El tipo de contrato (`Month-to-month`) está fuertemente asociado con una mayor evasión.
- Los servicios de internet de fibra óptica y los altos cargos mensuales presentan un mayor riesgo de Churn.
- La falta de servicios de valor agregado (seguridad, soporte) aumenta la probabilidad de Churn.
- Ciertos métodos de pago y la facturación electrónica están correlacionados con una mayor evasión.

## Recomendaciones

Basado en los insights, se proponen las siguientes recomendaciones para reducir la evasión de clientes:

- Focalizarse en la retención de nuevos clientes.
- Promover contratos a largo plazo mediante incentivos.
- Investigar las posibles causas del alto Churn en clientes con fibra óptica.
- Incentivar la contratación de servicios de seguridad y soporte en línea.
- Analizar y optimizar los procesos asociados con métodos de pago de alto riesgo y la facturación electrónica.
- Desarrollar modelos predictivos de Churn para identificar clientes en riesgo.
- Ofrecer intervenciones y beneficios personalizados a clientes de alto riesgo.

## Tecnologías Utilizadas

- Python
- Pandas
- Matplotlib
- Seaborn
- Google Colaboratory / Jupyter Notebooks

