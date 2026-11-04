[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=l23212635-collab/MSFP3)

# Práctica 3 — Sistema Musculoesquelético

Repositorio académico de la asignatura **Modelado de Sistemas Fisiológicos**, correspondiente al programa de **Ingeniería Biomédica** del Tecnológico Nacional de México / Instituto Tecnológico de Tijuana. Esta práctica integra modelado matemático, analogías eléctricas de sistemas fisiológicos, análisis de la respuesta dinámica, diseño de controladores PID y simulación computacional.

El caso de estudio representa el **sistema musculoesquelético** mediante una analogía eléctrica de tipo **RC de primer orden**. Se busca describir y comparar la respuesta del sistema ante una fuerza aplicada, considerando las diferencias entre un individuo sano (control) y un caso patológico, tanto en lazo abierto como mediante un sistema de control PID.

**Docente:** Dr. Paul Antonio Valle Trujillo

**Correo:** paul.valle@tectijuana.edu.mx

**Departamento:** Ingeniería Eléctrica y Electrónica

**Institución:** Tecnológico Nacional de México / Instituto Tecnológico de Tijuana

**Asignatura:** Modelado de Sistemas Fisiológicos

**Programa:** Ingeniería Biomédica

**Estudiante:** Perez Garcia Diego

**Número de control:** 23212635

**Correo:** l23212635@tectijuana.edu.mx

**Sede:** Blvd. Alberto Limón Padilla s/n, Tijuana, C. P. 22454, B. C., México.

---

<a id="contenido"></a>

## Contenido

