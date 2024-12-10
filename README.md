# ESRD-lab-analysis
Dashboard interactivo para analizar valores de laboratorio ESRD utilizando datos sintéticos generados por Synthea
Análisis y Visualización de Valores de Laboratorio ESRD
Objetivo: analizar nuestro censo mensual de pacientes con Enfermedad Renal en Etapa Terminal (ESRD) durante el año 2022 y evaluar sus valores de laboratorio mensualmente para:
Calcio
Sodio
Albúmina
Nitrógeno ureico en sangre (BUN)
Queremos rastrear cuándo un paciente no realizó su análisis de laboratorio en un mes determinado o no cumplió con los valores objetivo. También buscamos determinar el porcentaje de nuestra cohorte que alcanzó los objetivos organizacionales y analizar si estamos progresando positivamente con estos valores de laboratorio.
Esto nos permitirá identificar a los pacientes que tienen dificultades para cumplir con sus objetivos de valores de laboratorio y, posiblemente, proporcionarles recursos para garantizar que reciban un tratamiento de diálisis adecuado (transporte, educación, etc.).
Métricas relevantes:
Fechas de trasplante renal (si aplica).
Primer nivel de calcio del paciente cada mes (Código de laboratorio: 49765-1).
Primer nivel de sodio del paciente cada mes (Código de laboratorio: 2947-0).
Primer nivel de albúmina del paciente cada mes (Código de laboratorio: 1751-7).
Primer nivel de BUN del paciente cada mes (Código de laboratorio: 6299-2).
Porcentaje de pacientes que cumplen con el objetivo para cada uno de los valores de laboratorio anteriores (no se cumple el objetivo si el resultado está fuera del rango objetivo o si no se realizó el análisis en ese mes):
Calcio: 50%, rango de 8.4 a 9.4.
Sodio: 75%, >=137.
Albúmina: 60%, >=4.
BUN: 80%, rango de 5 a 20.
Raza.
Edad.
Nombre completo del paciente e información geográfica.
Fecha de fallecimiento.
Criterios de inclusión:
Pacientes con diagnóstico ICD9: 585.6 (diagnóstico de ESRD).
ESRD debe haber sido una condición activa para los pacientes en algún momento de 2022.
El paciente debe haber estado activo y haber tenido al menos un encuentro en los años 2022 o 2021.
Meses en los que el paciente estaba vivo.
Criterios de exclusión:
Meses en los que el paciente recibió un trasplante renal (código de procedimiento: 55.69).
Granularidad:
Combinación de paciente y meses.
Sugerencias:
Construir una lista de 12 filas, cada una con meses truncados (1/1/2022, 2/1/2022, etc.) para unirla con tu lista de pacientes con ESRD y crear una combinación.
Sin embargo, no todos los pacientes tendrán ESRD durante exactamente 12 meses. Algunos solo tendrán ESRD por 3 meses, otros por un par de meses, mejorarán y luego volverán a tener la condición por otros meses. Para manejar esto, necesitarás una columna que rastree cuándo comenzó el ESRD para cada paciente y una fecha de finalización que indique el evento más temprano entre:
Fallecimiento.
Trasplante.
Fin del ESRD.
Si la fecha de finalización del ESRD es nula y el paciente no ha fallecido ni ha recibido un trasplante renal, necesitarás asignar un valor ficticio como 2099-01-01 para que la unión entre los periodos de actividad de ESRD y la lista de meses truncados creada en el paso 1 sea posible.
Configurar esta columna permitirá realizar una combinación donde los puntos de inicio y finalización del ESRD se vinculen con la lista de fechas truncadas para crear la combinación de paciente y meses.
Metodología:
Generación de datos: Synthea se utilizó para crear datos realistas que simulan valores de laboratorio para pacientes con ESRD.
Preprocesamiento: Los datos se limpiaron y estructuraron en PostgreSQL.
Consultas SQL: Se ejecutaron consultas avanzadas para calcular porcentajes de cumplimiento y tendencias temporales.
Creación del dashboard: Los resultados se cargaron en una herramienta de visualización para diseñar un tablero interactivo.
Resultados obtenidos: El dashboard facilita la identificación rápida de pacientes con valores fuera del rango objetivo, lo que puede servir para priorizar intervenciones clínicas. También permite analizar tendencias a lo largo del tiempo y evaluar el impacto de las medidas terapéuticas implementadas.
Aplicaciones futuras:
Integrar predicciones basadas en modelos de machine learning para anticipar resultados anómalos.
Ampliar el análisis a otras métricas de salud.
Contribuciones en GitHub:
Subiré el código SQL, el esquema de base de datos, y una captura del dashboard en formato interactivo a un repositorio público.
Enlace Tableau 
https://public.tableau.com/app/profile/meliza.perneth/viz/CapstoneESRDLab/Dashboard2


