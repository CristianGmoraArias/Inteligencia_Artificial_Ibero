Explicación de los Modelos de Aprendizaje Automático Aplicados al Transporte Masivo
Se desarrollaron dos modelos de Machine Learning sobre un dataset sintético de demanda horaria para ilustrar las diferencias entre el aprendizaje supervisado y el no supervisado en el contexto de la planificación de transporte.

1. Modelo de Aprendizaje Supervisado: Predicción de Demanda (Random Forest)
Este enfoque se utiliza cuando se tiene una etiqueta histórica que se desea predecir.

A. Objetivo
Predecir la Demanda de Pasajeros (valor numérico) en una estación dada la hora, el día de la semana y las condiciones climáticas.

B. Componentes Clave
Etiqueta (y): Demanda_Pasajeros. Este es el valor objetivo que el modelo intenta aprender a calcular.

Características (X): Hora, Dia_Semana, Clima_Lluvia, Temperatura_C. Estas son las variables de entrada que el modelo utiliza como evidencia.

Modelo (Random Forest Regressor): Se utiliza un algoritmo de regresión robusto. El Random Forest funciona construyendo múltiples árboles de decisión y promediando sus resultados, lo que lo hace muy preciso para predecir valores numéricos y útil para determinar la importancia de las características.

Flujo del Aprendizaje:

División de Datos: El dataset se separa en conjuntos de Entrenamiento (para que el modelo aprenda la relación entre X y Y) y Prueba (para evaluar su desempeño en datos nunca vistos).

Entrenamiento: El modelo ajusta sus parámetros basándose en los datos de entrenamiento.

Evaluación: Se mide el rendimiento utilizando métricas como el Error Cuadrático Medio (MSE) y el Coeficiente de Determinación (R 
2
 ). Un R 
2
  cercano a 1 indica que el modelo explica bien la variabilidad de la demanda.

C. Aplicación
Permite a los operadores de transporte anticipar cuántos pasajeros llegarán en un momento específico, facilitando la asignación óptima de recursos (trenes o buses) y previniendo el hacinamiento.

2. Modelo de Aprendizaje No Supervisado: Segmentación de Patrones (K-Means)
Este enfoque se utiliza para descubrir estructuras y agrupar datos que no tienen una etiqueta predefinida.

A. Objetivo
Segmentar o agrupar las diferentes horas/días de operación en clústeres (grupos) que comparten patrones de uso similares, sin saber de antemano cuántos grupos existen.

B. Componentes Clave
Datos de Entrada: Se utilizan todas las variables (Hora, Dia_Semana, Temperatura, incluyendo la Demanda_Pasajeros), pero no hay una etiqueta de salida que el modelo deba predecir.

Preprocesamiento (Estandarización): Se aplica el StandardScaler para asegurar que todas las características (como la Hora y la Temperatura) tengan la misma escala. Esto es crucial en K-Means para que ninguna variable domine el proceso de agrupación debido a su rango de valores superior.

Modelo (K-Means): Un algoritmo de clustering que agrupa puntos de datos al minimizar la distancia entre los puntos dentro de cada clúster. El modelo encuentra los centroides (puntos medios) que mejor representan a cada grupo.

Determinación de K (Método del Codo): Se utiliza el Método del Codo para estimar el número ideal de clústeres (K). Se busca el punto de inflexión en el gráfico de la Suma de Errores Cuadráticos (SSE), donde agregar más clústeres no genera una mejora significativa.

C. Aplicación
Permite una planificación estratégica y dinámica. En lugar de tratar cada hora individualmente, el operador puede identificar los perfiles operacionales (e.g., "Pico Laboral Fuerte", "Valle Matutino", "Fin de Semana de Baja Demanda") y aplicar estrategias específicas (horarios, tarifas, personal) a cada clúster.