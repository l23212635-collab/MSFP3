[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=l23212635-collab/MSFP3)
# Práctica 3 — Sistema musculoesquelético

Repositorio académico de la asignatura **Modelado de Sistemas Fisiológicos**, correspondiente al programa de **Ingeniería Biomédica** del Tecnológico Nacional de México / Instituto Tecnológico de Tijuana. Esta práctica integra modelado matemático, analogías eléctricas de sistemas fisiológicos, análisis temporal y de estabilidad, diseño de controladores PID, simulación computacional y comparación de resultados.

El caso de estudio representa el **sistema musculoesquelético** mediante una analogía eléctrica basada en un circuito RC. Se busca reproducir y comparar la respuesta del sistema ante una fuerza de entrada \(F(t)\), considerando dos condiciones: un individuo en condiciones normales (control) y un caso patológico. También se analiza la aplicación de un controlador PID para modificar el comportamiento dinámico del modelo.

**Docente:** Dr. Paul Antonio Valle Trujillo

**Correo:** paul.valle@tectijuana.edu.mx

**Departamento:** Ingeniería Eléctrica y Electrónica

**Institución:** Tecnológico Nacional de México / Instituto Tecnológico de Tijuana

**Asignatura:** Modelado de Sistemas Fisiológicos

**Programa:** Ingeniería Biomédica

**Estudiante:** Perez Garcia Diego · 23212635 · l23212635@tectijuana.edu.mx

