[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=l23212635-collab/MSFP3)

# Práctica 3: Sistema Musculoesquelético

## Información del estudiante

**Nombre:** Perez Garcia Diego [23212635]  
**Correo electrónico:** l23212635@tectijuana.edu.mx  
**Carrera:** Ingeniería Biomédica  
**Asignatura:** Modelado de Sistemas Fisiológicos  

## Información del docente

**Docente:** Dr. Paul Antonio Valle Trujillo  
**Correo electrónico:** paul.valle@tectijuana.edu.mx  

**Departamento de Ingeniería Eléctrica y Electrónica**  
Tecnológico Nacional de México, Instituto Tecnológico de Tijuana.  
Blvd. Alberto Limón Padilla s/n, Tijuana, C.P. 22454, B.C., México.

---

<a id="contenido"></a>

## Contenido

1. [Introducción](#1-introducción)
2. [Competencia y objetivos](#2-competencia-y-objetivos)
3. [Relación con el temario de la asignatura](#3-relación-con-el-temario-de-la-asignatura)
4. [Descripción del sistema fisiológico](#4-descripción-del-sistema-fisiológico)
5. [Modelo matemático](#5-modelo-matemático)
6. [Análisis de la respuesta temporal y estabilidad](#6-análisis-de-la-respuesta-temporal-y-estabilidad)
7. [Señales de entrada y condiciones de simulación](#7-señales-de-entrada-y-condiciones-de-simulación)
8. [Implementación en MATLAB](#8-implementación-en-matlab)
9. [Modelado en Simulink](#9-modelado-en-simulink)
10. [Diseño del controlador PID](#10-diseño-del-controlador-pid)
11. [Implementación en Python](#11-implementación-en-python)
12. [Resultados y comparación](#12-resultados-y-comparación)
13. [Flujo de trabajo](#13-flujo-de-trabajo)
14. [Actividades desarrolladas](#14-actividades-desarrolladas)
15. [Estructura del repositorio](#15-estructura-del-repositorio)
16. [Requisitos de ejecución](#16-requisitos-de-ejecución)
17. [Reproducibilidad y entregables](#17-reproducibilidad-y-entregables)
18. [Conclusiones](#18-conclusiones)
19. [Referencias bibliográficas](#19-referencias-bibliográficas)

---

## 1. Introducción

El modelado de sistemas fisiológicos permite representar matemáticamente el comportamiento de los diferentes sistemas que conforman el cuerpo humano. Mediante modelos matemáticos y herramientas computacionales es posible estudiar la respuesta dinámica de un sistema biológico ante diferentes estímulos, así como analizar las variaciones que se presentan bajo distintas condiciones fisiológicas o patológicas.

En esta práctica se estudia el **sistema musculoesquelético**, específicamente mediante una representación basada en analogías eléctricas. Se emplean elementos resistivos y capacitivos para representar determinadas propiedades del comportamiento muscular, permitiendo construir un modelo matemático que describe su respuesta ante una fuerza de entrada.

A partir del modelo obtenido se analiza el comportamiento dinámico del sistema, se obtiene su función de transferencia y se realizan simulaciones computacionales en MATLAB, Simulink y Python.

Además, se compara la respuesta de un individuo en condiciones normales (control) con un caso patológico, con el propósito de identificar las diferencias en su comportamiento y estudiar la aplicación de un controlador PID para modificar la respuesta del sistema.

[⬆️ Volver al contenido](#contenido)

---

## 2. Competencia y objetivos

### Competencia

Desarrollar modelos matemáticos de sistemas fisiológicos mediante analogías eléctricas, aplicando herramientas de análisis y control de sistemas para estudiar su comportamiento dinámico y realizar simulaciones computacionales.

### Objetivo general

Modelar y analizar el comportamiento dinámico del sistema musculoesquelético mediante una analogía eléctrica, comparando la respuesta de un sistema en condiciones normales con un caso patológico y evaluando la aplicación de un controlador PID.

### Objetivos específicos

1. Desarrollar un modelo matemático que represente el comportamiento del sistema musculoesquelético.
2. Obtener la función de transferencia del sistema a partir de su representación eléctrica.
3. Analizar la respuesta dinámica ante una señal de entrada.
4. Simular el comportamiento del sistema en lazo abierto.
5. Diseñar e implementar un controlador PID.
6. Comparar la respuesta de un individuo en condiciones normales (control) con un caso patológico.
7. Interpretar las diferencias entre ambas respuestas y evaluar el efecto del controlador sobre el comportamiento del sistema.

[⬆️ Volver al contenido](#contenido)

---

## 3. Relación con el temario de la asignatura

La práctica se relaciona con los temas de modelado matemático, análisis de sistemas dinámicos y teoría clásica de control.

Los conocimientos aplicados incluyen:

- Modelado matemático de sistemas fisiológicos.
- Analogías entre circuitos eléctricos y sistemas biológicos.
- Obtención de funciones de transferencia.
- Análisis de sistemas de primer orden.
- Respuesta temporal de sistemas dinámicos.
- Estabilidad y comportamiento de sistemas.
- Simulación computacional.
- Diseño e implementación de controladores PID.
- Comparación entre condiciones fisiológicas normales y patológicas.

Estos conceptos permiten estudiar el comportamiento de un sistema fisiológico mediante herramientas matemáticas y computacionales.

[⬆️ Volver al contenido](#contenido)

---

## 4. Descripción del sistema fisiológico

El sistema musculoesquelético está relacionado con la generación de movimiento, el mantenimiento de la postura y la producción de fuerza mediante la interacción entre músculos, huesos, articulaciones y estructuras asociadas.

En esta práctica se utiliza una representación simplificada del comportamiento muscular mediante una analogía con un circuito eléctrico RC.

La analogía permite representar determinadas propiedades del sistema mediante componentes eléctricos:

| Elemento eléctrico | Representación en el modelo |
|---|---|
| Resistencia (R) | Oposición al movimiento o a la respuesta muscular |
| Capacitor (C) | Almacenamiento de energía asociado al comportamiento del tejido muscular |
| Señal de entrada | Fuerza aplicada al sistema, F(t) |
| Respuesta del sistema | Comportamiento dinámico asociado a la contracción muscular |

La fuerza aplicada representa la entrada del sistema, mientras que la respuesta obtenida permite estudiar cómo cambia el comportamiento muscular a lo largo del tiempo.

### 4.1 Condición normal y condición patológica

Se consideran dos condiciones para realizar el análisis:

**Caso control:**

Representa el comportamiento del sistema en condiciones normales. Se utiliza como referencia para estudiar la respuesta dinámica del modelo.

**Caso patológico:**

Representa una condición en la que se modifica el comportamiento del sistema mediante cambios en sus parámetros. Principalmente, se considera una variación en la resistencia, lo que modifica la constante de tiempo y la velocidad de respuesta.

La comparación permite observar cómo las modificaciones de los parámetros afectan el comportamiento dinámico del sistema.

[⬆️ Volver al contenido](#contenido)

---

## 5. Modelo matemático

Para estudiar el sistema musculoesquelético se utiliza una analogía eléctrica RC, mediante la cual se representa el comportamiento dinámico del modelo fisiológico.

El análisis matemático permite establecer la relación entre la señal de entrada y la respuesta del sistema.

### 5.1 Variables del modelo

Las principales variables consideradas son:

| Variable | Descripción |
|---|---|
| F(t) | Fuerza de entrada aplicada al sistema |
| R | Resistencia del modelo |
| C | Capacitancia del modelo |
| t | Tiempo |
| Respuesta | Salida dinámica del sistema |

### 5.2 Representación mediante circuito RC

El circuito RC permite representar el comportamiento del sistema utilizando elementos resistivos y capacitivos.

La resistencia representa la oposición al movimiento, mientras que el capacitor representa la capacidad de almacenamiento de energía del modelo.

A partir de las relaciones eléctricas entre sus componentes se establece una ecuación diferencial que permite describir la evolución temporal de la respuesta.

### 5.3 Función de transferencia

La función de transferencia permite representar matemáticamente la relación entre la entrada y la salida del sistema en el dominio de Laplace.

De manera general, se expresa como:

\[
G(s)=\frac{Y(s)}{U(s)}
\]

Donde:

- \(G(s)\): función de transferencia.
- \(Y(s)\): salida del sistema.
- \(U(s)\): entrada del sistema.
- \(s\): variable compleja del dominio de Laplace.

La función de transferencia específica se obtiene a partir de la ecuación diferencial y de los parámetros del circuito utilizado en la práctica.

### 5.4 Constante de tiempo

La constante de tiempo es un parámetro importante para analizar la velocidad de respuesta del sistema.

En un modelo RC de primer orden se relaciona con la resistencia y la capacitancia mediante:

\[
\tau=RC
\]

Donde:

- \(\tau\): constante de tiempo.
- \(R\): resistencia.
- \(C\): capacitancia.

Una modificación de la resistencia o de la capacitancia produce cambios en la constante de tiempo y, por lo tanto, en la respuesta dinámica.

En esta práctica, la comparación entre el caso control y el caso patológico permite estudiar cómo los cambios en los parámetros modifican la velocidad de respuesta del modelo.

[⬆️ Volver al contenido](#contenido)

---

## 6. Análisis de la respuesta temporal y estabilidad

El análisis temporal permite observar cómo responde el sistema ante una señal de entrada y cómo evoluciona su salida a través del tiempo.

Se estudian principalmente los siguientes aspectos:

- Tiempo de respuesta.
- Velocidad de respuesta.
- Comportamiento transitorio.
- Comportamiento en estado estable.
- Diferencias entre el caso control y el patológico.

### 6.1 Respuesta del caso control

La respuesta del caso control representa el comportamiento de referencia del sistema bajo condiciones normales.

Se utiliza para establecer una comparación con el comportamiento del caso patológico.

### 6.2 Respuesta del caso patológico

En el caso patológico se modifican los parámetros del modelo, principalmente la resistencia.

Esta modificación altera la constante de tiempo y puede provocar una respuesta más lenta y amortiguada en comparación con el caso control.

### 6.3 Comparación de respuestas

La comparación de ambas respuestas permite identificar las diferencias en el comportamiento dinámico del sistema.

Se busca observar cómo los cambios en los parámetros afectan la evolución de la salida y cómo estas variaciones pueden representar condiciones fisiológicas diferentes.

[⬆️ Volver al contenido](#contenido)

---

## 7. Señales de entrada y condiciones de simulación

Para estudiar el comportamiento del modelo se aplica una señal de entrada que representa la fuerza ejercida sobre el sistema musculoesquelético.

La señal de entrada permite observar la respuesta temporal y comparar el comportamiento de los dos escenarios.

Las simulaciones se realizan utilizando herramientas computacionales, considerando los parámetros establecidos para cada condición.

**Elementos considerados en la simulación:**

- Señal de entrada de fuerza.
- Parámetros del modelo RC.
- Condición control.
- Condición patológica.
- Tiempo de simulación.
- Respuesta del sistema.

Los valores numéricos específicos deben corresponder a los parámetros implementados en los archivos de MATLAB, Simulink y Python del repositorio.

[⬆️ Volver al contenido](#contenido)

---

## 8. Implementación en MATLAB

MATLAB se utiliza como herramienta principal para realizar los cálculos matemáticos, analizar el comportamiento del sistema y generar las gráficas correspondientes.

Mediante el código desarrollado se pueden establecer los parámetros del modelo, definir la señal de entrada y calcular la respuesta temporal.

Las actividades realizadas incluyen:

1. Definición de los parámetros del sistema.
2. Construcción del modelo matemático.
3. Obtención de la función de transferencia.
4. Definición de la señal de entrada.
5. Simulación de la respuesta temporal.
6. Comparación entre el caso control y el patológico.
7. Generación de gráficas para interpretar los resultados.

[⬆️ Volver al contenido](#contenido)

---

## 9. Modelado en Simulink

Simulink permite representar gráficamente el modelo matemático mediante bloques que representan operaciones y componentes del sistema.

La implementación facilita observar las conexiones entre las variables y estudiar la respuesta del modelo ante diferentes señales de entrada.

### 9.1 Modelo en lazo abierto

Se implementa el modelo del sistema sin utilizar un controlador, con el objetivo de observar su comportamiento natural ante la señal de entrada.

### 9.2 Modelo con controlador PID

Posteriormente, se incorpora un controlador PID para modificar la respuesta del sistema.

El controlador permite ajustar el comportamiento dinámico mediante la acción proporcional, integral y derivativa.

La finalidad es evaluar si la respuesta del sistema puede aproximarse a la respuesta de referencia del caso control.

[⬆️ Volver al contenido](#contenido)

---

## 10. Diseño del controlador PID

El controlador PID es una estrategia de control clásico que combina tres acciones: proporcional, integral y derivativa.

Su expresión general es:

\[
u(t)=K_p e(t)+K_i\int e(t)\,dt+K_d\frac{de(t)}{dt}
\]

Donde:

- \(u(t)\): señal de control.
- \(e(t)\): error entre la referencia y la salida.
- \(K_p\): ganancia proporcional.
- \(K_i\): ganancia integral.
- \(K_d\): ganancia derivativa.

### 10.1 Acción proporcional

La acción proporcional genera una señal de control proporcional al error existente entre la referencia y la salida del sistema.

### 10.2 Acción integral

La acción integral considera la acumulación del error a lo largo del tiempo, permitiendo reducir el error en estado estable.

### 10.3 Acción derivativa

La acción derivativa responde a la velocidad de cambio del error, contribuyendo a modificar el comportamiento transitorio del sistema.

### 10.4 Aplicación al sistema musculoesquelético

El controlador PID se incorpora para evaluar la posibilidad de compensar las diferencias entre el comportamiento del caso patológico y el caso control.

Se analiza la respuesta obtenida después de implementar el controlador y se compara con el comportamiento original del sistema.

[⬆️ Volver al contenido](#contenido)

---

## 11. Implementación en Python

Python se utiliza como herramienta complementaria para realizar simulaciones y representar gráficamente el comportamiento del sistema.

Mediante bibliotecas de cálculo científico es posible implementar el modelo matemático y analizar su respuesta temporal.

Las principales bibliotecas utilizadas son:

| Biblioteca | Función |
|---|---|
| NumPy | Operaciones numéricas y manejo de arreglos |
| Matplotlib | Generación de gráficas |
| SciPy | Herramientas para análisis y simulación de sistemas |
| Control | Modelado y análisis de sistemas de control |

La implementación permite comparar los resultados obtenidos mediante Python con los resultados de MATLAB y Simulink.

[⬆️ Volver al contenido](#contenido)

---

## 12. Resultados y comparación

Los resultados de la práctica permiten estudiar el comportamiento del sistema musculoesquelético mediante la representación eléctrica propuesta.

Se comparan las respuestas del caso control y del caso patológico para identificar los efectos de las modificaciones de los parámetros.

### 12.1 Comparación entre control y caso patológico

La comparación se realiza considerando:

- La velocidad de respuesta.
- La evolución temporal de la salida.
- Las diferencias en el comportamiento transitorio.
- El efecto de los parámetros del modelo.
- La respuesta obtenida después de aplicar el controlador PID.

### 12.2 Interpretación de resultados

El análisis permite observar que las modificaciones en la resistencia del modelo afectan directamente la constante de tiempo y, por consiguiente, la velocidad de respuesta.

En el caso patológico se presenta una respuesta más lenta y amortiguada en comparación con el caso control.

La implementación del controlador PID permite estudiar la posibilidad de compensar estas diferencias y obtener una respuesta más cercana a la condición de referencia.

### 12.3 Evidencia gráfica

En el repositorio se incluyen las gráficas generadas durante las simulaciones, en las cuales se presenta la comparación entre el caso control y el caso patológico.

Estas representaciones permiten visualizar las diferencias en el comportamiento dinámico y evaluar los efectos de la estrategia de control implementada.

[⬆️ Volver al contenido](#contenido)

---

## 13. Flujo de trabajo

El desarrollo de la práctica sigue una secuencia de actividades que permite pasar desde la descripción del sistema fisiológico hasta la simulación y análisis de resultados.

### 13.1 Diagrama general del procedimiento

El procedimiento desarrollado durante la práctica se representa mediante la siguiente secuencia de actividades:

```text
Descripción del sistema musculoesquelético
                  |
                  v
         Analogía eléctrica RC
                  |
                  v
       Desarrollo del modelo matemático
                  |
                  v
    Obtención de la función de transferencia
                  |
                  v
 Definición de parámetros y señal de entrada
                  |
                  v
          Simulación en MATLAB
                  |
                  v
       Implementación en Simulink
                  |
                  v
 Análisis del caso control y patológico
                  |
                  v
       Diseño del controlador PID
                  |
                  v
          Simulación en Python
                  |
                  v
       Comparación de resultados
                  |
                  v
       Interpretación y conclusiones
```

### 13.2 Procedimiento

1. Identificar las características principales del sistema musculoesquelético.
2. Establecer la analogía eléctrica utilizada para representar el comportamiento muscular.
3. Formular el modelo matemático.
4. Obtener la función de transferencia.
5. Definir los parámetros correspondientes a cada condición.
6. Implementar el modelo en MATLAB.
7. Construir el modelo de bloques en Simulink.
8. Realizar las simulaciones en lazo abierto.
9. Comparar el comportamiento del caso control y el patológico.
10. Incorporar el controlador PID.
11. Evaluar los resultados obtenidos.
12. Documentar las gráficas y conclusiones.

[⬆️ Volver al contenido](#contenido)

---

## 14. Actividades desarrolladas

Durante el desarrollo de la práctica se consideran las siguientes actividades:

- [x] Descripción del sistema musculoesquelético.
- [x] Establecimiento de una analogía eléctrica.
- [x] Desarrollo del modelo matemático.
- [x] Análisis de la función de transferencia.
- [x] Simulación computacional del sistema.
- [x] Comparación entre el caso control y el patológico.
- [x] Implementación del modelo en herramientas de simulación.
- [x] Diseño y análisis del controlador PID.
- [x] Generación de gráficas y evidencia de resultados.
- [x] Elaboración de la documentación de la práctica.

[⬆️ Volver al contenido](#contenido)

---

## 15. Estructura del repositorio

El repositorio contiene los archivos necesarios para consultar, ejecutar y analizar el desarrollo de la práctica.

La estructura general se organiza de la siguiente manera:

```text
MSFP3/
│
├── README.md
│
├── MATLAB/
│   └── Practica3.mlx
│
├── Simulink/
│   └── Sistema_Musculoesqueletico.slx
│
├── Python/
│   └── Practica3.py
│
├── Resultados/
│   ├── Control_vs_Caso.pdf
│   └── Graficas/
│
├── Evidencias/
│   ├── Analisis_Matematico/
│   └── Modelo_Fisiologico/
│
└── Referencias/
```

### 15.1 Descripción de los archivos

| Archivo o carpeta | Descripción |
|---|---|
| `README.md` | Documentación general de la práctica |
| `Practica3.mlx` | Notebook de MATLAB con el desarrollo computacional |
| `Sistema_Musculoesqueletico.slx` | Modelo del sistema implementado en Simulink |
| `Practica3.py` | Código de simulación desarrollado en Python |
| `Control_vs_Caso.pdf` | Gráficas comparativas del caso control y patológico |
| `Graficas/` | Resultados gráficos de las simulaciones |
| `Analisis_Matematico/` | Evidencia del desarrollo matemático |
| `Modelo_Fisiologico/` | Representación fisiológica elaborada en BioRender |

*Nota: Los nombres de los archivos y carpetas deben coincidir con los nombres reales utilizados en el repositorio.*

[⬆️ Volver al contenido](#contenido)

---

## 16. Requisitos de ejecución

Para ejecutar y revisar los archivos de la práctica se requieren las siguientes herramientas:

### MATLAB

Se utiliza para ejecutar el notebook y realizar los cálculos matemáticos y simulaciones.

### Simulink

Se utiliza para construir y ejecutar el modelo mediante diagramas de bloques.

### Python

Se utiliza para ejecutar el código de simulación y generar gráficas.

### Bibliotecas de Python

Las bibliotecas necesarias para la implementación incluyen:

```bash
pip install numpy matplotlib scipy control
```

[⬆️ Volver al contenido](#contenido)

---

## 17. Reproducibilidad y entregables

Para reproducir los resultados de la práctica se recomienda seguir el orden de trabajo establecido:

1. Revisar la descripción del sistema y su analogía eléctrica.
2. Consultar el desarrollo matemático.
3. Abrir y ejecutar el archivo de MATLAB.
4. Revisar el modelo implementado en Simulink.
5. Ejecutar el código desarrollado en Python.
6. Consultar las gráficas comparativas.
7. Analizar las diferencias entre el caso control y el patológico.
8. Revisar el comportamiento del sistema con el controlador PID.

### Entregables

Los elementos que conforman la documentación y evidencia de la práctica son:

- Modelo matemático del sistema musculoesquelético.
- Función de transferencia.
- Código de MATLAB.
- Modelo de Simulink.
- Código de Python.
- Gráficas de comparación entre control y caso patológico.
- Evidencia del análisis matemático.
- Representación del modelo fisiológico en BioRender.
- Documentación del procedimiento y resultados.

[⬆️ Volver al contenido](#contenido)

---

## 18. Conclusiones

El desarrollo de esta práctica permitió estudiar el comportamiento del sistema musculoesquelético mediante una representación basada en analogías eléctricas.

A través del modelo RC fue posible relacionar los parámetros eléctricos con determinadas propiedades del comportamiento muscular, facilitando el análisis matemático y la simulación del sistema.

La comparación entre el caso control y el caso patológico permitió observar cómo las modificaciones en los parámetros afectan la constante de tiempo y la velocidad de respuesta del modelo.

Asimismo, la implementación de un controlador PID permitió estudiar una estrategia de control para compensar las diferencias entre ambas condiciones y aproximar el comportamiento del sistema patológico al de referencia.

Finalmente, el uso de MATLAB, Simulink y Python permitió complementar el análisis matemático con simulaciones computacionales y representaciones gráficas, reforzando la comprensión del modelado y control de sistemas fisiológicos.

[⬆️ Volver al contenido](#contenido)

---

## 19. Referencias bibliográficas

[1] P. A. Valle, *Syllabus para Modelado de Sistemas Fisiológicos*, Tecnológico Nacional de México, Instituto Tecnológico de Tijuana, 2025. Disponible en: https://biomath.xyz/course/

[2] M. C. Khoo, *Physiological Control Systems: Analysis, Simulation, and Estimation*, 2nd ed. IEEE Press, 2018, sec. 2, p. 26.

[3] N. S. Nise, *Control Systems Engineering*, 8th ed. Wiley, 2020.

[4] T. Kind, T. J. C. Faes, J. W. Lankhaar, A. Vonk-Noordegraaf, and M. Verhaegen, "Estimation of three- and four-element Windkessel parameters using subspace model identification," *IEEE Transactions on Biomedical Engineering*, vol. 57, no. 7, pp. 1531-1538, Jul. 2010. https://doi.org/10.1109/TBME.2010.2041351

[⬆️ Volver al contenido](#contenido)

---

**Tecnológico Nacional de México | Instituto Tecnológico de Tijuana**  
**Ingeniería Biomédica | Modelado de Sistemas Fisiológicos**
