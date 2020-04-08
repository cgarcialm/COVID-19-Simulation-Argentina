# Coronavirus: Análisis de medidas no farmacéuticas

# =======================================
# Resumen de resultados

## Objetivo

Ayudar a estimar el pico de demanda hospitalaria en Argentina frente a la aplicación por calendario de medidas no farmacéuticas: su fecha estimada de ocurrencia y la saturación que generará en el sistema de salud.

## Conclusiones

1. Las **medidas** que se están tomando para la contención del virus hasta ahora parecen ser las **correctas y debieran mantenerse por al menos X días** para evitar fallecimientos por la saturación del sistema hospitalario.

2. **La saturación del sistema hospitalario difiere mucho entre Buenos Aires y el interior del país ya que la capacidad mismo en el interior es X veces más baja por habitante en el interior.** La diferencia en densidad poblacional y en población en sí, genera menos cantidad de infectados pero genera que no se pueda brindar asistencia a todos los pacientes, si no se toman medidas más intensivas y a más largo plazo.

3. 

## Escenarios propuestos y resumen de resultados

### Optimista: Medidas de aislamiento intensivas de corto plazo y extensión sólo de medidas de limitación en las fronteras  

blablabla + gráficos resultado Power BI

### Intermedio: Medidas de aislamiento intensivas de mediano plazo y vuelta a la normalidad gradualmente

blablabla + gráficos resultado Power BI

### Pesimista: Medidas de aislamiento moderadas de largo plazo 

blablabla + gráficos resultado Power BI

# =======================================
# Desarrollo de la simulación

### 1. Contexto

*En cuestión de semanas, el mundo entero se vio desacelerado por la presencia de un nuevo virus que se extiende a un ritmo muy rápido a través del contagio por simples estornudos, el COVID-19. Muchas economías están frenadas, las personas aisladas y todos los gobernantes preguntándose: **qué es lo que hay que hacer, de qué forma y cuándo para generar el menor impacto posible**.*

De ahí la primera pregunta: *¿A qué nos referimos cuando hablamos de impacto?* El impacto directo claramente es la salud de las personas que habitan cada país que los gobernantes dirigen. Pero a eso subsiguen otras consecuencias: la saturación del sistema de salud del país que necesita estar disponible para otras necesidades, las consecuencias económicas que surgen de tener países enteros sin producir, sin transportar, importar o exportar durante tiempos extendidos y, finalmente, los efectos en la microeconomía de las familias que tienen que hacer frente a una situación de emergencia.

En el modelo que se plantea en este análisis se busca visualizar y estimar el impacto en las salud de las personas en lo correspondiente al COVID y el grado de saturación del sistema hospitalario dado el dimensionamiento existente hoy. El resto de las preguntas deberán considerarse por fuera, en un análisis abarcativo como un costo que viene asociado a la estrategia utilizada en cada simulación.

La segunda pregunta es hasta cuándo hay que tomar cada una de las medidas posibles. *¿Qué pasa si liberamos al sistema muy rápido y estamos de nuevo en el punto de partida?* Para responder esto, hay que entender la evolución del sistema afectado por varias medidas aplicadas probablemente en simulatáneo.

#### Argentina

El primer caso confirmado de COVID19 en el país fue el 3 de Marzo en Buenos Aires. El paciente, de 43 años, había llegado al país el 1 de Marzo desde Italia.

En ese momento, otros países en el mundo ya experimentaban evoluciones mucho más desarrolladas: China informaba

![Serie de tiempo Italia](/images/timeseries_Italy.png)

![Serie de tiempo Francia](/images/timeseries_France.png)

![Serie de tiempo Spain](/images/timeseries_Spain.png)

![Serie de tiempo China](/images/timeseries_China.png)

#### Series de tiempo de medidas en Europa y USA

Agregar series de tiempo

### 2. KPIs

Indicadores resultantes de la simulación de X días, calculados a nivel total y a nivel región.

- **Re**: Ratio de reproducción efectivo. Ratio de reproducción básico de la enfermedad afectado por medidas gubernamentales.

- **Infectados**: Cantidad de infectados.

- **Fallecimientos**: Cantidad de fallecimientos.

- **Saturación de hospitales**: Proporción utilizada de las instalaciones y equipamiento de salud disponible.

### 3. Montecarlo

### 4. Modelo Conceptual

Para este análisis se desarrolló un [**Modelo Basado en Agentes en el software de simulación Anylogic**](https://www.anylogic.com/use-of-simulation/agent-based-modeling/) para poder entender y mostrar cómo las conductas individuales (en este caso de las regiones y las personas) en un entorno conectado y definido (el país y sus fronteras) afectan a la evolución del sistema completo, a su vez limitada o guiada por las distintas medidas que se pueden tomar a nivel macro (políticas desde el Estado).

En este tipo de modelos, los agentes tienen distintos *estados* en los que pueden estar en cada unidad de tiempo. Para pasar de un estado a otro existen *transiciones* y una probabilidad asociada a cada una de ellas que se evalúa en cada unidad de tiempo.

En esta modelización existen dos tipos de agentes:  
- ***Las Regiones*** interactúan entre sí a través de los movimientos migratorios internos y con el exterior del sistema a através de los movimientos migratorios externos. Además, contienen a los agentes Personas que son afectados por características de la región como la densidad y las políticas aplicadas en la misma que influyen en la tasa de contacto entre ellos.
- ***Las Personas*** transicionan entre estados que describen su situación ante la enfermedad y la interacción con las demás personas de la región a la que pertenecen. 

#### Las Regiones

#### Las Personas 

Las personas tienen dos tipos de diagramas de estados que queremos diferenciar:

1. El estado ante la infección

2. El estado ante sistema de salud

Estos flujos de estados interactúan entre sí porque de por sí, no se va a internar a una persona sana, pero van en paralelo ya que las limitaciones del sistema de salud, como su capacidad o la disponibilidad de cierto tipo de camas puede hacer que los pacientes no reciban el nivel de asistencia necesaria.

##### El estado ante la infección

> ![Diagrama de Estados de Infección](/images/enfermedad.png)
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

##### El estado de detección de la enfermedad ante el sistema de salud

> ![Diagrama de Estados ante el Sistema de Salud](/images/detección.png)
>
> 

### Transiciones

Las transiciones entre los estados están definidas por probabilidades. Dichas probabilidades son características propias de la enfermedad y de la población en la que se está distribuyendo, que tienen valores "libres" pero sus valores "efectivos" pueden verse limitados por políticas externas al diagrama de estados, como por ejemplo una medida de cuarentena que disminuye la tasa de contacto de una población. Su valores efectivos variarán por Región ya que se puede aplicar distintas políticas para cada una.

### 5. Variables de Decisión

### 6. Lógicas de la simulación

## Validación

## Data

## Fuentes
