# Inteligencia_Artificial_Ibero
El código simula un sistema inteligente de rutas mediante tres componentes fundamentales:

1. Base de Conocimiento (CONEXIONES)
La base de conocimiento está compuesta por Hechos (datos brutos) que describen la red de transporte. Cada conexión contiene: el destino, la Línea de transporte (necesaria para la lógica de transferencia) y el Tiempo estimado (necesario para la optimización).

2. Motor de Inferencia (regla_buscar_rutas)
Esta función actúa como el motor que aplica las reglas de movimiento sobre los hechos.

Utiliza el algoritmo de Búsqueda en Amplitud (BFS) para explorar sistemáticamente todas las rutas posibles.

Regla de Transferencia: La inteligencia del sistema reside en esta regla: if linea_nueva != linea_ant. Si el viajero debe cambiar de línea en una estación, el contador de transferencias se incrementa.

Regla de Poda: El límite de dos transferencias evita buscar rutas infinitas o excesivamente ineficientes, manteniendo el foco en soluciones prácticas.

3. Regla de Optimización (motor_principal)
Una vez que el motor de inferencia encuentra todas las rutas, se aplica la regla de optimización para determinar la "mejor" ruta:

Prioridad Máxima: La ruta con la menor cantidad de transferencias es siempre la preferida (es decir, la ruta más directa).

Desempate: Si hay varias rutas con el mismo mínimo de transferencias, se elige la que tenga el menor tiempo total.

El uso de la función min() con una clave de tupla logra esta jerarquía de reglas de decisión, resultando en la ruta más eficiente para el viajero.
