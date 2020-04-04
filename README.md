# Coronavirus: El mundo inhala, aguanta y ¿cuándo exhala?

## Objetivo

Ayudar a estimar el pico de demanda hospitalaria en Argentina y su fecha estimada de ocurrencia, frente a la aplicación por calendario de medidas no farmacéuticas.

## Resumen de resultados



## Escenarios propuestos

1. Medidas de aislamiento intensivas de corto plazo y extensión de medidas de limitación en las fronteras  
2. Medidas de aislamiento intensivas de mediano plazo y vuelta a la normalidad gradualmente
3. Medidas de aislamiento moderadas de largo plazo 

## Conclusiones

Resumen de este estudio: 

## Desarrollo de la simulación

### 1. Contexto

*En cuestión de semanas, el mundo entero se vio desacelerado por la presencia de un nuevo virus que se extiende a un ritmo muy rápido a través del contagio por simples estornudos, el COVID-19. Muchas economías están frenadas, las personas aisladas y todos los gobernantes preguntándose: **qué es lo que hay que hacer, de qué forma y cuándo para generar el menor impacto posible**.*

De ahí la primera pregunta: *¿A qué nos referimos cuando hablamos de impacto?* El impacto directo claramente es la salud de las personas que habitan cada país que los gobernantes dirigen. Pero a eso subsiguen otras consecuencias: la saturación del sistema de salud del país que necesita estar disponible para otras necesidades, las consecuencias económicas que surgen de tener países enteros sin producir, sin transportar, importar o exportar durante tiempos extendidos y, finalmente, los efectos en la microeconomía de las familias que tienen que hacer frente a una situación de emergencia.

En el modelo que se plantea en este análisis se busca visualizar y estimar el impacto en las salud de las personas en lo correspondiente al COVID y el grado de saturación del sistema hospitalario dado el dimensionamiento existente hoy. El resto de las preguntas deberán considerarse por fuera, en un análisis abarcativo como un costo que viene asociado a la estrategia utilizada en cada simulación.

La segunda pregunta es hasta cuándo hay que tomar cada una de las medidas posibles y cómo es el efecto conjunto que tiene la aplicación de varias de ellas en simultáneo. *¿Qué pasa si exhalamos muy rápido y volvemos al punto de inicio?*

#### Argentina

El primer caso confirmado de COVID19 en el país fue el 3 de Marzo en Buenos Aires. El paciente, de 43 años, había llegado al país el 1 de Marzo desde Italia.

En ese momento, otros países en el mundo ya experimentaban evoluciones mucho más desarrolladas: China informaba



### 2. Modelo Conceptual

Para este análisis se desarrolló un **Modelo Basado en Agentes** para poder entender y mostrar cómo las conductas individuales (en este caso de las regiones y las personas) en un entorno conectado y definido (el país y sus fronteras) afectan a la evolución del sistema completo, a su vez limitada o guiada por las distintas medidas que se pueden tomar a nivel macro (políticas desde el Estado).

En esta modelización existen dos tipos de agentes: las personas y las regiones. Las regiones, en principio, funcionan a modo informativo para obtener estadísticas de la simulación, pero las personas tienen una estructura de comportamiento específica y definida. 

En este tipo de modelos, los agentes tienen distintos *estados* en los que pueden estar en cada unidad de tiempo. Para pasar de un estado a otro existen *transiciones* y una probabilidad asociada a cada una de ellas que se evalúa en cada unidad de tiempo.

Las personas tienen dos tipos de diagramas de estados que queremos diferenciar:
1. El estado ante la infección
2. El estado ante la detección de la misma en el sistema de salud

#### El estado ante la infección

> ![Diagrama de Estados de infección](/images/enfermedad.png)
>
> Un agente, es decir una persona en este caso, por defecto se encuentra sana. En el caso de contagio del virus, va a pasar a ser una 
persona ***infectada*** e ingresar en el diagrama de estado ante la infección.
> Con una determinada probabilidad se define si se trata 
> - de una persona que será asintomática o 
> - una persona que comenzará su periodo de incubación.
>
> El tipo de persona que es ***asintomática***, estará un tiempo infectada, sin haberse dado cuenta de estar infectada, a menos que se le realice un test aleatorio. 
>
> El tipo de persona que empieza el periodo de ***incubación*** transcurre un tiempo, que sigue una determinada distribución asociada a la enfermedad, hasta sentir el primer síntoma, momento en el que pasara al estado de ***síntomatico***. Cuando esto ocurra, se tratará de síntomas de gravedad ***leve***. Con determinada probabilidad asociada a su rango etario, podrá empeorar en gravedad de ahí en adelante. Los siguientes estados asociados a la gravedad son ***moderado*** y ***grave***. 
>
> * En todos los estados pertenecientes al diagrama de infección, un agente se encuentra contagiando con el ratio asoaciado a la enfermedad. 
> * Desde todos los estados del diagrama de infección se evalúa un tiempo para pasar al estado ***curado*** que sigue una determinada distribución relacionada a la enfermedad.
> * En caso de no haberse cumplido el tiempo de curación, solamente desde los estados moderado y grave podrá pasar un agente a estar en estado ***fallecido*** con una probabilidad asociada al rango etario.

#### El estado de detección de la enfermedad ante el sistema de salud

> ![Diagrama de Estados enfermedad](/images/detección.png)
>
> blablabla

Las transiciones entre los estados están definidas por probabilidades. Dichas probabilidades son características propias de la enfermedad y de la población en la que se está distribuyendo, que tienen valores "libres" pero sus valores "efectivos" pueden verse limitados por políticas externas al diagrama de estados, como una medida de cuarentena que disminuye la tasa de contacto de una población.

### 3. KPIs

- Infectados
- Fallecimientos
- Saturación de hospitales

### 4. Variables de Decisión

### 5. Lógicas de la simulación

## Validación

## Data

## Fuentes