1. [Resumen](#resumen)
2. [Competencia y objetivos](#objetivos)
3. [Relación con el temario](#temario)
4. [Modelo físico y analogía eléctrica](#analogia)
5. [Formulación matemática](#modelo)
6. [Análisis temporal y de estabilidad](#analisis)
7. [Señales de entrada y condiciones de simulación](#senales)
8. [Implementación en MATLAB y Simulink](#matlab)
9. [Control en lazo cerrado y controlador PID](#pid)
10. [Reproducción en Python](#python)
11. [Resultados y comparación entre control y caso](#resultados)
12. [Flujo de trabajo](#flujo)
13. [Actividades del estudiante](#actividades)
14. [Estructura del repositorio](#estructura)
15. [Requisitos](#requisitos)
16. [Reproducibilidad y entregables](#reproducibilidad)
17. [Referencias](#referencias)

---

<a id="resumen"></a>

## Resumen

La práctica tiene como propósito desarrollar y analizar un modelo matemático del **sistema musculoesquelético**, utilizando una analogía eléctrica de tipo RC para representar su comportamiento dinámico. A través de esta aproximación se busca comprender cómo responde el sistema ante una fuerza aplicada y cómo las variaciones en sus parámetros pueden modificar su respuesta fisiológica.

El modelo considera una resistencia equivalente y una capacitancia, cuyos valores representan características asociadas con la oposición al movimiento y la capacidad de almacenamiento de energía en el tejido muscular. Mediante esta representación se obtiene un sistema de primer orden que permite estudiar la respuesta temporal y comparar las condiciones de un individuo sano con las de un caso patológico.

Posteriormente, se analiza el comportamiento del sistema mediante herramientas computacionales como **MATLAB, Simulink y Python**, considerando la respuesta en lazo abierto y la implementación de un controlador PID para mejorar el comportamiento dinámico del sistema.

La comparación entre el caso de control y el caso patológico permite identificar las diferencias en la respuesta del modelo y evaluar la utilidad de los sistemas de control aplicados a modelos fisiológicos.

**Palabras clave:** sistema musculoesquelético; contracción muscular; fuerza; analogía RC; función de transferencia; controlador PID; MATLAB; Simulink; Python; modelado de sistemas fisiológicos.

[Volver al contenido](#contenido)

---

<a id="objetivos"></a>

## Competencia y objetivos

### Competencia a desarrollar

Aplicar los principios del modelado matemático y de la Ingeniería de Control para representar el comportamiento dinámico del sistema musculoesquelético mediante una analogía eléctrica RC, identificando las diferencias entre un individuo sano y un caso patológico, así como evaluando la respuesta del sistema mediante simulaciones computacionales.

### Objetivo general

Desarrollar y analizar un modelo matemático del sistema musculoesquelético mediante una analogía eléctrica de primer orden, utilizando herramientas computacionales para estudiar su respuesta dinámica y comparar el comportamiento entre el individuo sano y el caso patológico, incorporando un controlador PID para mejorar la respuesta del sistema.

### Objetivos específicos

- Desarrollar el modelo matemático del sistema musculoesquelético.
- Identificar los elementos eléctricos equivalentes del modelo fisiológico.
- Obtener la función de transferencia del sistema.
- Analizar la respuesta dinámica del sistema ante una señal de entrada.
- Simular el comportamiento del sistema en lazo abierto.
- Diseñar e implementar un controlador PID.
- Comparar el comportamiento entre el individuo sano (control) y el caso patológico.
- Interpretar las diferencias observadas en las respuestas obtenidas mediante simulación.

[Volver al contenido](#contenido)

---

<a id="temario"></a>

## Relación con el temario

La práctica integra contenidos de la asignatura **Modelado de Sistemas Fisiológicos**, principalmente relacionados con el modelado matemático, los sistemas de control y la simulación computacional.

| Área | Contenidos aplicados |
|---|---|
| Modelado matemático | Representación matemática del sistema musculoesquelético y obtención de la función de transferencia |
| Analogías eléctricas | Representación del sistema fisiológico mediante un circuito RC |
| Sistemas de control | Análisis de la respuesta en lazo abierto y diseño de un controlador PID |
| Análisis dinámico | Estudio de la respuesta temporal y comparación de parámetros |
| Simulación computacional | Implementación del modelo en MATLAB, Simulink y Python |

El enfoque combina **Ingeniería de Control, Electrónica Analógica, Ciencias de la Computación y Fisiología**, con el propósito de comprender y representar cuantitativamente el comportamiento de un sistema fisiológico.

[Volver al contenido](#contenido)

---

<a id="analogia"></a>

## Modelo físico y analogía eléctrica

El sistema musculoesquelético puede representarse mediante una analogía eléctrica de tipo RC, en la cual los elementos del circuito permiten describir de manera simplificada el comportamiento dinámico asociado con la contracción muscular.

En esta representación, la resistencia modela la oposición al movimiento, mientras que el capacitor representa la capacidad de almacenamiento de energía relacionada con las propiedades elásticas del tejido muscular.

La señal de entrada corresponde a una fuerza aplicada \(F(t)\), que genera una respuesta dinámica en el sistema.

### Correspondencia fisiológica y eléctrica

| Símbolo | Equivalente eléctrico | Interpretación fisiológica |
|---|---|---|
| \(F(t)\) | Voltaje de entrada | Fuerza aplicada al sistema |
| \(R\) | Resistencia | Oposición al movimiento |
| \(C\) | Capacitancia | Capacidad de almacenamiento de energía del tejido muscular |
| \(y(t)\) | Voltaje de salida | Respuesta del sistema musculoesquelético |

### Comparación entre individuo sano y caso patológico

El modelo contempla dos condiciones de funcionamiento:

- **Control:** representa el comportamiento de referencia de un individuo sano.
- **Caso patológico:** representa una condición en la que existen alteraciones en las propiedades del sistema musculoesquelético.

La diferencia entre ambas condiciones se refleja principalmente en los parámetros del modelo, particularmente en la resistencia equivalente. Estas variaciones modifican la constante de tiempo y, por consiguiente, la velocidad de respuesta del sistema.

El caso patológico presenta una respuesta más lenta y amortiguada en comparación con el control.

[Volver al contenido](#contenido)

---

<a id="modelo"></a>

## Formulación matemática

### 1. Modelo matemático

El sistema musculoesquelético se representa mediante un modelo de primer orden basado en una analogía eléctrica RC.

La formulación matemática permite relacionar la señal de entrada con la respuesta de salida del sistema, considerando los parámetros eléctricos equivalentes.

La ecuación diferencial y la función de transferencia deben corresponder a la configuración específica del circuito RC utilizado en la práctica.

### 2. Función de transferencia

La función de transferencia representa la relación entre la salida y la entrada del sistema en el dominio de Laplace:

\[
G(s)=\frac{Y(s)}{F(s)}
\]

Para obtener la expresión particular del modelo se consideran las ecuaciones del circuito equivalente y las condiciones iniciales correspondientes.

### 3. Representación del sistema

El modelo se utiliza para analizar el comportamiento dinámico del sistema musculoesquelético y comparar las respuestas correspondientes al individuo sano y al caso patológico.

Los parámetros específicos y la expresión final de la función de transferencia deben documentarse de acuerdo con el desarrollo matemático realizado en la práctica.

[Volver al contenido](#contenido)

---

<a id="analisis"></a>

## Análisis temporal y de estabilidad

El análisis temporal permite estudiar la evolución de la respuesta del sistema musculoesquelético ante una señal de entrada.

Debido a que el modelo presenta un comportamiento de primer orden, su respuesta depende de los parámetros que conforman la analogía eléctrica RC.

### 1. Constante de tiempo

La constante de tiempo es un parámetro importante para describir la rapidez con la que responde el sistema ante una entrada.

En el modelo RC, su valor depende de la resistencia y la capacitancia equivalentes:

\[
\tau=RC
\]

Una variación en estos parámetros modifica la velocidad de respuesta del sistema.

### 2. Respuesta dinámica

La respuesta del sistema se analiza considerando las diferencias entre las dos condiciones estudiadas:

- Individuo sano (control).
- Caso patológico.

El comportamiento del sistema permite observar cómo las alteraciones en los parámetros modifican la respuesta temporal.

### 3. Estabilidad

La estabilidad del sistema se estudia mediante la función de transferencia y la ubicación de sus polos en el plano complejo.

Para un sistema de primer orden, el polo permite determinar las características de estabilidad y la rapidez de respuesta.

### 4. Comparación de respuestas

Se analizan las diferencias entre el comportamiento del control y el caso patológico, considerando:

- Rapidez de respuesta.
- Tiempo de establecimiento.
- Amplitud de la respuesta.
- Comportamiento transitorio.
- Efecto de los parámetros del modelo.

[Volver al contenido](#contenido)

---

<a id="senales"></a>

## Señales de entrada y condiciones de simulación

La simulación permite estudiar el comportamiento del sistema musculoesquelético mediante la aplicación de una señal de entrada que representa la fuerza aplicada.

La respuesta obtenida se analiza para las condiciones de control y caso patológico.

### Condiciones de simulación

| Parámetro | Descripción |
|---|---|
| Sistema | Musculoesquelético |
| Modelo | Analogía eléctrica RC |
| Orden | Primer orden |
| Entrada | Fuerza aplicada \(F(t)\) |
| Salida | Respuesta del sistema |
| Condiciones | Control y caso patológico |
| Herramientas | MATLAB, Simulink y Python |

Los valores numéricos de los parámetros, el intervalo de simulación y las características específicas de la señal de entrada se documentan de acuerdo con la configuración utilizada en los archivos computacionales de la práctica.

[Volver al contenido](#contenido)

---

<a id="matlab"></a>

## Implementación en MATLAB y Simulink

La implementación computacional permite representar el modelo matemático del sistema musculoesquelético y analizar su comportamiento mediante simulaciones.

Se utiliza MATLAB para realizar los cálculos matemáticos, obtener las respuestas del sistema y generar las gráficas correspondientes.

Por otra parte, Simulink permite construir una representación gráfica del modelo mediante bloques que describen las relaciones matemáticas del sistema.

### Implementación del modelo

Durante esta etapa se consideran las siguientes actividades:

1. Definición de los parámetros del modelo.
2. Construcción de la función de transferencia.
3. Implementación del sistema en Simulink.
4. Aplicación de la señal de entrada.
5. Obtención de la respuesta temporal.
6. Comparación entre el control y el caso patológico.

### Análisis de resultados

Las gráficas obtenidas permiten visualizar las diferencias entre ambas condiciones y estudiar cómo los parámetros del modelo afectan la respuesta dinámica.

[Volver al contenido](#contenido)

---

<a id="pid"></a>

## Control en lazo cerrado y controlador PID

El controlador PID se incorpora con la finalidad de mejorar la respuesta dinámica del sistema musculoesquelético y reducir las diferencias entre la respuesta deseada y la respuesta obtenida.

El controlador utiliza tres acciones principales:

| Acción | Descripción |
|---|---|
| Proporcional (P) | Actúa en función del error presente |
| Integral (I) | Considera la acumulación del error a lo largo del tiempo |
| Derivativa (D) | Considera la velocidad de cambio del error |

### 1. Señal de error

La señal de error se obtiene mediante la diferencia entre la referencia y la salida del sistema:

\[
e(t)=r(t)-y(t)
\]

Donde:

- \(r(t)\): señal de referencia.
- \(y(t)\): salida del sistema.
- \(e(t)\): señal de error.

### 2. Función del controlador PID

La expresión general del controlador PID es:

\[
u(t)=K_Pe(t)+K_I\int e(t)\,dt+K_D\frac{de(t)}{dt}
\]

Donde:

- \(K_P\): ganancia proporcional.
- \(K_I\): ganancia integral.
- \(K_D\): ganancia derivativa.

### 3. Evaluación del controlador

La implementación del controlador permite comparar el comportamiento del sistema antes y después de incorporar la acción de control.

Se busca observar si la respuesta controlada presenta una mejora en su comportamiento dinámico y si logra aproximarse a la respuesta de referencia.

[Volver al contenido](#contenido)

---

<a id="python"></a>

## Reproducción en Python

La implementación en Python permite reproducir el modelo matemático del sistema musculoesquelético mediante herramientas de programación científica.

El programa permite realizar cálculos, simular la respuesta del sistema y generar gráficas para comparar las condiciones de control y caso patológico.

### Procedimiento

1. Importación de las bibliotecas necesarias.
2. Definición de los parámetros del modelo.
3. Construcción de la señal de entrada.
4. Definición de la función de transferencia.
5. Simulación de la respuesta del sistema.
6. Comparación entre el control y el caso patológico.
7. Generación de las gráficas correspondientes.

La implementación en Python funciona como una herramienta complementaria para verificar los resultados obtenidos mediante MATLAB y Simulink.

[Volver al contenido](#contenido)

---

<a id="resultados"></a>

## Resultados y comparación entre control y caso

Los resultados de la práctica permiten analizar las diferencias en el comportamiento del sistema musculoesquelético bajo dos condiciones: individuo sano y caso patológico.

La comparación se realiza mediante las respuestas temporales obtenidas en las simulaciones.

### Aspectos para analizar

- Diferencias en la velocidad de respuesta.
- Variación de la constante de tiempo.
- Comportamiento transitorio.
- Diferencias entre la respuesta del control y el caso patológico.
- Efecto del controlador PID.
- Comparación entre los resultados obtenidos en MATLAB, Simulink y Python.

### Evidencia gráfica

En esta sección se incorporan las gráficas generadas durante la práctica para documentar el comportamiento del sistema.

| Resultado | Archivo |
|---|---|
| Comparación de respuestas del sistema | Gráficas de control vs. caso en PDF |
| Simulación computacional | Cuaderno de MATLAB |
| Modelo gráfico | Archivo de Simulink |
| Reproducción del modelo | Código de Python |

Las gráficas deben permitir identificar las diferencias entre ambas condiciones y explicar el efecto de los parámetros sobre la respuesta dinámica.

[Volver al contenido](#contenido)

---

<a id="flujo"></a>

## Flujo de trabajo

El desarrollo de la práctica sigue una secuencia que integra el modelado matemático, la simulación computacional y el análisis de resultados.

```mermaid
flowchart TD
    A[Identificación del sistema musculoesquelético] --> B[Analogía eléctrica RC]
    B --> C[Formulación matemática]
    C --> D[Obtención de la función de transferencia]
    D --> E[Análisis de la respuesta dinámica]
    E --> F[Simulación en MATLAB y Simulink]
    E --> G[Implementación en Python]
    F --> H[Comparación control vs. caso]
    G --> H
    H --> I[Diseño del controlador PID]
    I --> J[Simulación en lazo cerrado]
    J --> K[Análisis de resultados]
    K --> L[Documentación y evidencias en GitHub]ng subspace model identification", IEEE Transactions on Biomedical Engineering, vol. 57, no. 7, pp. 1531–1538, Jul 2010. https://doi.org/10.1109/TBME.2010.2041351