**Repositorio de la práctica:** https://github.com/l23212635-collab/MSFP3

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
8. [Implementación en MATLAB, Simulink y Simscape](#matlab)
9. [Control en lazo cerrado y sintonización PID](#pid)
10. [Reproducción en Python](#python)
11. [Controlador analógico y laboratorio](#laboratorio)
12. [Resultados y verificación cruzada](#resultados)
13. [Flujo de trabajo](#flujo)
14. [Actividades del estudiante](#actividades)
15. [Estructura del repositorio](#estructura)
16. [Requisitos](#requisitos)
17. [Reproducibilidad y entregables](#reproducibilidad)
18.  [Diagrama del sistema musculoesquelético](#diagrama-del-sistema-musculoesqueletico)
19. [Referencias](#referencias)

---

<a id="resumen"></a>

## Resumen

La práctica tiene como propósito **desarrollar y analizar un modelo matemático del sistema musculoesquelético**, utilizando una analogía eléctrica para representar determinadas propiedades del comportamiento muscular. Mediante elementos resistivos y capacitivos se construye un modelo que permite estudiar la respuesta del sistema ante una fuerza de entrada \(F(t)\).

A partir de la representación eléctrica se establece el modelo matemático y se analiza su comportamiento dinámico. Se consideran dos condiciones de funcionamiento: un caso control, que representa el comportamiento de referencia, y un caso patológico, en el que se modifican los parámetros del modelo para representar una respuesta diferente.

Se estudia la respuesta temporal de ambos escenarios mediante simulaciones computacionales. Posteriormente, se incorpora un **controlador PID** para evaluar su capacidad de modificar la respuesta del caso patológico y aproximarla al comportamiento del caso control. El desarrollo se complementa mediante implementaciones en MATLAB, Simulink y Python, así como con gráficas comparativas.

Esta práctica integra el modelado matemático, el análisis de sistemas dinámicos y la aplicación de conceptos de control clásico a un sistema fisiológico.

**Palabras clave:** sistema musculoesquelético; contracción muscular; fuerza \(F(t)\);Control neuromuscular; Respuesta dinámica; 

[Volver al contenido](#contenido)

---

<a id="objetivos"></a>

## Competencia y objetivos

### Competencia a desarrollar

Comprender los conceptos básicos de Ingeniería de Control, el modelado matemático de sistemas fisiológicos, la respuesta temporal y los criterios de estabilidad mediante la representación eléctrica del sistema musculoesquelético. La práctica permite aplicar herramientas computacionales para analizar el comportamiento del modelo y comparar diferentes condiciones fisiológicas.

### Objetivo general

Desarrollar y analizar un modelo matemático del sistema musculoesquelético mediante una analogía eléctrica, implementando simulaciones computacionales y un controlador PID para comparar la respuesta de un individuo en condiciones normales con un caso patológico.

### Objetivos específicos

- Identificar las variables de entrada y salida, así como los parámetros del modelo eléctrico equivalente.
- Representar el comportamiento del sistema musculoesquelético mediante una analogía eléctrica RC.
- Obtener el modelo matemático y la función de transferencia correspondiente.
- Analizar la respuesta temporal del sistema ante una señal de entrada.
- Comparar el comportamiento dinámico del caso control con el caso patológico.
- Identificar cómo las modificaciones de los parámetros afectan la constante de tiempo y la velocidad de respuesta.
- Implementar el modelo matemático en MATLAB y Simulink.
- Reproducir las simulaciones mediante Python.
- Diseñar e implementar un controlador PID para modificar la respuesta del sistema.
- Evaluar las diferencias entre las respuestas obtenidas antes y después de aplicar el controlador.
- Documentar los resultados matemáticos y computacionales de la práctica en un repositorio de GitHub.

[Volver al contenido](#contenido)

---

<a id="temario"></a>

## Relación con el temario

La práctica integra contenidos correspondientes a las áreas de la asignatura **Modelado de Sistemas Fisiológicos**:

| Área | Contenidos aplicados |
|---|---|
| Sistemas fisiológicos | Descripción y representación del sistema musculoesquelético |
| Modelado matemático | Analogía circuito-sistema fisiológico, ecuaciones diferenciales y función de transferencia |
| Sistemas de control | Diagramas de bloques, respuesta temporal y análisis del comportamiento dinámico |
| Controladores | Diseño e implementación de un controlador PID |
| Simulación computacional | Implementación del modelo en MATLAB, Simulink y Python |

El enfoque combina **Ingeniería de Control, Electrónica, Ciencias de la Computación y Fisiología**, mediante la aplicación de herramientas matemáticas y computacionales para estudiar el comportamiento de un sistema biológico.

[Volver al contenido](#contenido)

---

<a id="analogia"></a>

## Modelo físico y analogía eléctrica

El sistema musculoesquelético se representa mediante una analogía eléctrica RC. Esta representación permite estudiar el comportamiento dinámico asociado a la contracción muscular mediante componentes eléctricos que representan propiedades simplificadas del sistema fisiológico.

La resistencia representa la oposición al movimiento o a la respuesta muscular, mientras que el capacitor representa el almacenamiento de energía asociado al comportamiento del tejido muscular.

| Símbolo | Equivalente eléctrico | Interpretación fisiológica |
|---|---|---|
| \(F(t)\) | Señal de entrada | Fuerza aplicada al sistema |
| \(R\) | Resistencia | Oposición al movimiento o respuesta muscular |
| \(C\) | Capacitancia | Almacenamiento de energía asociado al tejido muscular |
| \(t\) | Tiempo | Evolución temporal de la respuesta |
| Salida | Respuesta del circuito | Comportamiento dinámico asociado a la contracción muscular |

### Parámetros para la emulación eléctrica

El modelo considera parámetros eléctricos que permiten representar las condiciones de funcionamiento del sistema.

Entre los parámetros considerados en el desarrollo de la práctica se encuentran:

| Parámetro | Descripción |
|---|---|
| \(R\) | Resistencia del modelo |
| \(C\) | Capacitancia del modelo |
| \(F(t)\) | Fuerza aplicada como señal de entrada |
| \(R_{\text{control}}\) | Resistencia correspondiente al caso control |
| \(R_{\text{caso}}\) | Resistencia correspondiente al caso patológico |

La diferencia entre el caso control y el patológico se representa mediante modificaciones en los parámetros del modelo, principalmente en la resistencia. Estos cambios producen variaciones en la constante de tiempo y, por consiguiente, en la velocidad de respuesta.

> **Alcance de la analogía:** el circuito RC es una representación simplificada del comportamiento del sistema musculoesquelético. Los componentes eléctricos permiten estudiar matemáticamente ciertas propiedades dinámicas, pero no representan de manera completa todos los procesos fisiológicos involucrados en la contracción muscular.

La representación fisiológica del modelo se complementa con el material gráfico elaborado en BioRender.

[Volver al contenido](#contenido)

---

<a id="modelo"></a>

## Formulación matemática

### 1. Ecuaciones integro-diferenciales

Debido a que el sistema contiene dos fuentes de voltaje, se aplica el principio de superposición para obtener la respuesta total. Se analizan dos circuitos por separado: el primero considera activa la fuente \(F_0(t)\), mientras que el segundo considera activa la fuente \(F(t)\).

**Circuito 1: Fuente \(F_0(t)\) activa**

Aplicando las relaciones del circuito se obtiene:

$$
X(t)=X_1(t)+X_2(t)
$$

Las ecuaciones correspondientes son:

$$
X_1(t)=C_s\frac{d[F(t)-F_{s1}(t)]}{dt}
$$

$$
X_2(t)=\frac{F(t)-F_{s1}(t)}{R}
$$

Considerando la relación con el capacitor \(C_p\):

$$
C_p\frac{dF_{s1}(t)}{dt}=
C_s\frac{d[F(t)-F_{s1}(t)]}{dt}
+
\frac{F(t)-F_{s1}(t)}{R}
$$

Aplicando la transformada de Laplace, con condiciones iniciales nulas:

$$
C_p sF_{s1}(s)=
C_s s[F(s)-F_{s1}(s)]
+
\frac{F(s)-F_{s1}(s)}{R}
$$

Agrupando términos:

$$
\left(C_p s+C_s s+\frac{1}{R}\right)F_{s1}(s) =
\left(C_s s+\frac{1}{R}\right)F(s)
$$

Por lo tanto:

$$
F_{s1}(s)=
\frac{C_sRs+1}{R(C_p+C_s)s+1}F(s)
$$

**Circuito 2: Fuente \(F(t)\) activa**

Para el segundo circuito se considera la relación:

$$
F_0(t)=\alpha F(t)
$$

A partir de las ecuaciones del circuito:

$$
F_{s2}(t)=\frac{1}{C_p+C_s}\int x(t)\,dt
$$

La relación en el dominio de Laplace es:

$$
F_{s2}(s)=\frac{X(s)}{(C_p+C_s)s}
$$

Aplicando la relación de voltajes del circuito:

$$
-\alpha F(s)=
RX(s)+\frac{X(s)}{(C_p+C_s)s}
$$

Despejando y sustituyendo:

$$
F_{s2}(s)=
-\frac{\alpha}{R(C_p+C_s)s+1}F(s)
$$

Finalmente, mediante el principio de superposición:

$$
F_s(s)=F_{s1}(s)+F_{s2}(s)
$$
### 2. Función de transferencia

La función de transferencia se obtiene mediante la suma de las respuestas correspondientes a los dos circuitos analizados.

A partir de:

$$
F_s(s)=F_{s1}(s)+F_{s2}(s)
$$

Se sustituyen las expresiones obtenidas:

$$
F_s(s)=
\frac{C_sRs+1}{R(C_p+C_s)s+1}F(s)-
\frac{\alpha}{R(C_p+C_s)s+1}F(s)
$$

Agrupando términos:

$$
F_s(s)=
\frac{C_sRs+1-\alpha}{R(C_p+C_s)s+1}F(s)
$$

Por lo tanto, la función de transferencia del sistema es:

$$
\boxed{
G(s)=\frac{F_s(s)}{F(s)}=
\frac{C_sRs+1-\alpha}
{R(C_p+C_s)s+1}
}
$$

Donde:

- \(F_s(s)\): fuerza de salida del sistema.
- \(F(s)\): fuerza de entrada.
- \(R\): resistencia eléctrica.
- \(C_p\): capacitancia.
- \(C_s\): capacitancia.
- \(\alpha\): parámetro asociado a la segunda fuente de voltaje.
- \(s\): variable compleja del dominio de Laplace.

Esta función de transferencia representa el comportamiento total del sistema considerando las dos fuentes mediante el principio de superposición.

### 3. Ecuación diferencial ordinaria (EDO)

Partiendo de la función de transferencia:

$$
\frac{F_s(s)}{F(s)}=
\frac{C_sRs+1-\alpha}
{R(C_p+C_s)s+1}
$$

Se realiza el producto cruzado:

$$
[R(C_p+C_s)s+1]F_s(s)=
[C_sRs+1-\alpha]F(s)
$$

Aplicando la transformada inversa de Laplace, considerando condiciones iniciales nulas, se obtiene la ecuación diferencial ordinaria:

$$
\boxed{
R(C_p+C_s)\frac{dF_s(t)}{dt}+F_s(t)=
RC_s\frac{dF(t)}{dt}+(1-\alpha)F(t)
}
$$

Esta ecuación describe la relación dinámica entre la fuerza de entrada y la fuerza de salida del sistema musculoesquelético.

[Volver al contenido](#contenido)

---

<a id="analisis"></a>

## Análisis temporal y de estabilidad

### 1. Error en estado estacionario

Para calcular el error en estado estacionario se considera una entrada escalón unitario:

$$
F(s)=\frac{1}{s}
$$

El error se expresa como:

$$
E(s)=F(s)-F_s(s)
$$

Aplicando el teorema del valor final:

$$
e_{ss}=\lim_{s\to0}sE(s)
$$

Sustituyendo la función de transferencia:

$$
e_{ss}=
\lim_{s\to0}
s\left[
\frac{1}{s}-
\frac{C_sRs+1-\alpha}
{R(C_p+C_s)s+1}\frac{1}{s}
\right]
$$

Simplificando:

$$
e_{ss}=
\lim_{s\to0}
\left[
1-
\frac{C_sRs+1-\alpha}
{R(C_p+C_s)s+1}
\right]
$$

Evaluando el límite:

$$
\boxed{e_{ss}=\alpha}
$$

Por lo tanto, el error en estado estacionario depende del parámetro \(\alpha\).

### 2. Polos y estabilidad

Para determinar la estabilidad del sistema se iguala a cero el denominador de la función de transferencia:

$$
R(C_p+C_s)s+1=0
$$

Despejando el polo:

$$
\boxed{
\lambda=-\frac{1}{R(C_p+C_s)}
}
$$

El sistema presenta un único polo, cuya ubicación depende de la resistencia \(R\) y de las capacitancias \(C_p\) y \(C_s\).

Considerando que:

$$
R>0,\qquad C_p>0,\qquad C_s>0
$$

Se cumple que:

$$
\lambda<0
$$

Por lo tanto, el polo se encuentra en el semiplano izquierdo del plano complejo y **el sistema es estable en lazo abierto**.

### 3. Predicción previa

De acuerdo con la función de transferencia obtenida, se espera que el sistema presente un comportamiento estable cuando sus parámetros eléctricos sean positivos.

Asimismo, las variaciones en la resistencia y las capacitancias modifican la ubicación del polo, afectando la velocidad de respuesta del sistema.

El error en estado estacionario está determinado por el parámetro \(\alpha\), de acuerdo con el análisis realizado.

[Volver al contenido](#contenido)

#### Ejemplo mínimo de verificación en MATLAB

```matlab
% Definición de parámetros del modelo
F0 = 1.0;
alpha = 0.25;

Cg = 10e-6;
Cp = 100e-6;

R_control = 100;
R_caso = 10e3;

% Vector de tiempo
t = 0:1e-3:10;

% Constantes de tiempo
tau_control = R_control * Cp;
tau_caso = R_caso * Cp;

% Mostrar resultados
disp(tau_control)
disp(tau_caso)
```

Este código presenta parámetros utilizados anteriormente en el desarrollo del modelo. La función de transferencia y la implementación definitiva deben corresponder al circuito utilizado en los archivos de la práctica.

[Volver al contenido](#contenido)

---

<a id="senales"></a>

## Señales de entrada y condiciones de simulación

Para estudiar el comportamiento del sistema musculoesquelético se utiliza una señal de entrada que representa la fuerza aplicada sobre el modelo.

La señal permite analizar la respuesta temporal y comparar el comportamiento de las condiciones control y patológica.

En el desarrollo computacional se consideran las siguientes condiciones:

| Variable | Descripción |
|---|---|
| \(F_0\) | Amplitud de la fuerza de entrada |
| \(\alpha\) | Parámetro del modelo |
| \(C_g\) | Capacitancia del modelo |
| \(C_p\) | Capacitancia del modelo |
| \(R_{\text{control}}\) | Resistencia del caso control |
| \(R_{\text{caso}}\) | Resistencia del caso patológico |
| \(t\) | Intervalo de simulación |

La configuración temporal utilizada en el código de referencia es:

\[
t=0:10^{-3}:10\ \mathrm{s}
\]

La señal de entrada se define mediante los parámetros establecidos en el programa de simulación. Para el ejemplo de entrada tipo pulso, se considera un intervalo de aplicación entre \(t=1\) y \(t=2\) segundos.

Las simulaciones permiten observar las diferencias entre ambas condiciones y estudiar el comportamiento del sistema ante la fuerza aplicada.

[Volver al contenido](#contenido)

---

<a id="matlab"></a>

## Implementación en MATLAB, Simulink y Simscape

Se utilizan herramientas de MATLAB y Simulink para implementar el modelo matemático y estudiar la respuesta dinámica del sistema musculoesquelético.

Las representaciones permiten comparar el comportamiento del modelo bajo las condiciones control y patológica.

| Implementación | Descripción | Aspecto por verificar |
|---|---|---|
| MATLAB | Desarrollo matemático y simulación computacional | Consistencia de los parámetros y resultados |
| Simulink | Representación del modelo mediante bloques | Conexiones y comportamiento dinámico |
| Comparación de respuestas | Análisis de las condiciones control y patológica | Diferencias en la respuesta temporal |

### Ejecución desde el cuaderno MATLAB

El cuaderno computacional suministrado permite ejecutar los cálculos y generar las gráficas correspondientes al comportamiento del sistema.

Durante la implementación se consideran las siguientes variables y resultados:

1. **Parámetros:** valores correspondientes al modelo musculoesquelético.
2. **Entrada:** fuerza aplicada al sistema, \(F(t)\).
3. **Caso control:** respuesta del modelo en condiciones normales.
4. **Caso patológico:** respuesta del modelo con parámetros modificados.
5. **Comparación:** representación gráfica de ambas respuestas.

El estudiante debe revisar la conexión entre el desarrollo matemático, los parámetros utilizados y los resultados obtenidos en las simulaciones.

El archivo de MATLAB debe conservarse en el repositorio para permitir la reproducción de los resultados.

[Volver al contenido](#contenido)

---

<a id="pid"></a>

## Control en lazo cerrado y sintonización PID

### 1. Retroalimentación negativa

El controlador PID se incorpora para modificar el comportamiento dinámico del sistema y evaluar la posibilidad de aproximar la respuesta del caso patológico al comportamiento de referencia del caso control.

La señal de error se define de manera general como:

\[
e(t)=r(t)-y(t)
\]

Donde:

- \(e(t)\): error del sistema.
- \(r(t)\): señal de referencia.
- \(y(t)\): salida del sistema.

La señal de control se obtiene mediante la combinación de las acciones proporcional, integral y derivativa.

### 2. Sintonización

El controlador PID utiliza tres ganancias principales:

- \(K_p\): ganancia proporcional.
- \(K_i\): ganancia integral.
- \(K_d\): ganancia derivativa.

La expresión general del controlador es:

\[
u(t)=K_p e(t)+K_i\int e(t)\,dt+K_d\frac{de(t)}{dt}
\]

La sintonización permite modificar el comportamiento del sistema mediante el ajuste de las ganancias del controlador.

Se comparan las respuestas obtenidas antes y después de incorporar el PID para evaluar los cambios en la velocidad de respuesta y el comportamiento transitorio.

### 3. Realización mediante componentes analógicos

La representación física del sistema musculoesquelético se realiza mediante un circuito eléctrico RC, utilizando resistencias, capacitores y fuentes de voltaje para reproducir el comportamiento dinámico establecido en el análisis matemático.

Los componentes considerados son:

| Componente | Función dentro del circuito |
|---|---|
| Resistencia \(R\) | Representa la oposición al movimiento o a la respuesta muscular. |
| Capacitor \(C_p\) | Representa el almacenamiento de energía del modelo. |
| Capacitor \(C_s\) | Participa en la dinámica del circuito y en la respuesta del sistema. |
| Fuente \(F(t)\) | Representa la señal de entrada aplicada al sistema. |
| Fuente \(F_0(t)\) | Representa la segunda fuente de voltaje considerada en el análisis. |

Para obtener la respuesta total se aplica el principio de superposición, considerando por separado la contribución de cada fuente de voltaje y posteriormente sumando ambas respuestas:

\[
F_s(t)=F_{s1}(t)+F_{s2}(t)
\]

La relación entre las fuentes se establece mediante el parámetro \(\alpha\):

\[
F_0(t)=\alpha F(t)
\]

El comportamiento del circuito se describe mediante la función de transferencia obtenida en el análisis matemático:

\[
\boxed{
G(s)=
\frac{C_sRs+1-\alpha}
{R(C_p+C_s)s+1}
}
\]

Esta expresión permite relacionar los componentes físicos del circuito con el comportamiento dinámico del sistema musculoesquelético.

La implementación considera dos condiciones de funcionamiento: el caso control y el caso patológico. Las diferencias se representan mediante la modificación de los parámetros del circuito, principalmente la resistencia, lo que produce cambios en la constante de tiempo y en la respuesta del sistema.

La realización mediante componentes analógicos permite establecer una correspondencia entre el modelo matemático y su representación eléctrica, facilitando la comparación de los resultados teóricos y computacionales.

> **Nota:** En esta sección se describe la implementación del modelo fisiológico mediante el circuito RC. No se especifica un diseño físico de controlador PID con amplificadores operacionales dentro del análisis matemático presentado..

[Volver al contenido](#contenido)

---

<a id="python"></a>

## Reproducción en Python

Python se utiliza como herramienta complementaria para reproducir las simulaciones y representar gráficamente el comportamiento del sistema musculoesquelético.

La implementación permite comparar los resultados obtenidos con MATLAB y analizar las respuestas de las condiciones control y patológica.

El programa considera los siguientes apartados:

1. Definición del vector temporal.
2. Establecimiento de los parámetros del modelo.
3. Definición de la señal de entrada.
4. Construcción del modelo matemático.
5. Simulación de la respuesta del caso control.
6. Simulación de la respuesta del caso patológico.
7. Implementación del controlador PID.
8. Generación de gráficas comparativas.

Las principales bibliotecas consideradas para el desarrollo son:

- **NumPy:** operaciones numéricas y manejo de arreglos.
- **Matplotlib:** generación de gráficas.
- **SciPy:** herramientas para análisis y simulación de sistemas.
- **Control:** modelado y análisis de sistemas de control.

El código Python forma parte de los archivos del repositorio y permite complementar el análisis realizado en MATLAB y Simulink.

[Volver al contenido](#contenido)

---

<a id="laboratorio"></a>

## Controlador analógico y laboratorio

### Materiales y equipo

Para el desarrollo computacional de la práctica se utilizan herramientas de modelado y simulación.

Los recursos documentados incluyen:

**Herramientas computacionales:** MATLAB, Simulink y Python.

**Recursos de documentación:** gráficas de resultados, evidencia del análisis matemático y representación del modelo fisiológico en BioRender.

### Configuración de las simulaciones

Las simulaciones se realizan utilizando los parámetros correspondientes a cada condición del sistema musculoesquelético.

Se consideran los siguientes elementos:

| Elemento | Función |
|---|---|
| Señal de entrada | Representa la fuerza aplicada al sistema |
| Caso control | Representa la condición normal |
| Caso patológico | Representa la condición con parámetros modificados |
| Controlador PID | Modifica la respuesta dinámica del modelo |
| Gráficas | Permiten comparar los resultados |

### 1. Modelo del sistema en lazo abierto

El sistema en lazo abierto se analiza a partir de la función de transferencia obtenida mediante el principio de superposición, considerando las dos fuentes de voltaje del circuito RC.

La función de transferencia del sistema es:

\[
G(s)=\frac{F_s(s)}{F(s)}=
\frac{C_sRs+1-\alpha}
{R(C_p+C_s)s+1}
\]

A partir de esta expresión se analiza el comportamiento dinámico del sistema, considerando su respuesta temporal, el error en estado estacionario y la ubicación de sus polos.

El polo del sistema se obtiene mediante:

\[
s=-\frac{1}{R(C_p+C_s)}
\]

Para valores positivos de resistencia y capacitancias, el polo se encuentra en el semiplano izquierdo, por lo que el sistema es estable en lazo abierto.

Se comparan las condiciones control y patológica mediante la modificación de los parámetros del circuito, principalmente la resistencia.

### 2. Sistema en lazo cerrado

Para estudiar el comportamiento del sistema en lazo cerrado se considera la incorporación de un controlador PID y un esquema de retroalimentación negativa.

El error se define como la diferencia entre la señal de referencia y la salida del sistema:

\[
e(t)=r(t)-F_s(t)
\]

El controlador PID utiliza tres acciones de control:

\[
C(s)=K_p+\frac{K_i}{s}+K_ds
\]

Donde:

- \(K_p\): ganancia proporcional.
- \(K_i\): ganancia integral.
- \(K_d\): ganancia derivativa.

La función de transferencia en lazo cerrado, considerando retroalimentación unitaria, se expresa de manera general como:

\[
T(s)=\frac{C(s)G(s)}{1+C(s)G(s)}
\]

La incorporación del controlador permite modificar la respuesta dinámica del sistema y evaluar si el comportamiento del caso patológico puede aproximarse al del caso control.

La comparación entre la respuesta en lazo abierto y en lazo cerrado permite analizar el efecto del controlador sobre el comportamiento del modelo.

### 3. Comparación con la simulación

Los resultados obtenidos mediante MATLAB, Simulink y Python permiten comparar las diferentes implementaciones del modelo.

La comparación debe considerar:

- Diferencias en los parámetros utilizados.
- Comportamiento de la respuesta temporal.
- Velocidad de respuesta.
- Efecto del controlador PID.
- Consistencia entre las gráficas obtenidas.

[Volver al contenido](#contenido)

---

<a id="resultados"></a>

## Resultados y verificación cruzada

Las respuestas permiten contrastar el comportamiento del sistema musculoesquelético bajo dos condiciones: caso control y caso patológico.

El análisis gráfico permite identificar las diferencias en la respuesta dinámica y estudiar los efectos de los cambios en los parámetros del modelo.

### Archivos de resultados identificados en el repositorio

| Tipo de evidencia | Archivo | Descripción |
|---|---|---|
| Análisis matemático | [Análisis Matemático_3.pdf](Análisis%20Matemático_3.pdf) | Desarrollo de las ecuaciones integro-diferenciales, función de transferencia, EDO, error en estado estacionario, polos y estabilidad. |
| Resultados de MATLAB | [Control y Caso_matlab3.pdf](Control%20y%20Caso_matlab3.pdf) | Gráficas comparativas de la respuesta del caso control y el caso patológico. |
| Controlador PID | [Controlador PID.jpeg](Controlador%20PID.jpeg) | Evidencia gráfica del controlador PID. |
| Diagrama musculoesquelético | [Diagrama Muscoesqueletico P.3.png](Diagrama%20Muscoesqueletico%20P.3.png) | Representación gráfica del sistema musculoesquelético. |
| Modelo fisiológico | [Sistema_Musculoesqueletico.pdf](Sistema_Musculoesqueletico.pdf) | Documento con la representación del sistema musculoesquelético. |
| Cuaderno MATLAB | [Perez23212635_3.mlx.m](Perez23212635_3.mlx.m) | Archivo correspondiente al desarrollo computacional en MATLAB. |
| Modelo Simulink | [Sistema3 (1).slx](Sistema3%20(1).slx) | Modelo del sistema implementado mediante diagramas de bloques en Simulink. |
| Simulación en Python | [perez23212635.py.py](perez23212635.py.py) | Código utilizado para reproducir el modelo y generar simulaciones. |
| Cuadernillo de la práctica | [Perez23212635_3_Cuadernillo.pdf](Perez23212635_3_Cuadernillo.pdf) | Documento complementario con el desarrollo y las evidencias de la práctica. |

**Archivos complementarios del repositorio:**

- `CITATION.cff`: información para citar el repositorio.
- `LICENSE`: archivo con la licencia del proyecto.
- `README.md`: documentación general de la práctica.

Los archivos anteriores corresponden a las evidencias y herramientas utilizadas durante el desarrollo de la práctica. Los documentos PDF se enlazan para su consulta, mientras que los archivos de MATLAB, Simulink y Python permiten revisar las implementaciones computacionales.

[Volver al contenido](#contenido)

### Aspectos para discutir

- Correspondencia entre la analogía eléctrica y el sistema musculoesquelético.
- Diferencias entre las respuestas del caso control y el patológico.
- Efecto de los cambios en los parámetros del modelo.
- Comportamiento de la respuesta temporal.
- Efecto del controlador PID sobre la respuesta del sistema.
- Consistencia entre los resultados de MATLAB, Simulink y Python.
- Limitaciones de la representación eléctrica del sistema fisiológico.

**Resultados del estudiante:** incorporar las gráficas obtenidas, los resultados de las simulaciones y una interpretación propia sobre las diferencias entre el caso control y el patológico. Los valores y las figuras deben corresponder a los archivos ejecutados en el repositorio.

[Volver al contenido](#contenido)

---

<a id="flujo"></a>

## Flujo de trabajo

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
              MATLAB
                  |
                  v
              Simulink
                  |
                  v
      Análisis del caso control y patológico
                  |
                  v
          Diseño del controlador PID
                  |
                  v
                Python
                  |
                  v
         Comparación de resultados
                  |
                  v
         Interpretación y conclusiones
                  |
                  v
         Documentación en GitHub
```

El procedimiento integra la formulación matemática, la simulación *in silico* y la comparación de resultados para estudiar el comportamiento del sistema musculoesquelético.

[Volver al contenido](#contenido)

---

<a id="actividades"></a>

## Actividades del estudiante

La práctica sigue una secuencia de **modelado, simulación, comparación y documentación**, enfocada en el análisis del comportamiento del sistema musculoesquelético.

### Etapa 1. Formulación y análisis

- [ ] Identificar las variables de entrada y salida del modelo.
- [ ] Identificar los elementos de la analogía eléctrica RC.
- [ ] Establecer los parámetros del modelo.
- [ ] Desarrollar las ecuaciones matemáticas.
- [ ] Obtener la función de transferencia.
- [ ] Analizar la constante de tiempo.
- [ ] Comparar las condiciones control y patológica.

### Etapa 2. Simulación de la planta

- [ ] Implementar el modelo en MATLAB.
- [ ] Implementar el modelo en Simulink.
- [ ] Definir la señal de entrada.
- [ ] Simular la respuesta del caso control.
- [ ] Simular la respuesta del caso patológico.
- [ ] Generar las gráficas comparativas.

### Etapa 3. Diseño y comprobación del controlador

- [ ] Implementar el controlador PID.
- [ ] Identificar las ganancias proporcional, integral y derivativa.
- [ ] Analizar la respuesta del sistema con el controlador.
- [ ] Comparar la respuesta controlada con la respuesta original.
- [ ] Reproducir las simulaciones mediante Python.
- [ ] Comparar los resultados obtenidos en las diferentes herramientas.

### Etapa 4. Comprobación y documentación

- [ ] Incorporar las gráficas de MATLAB.
- [ ] Incorporar el modelo de Simulink.
- [ ] Incorporar el código de Python.
- [ ] Agregar evidencia del análisis matemático.
- [ ] Agregar la representación fisiológica en BioRender.
- [ ] Documentar los resultados y las diferencias observadas.
- [ ] Publicar los archivos correspondientes en GitHub.

[Volver al contenido](#contenido)

---

<a id="estructura"></a>

## Estructura del repositorio

Una organización **sugerida** para la entrega, compatible con los tipos de archivos identificados en la práctica, es:

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

**Criterio de nombres:** los nombres anteriores representan una propuesta de organización. Deben coincidir con los nombres reales de los archivos incluidos en el repositorio. Si se utilizan otras denominaciones o subcarpetas, actualizar las rutas del README para que los enlaces funcionen correctamente.

[Volver al contenido](#contenido)

---

<a id="requisitos"></a>

## Requisitos

### Software

- **MATLAB**, para realizar los cálculos y simulaciones matemáticas.
- **Simulink**, para implementar el modelo mediante diagramas de bloques.
- **Python**, para reproducir las simulaciones y generar gráficas.
- **NumPy**, para operaciones numéricas.
- **Matplotlib**, para la representación gráfica.
- **SciPy**, para herramientas de análisis y simulación.
- **Control**, para el modelado y análisis de sistemas de control.
- **Git y GitHub**, para organizar y presentar el repositorio de la práctica.

Las versiones mínimas de software y las dependencias específicas deben verificarse con los archivos originales de la práctica.

### Recursos de laboratorio

La documentación de la práctica contempla recursos computacionales y evidencia gráfica del modelo. No se especifica un montaje físico obligatorio ni una lista de componentes de laboratorio para esta implementación.

[Volver al contenido](#contenido)

---

<a id="reproducibilidad"></a>

## Reproducibilidad y entregables

### Secuencia de reproducción

1. Consultar el repositorio de la práctica y descargar los archivos correspondientes.
2. Revisar la descripción del sistema musculoesquelético y su analogía eléctrica.
3. Identificar las variables y los parámetros del modelo.
4. Consultar el desarrollo matemático y la función de transferencia.
5. Ejecutar el archivo de MATLAB.
6. Revisar y ejecutar el modelo de Simulink.
7. Ejecutar el código de Python.
8. Comparar las respuestas del caso control y el caso patológico.
9. Analizar el comportamiento del sistema con el controlador PID.
10. Incorporar las gráficas y evidencias al repositorio.
11. Completar la documentación y las conclusiones de la práctica.

### Resultados mínimos esperados

| Entregable | Evidencia solicitada |
|---|---|
| Modelo matemático | Desarrollo de las ecuaciones del sistema |
| Función de transferencia | Representación matemática del modelo |
| Análisis del sistema | Comparación de las condiciones control y patológica |
| MATLAB | Cuaderno computacional `.mlx` |
| Simulink | Modelo del sistema `.slx` |
| Python | Código de simulación `.py` |
| Resultados | Gráficas comparativas en PDF |
| Evidencia matemática | Desarrollo y análisis del modelo |
| Modelo fisiológico | Representación elaborada en BioRender |
| Documentación | `README.md` y explicación de resultados |

### Criterios de presentación académica

En el README final debe distinguirse entre **resultados obtenidos mediante simulación**, **parámetros utilizados en el modelo** y **análisis realizado por el estudiante**.

La ejecución de los programas y la generación de figuras no sustituyen la interpretación del comportamiento fisiológico y matemático del sistema. Es importante explicar las diferencias entre las condiciones control y patológica, así como el efecto del controlador PID.

[Volver al contenido](#contenido)

---

<a id="referencias"></a>

---

<a id="diagrama-del-sistema-musculoesqueletico"></a>

## Diagrama del sistema musculoesquelético

La siguiente figura representa el modelo fisiológico del sistema musculoesquelético, mostrando la comparación entre el caso control y el caso patológico asociado a la atrofia muscular, así como su correspondiente modelo mecánico.

![Diagrama del sistema musculoesquelético](DIagrama%20Muscoesqueletico%20P.3.png)

[Volver al contenido](#contenido)

---

## Referencias

[1] P. A. Valle, *Syllabus para Modelado de Sistemas Fisiológicos*, Tecnológico Nacional de México / Instituto Tecnológico de Tijuana, 2025. Disponible en: https://biomath.xyz/course/

[2] M. C. Khoo, *Physiological Control Systems: Analysis, Simulation, and Estimation*, 2nd ed., IEEE Press, 2018, sección 2, p. 26.

[3] N. S. Nise, *Control Systems Engineering*, 8th ed., John Wiley & Sons, 2020.

[4] T. Kind, T. J. Faes, J. W. Lankhaar, A. Vonk-Noordegraaf, and M. Verhaegen, "Estimation of three- and four-element Windkessel parameters using subspace model identification," *IEEE Transactions on Biomedical Engineering*, vol. 57, no. 7, pp. 1531-1538, Jul. 2010. https://doi.org/10.1109/TBME.2010.2041351

[Volver al contenido](#contenido)

---

## Uso académico

Este repositorio se utiliza como evidencia de la práctica de **Modelado de Sistemas Fisiológicos**, enfocada en el estudio del sistema musculoesquelético mediante una analogía eléctrica RC.

Su finalidad es desarrollar habilidades de modelado matemático, análisis de sistemas dinámicos, simulación computacional y aplicación de controladores PID. El trabajo permite comparar diferentes condiciones de funcionamiento del modelo y estudiar cómo las modificaciones de sus parámetros afectan la respuesta del sistema.

Los resultados deben corresponder a las simulaciones y archivos desarrollados por el estudiante. Cualquier modificación de parámetros, estructura del modelo o procedimiento debe identificarse y justificarse.
