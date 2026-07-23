# Ficha de análisis
Actividad de Clase: Analizando Agentes de IA con Hugging Face Spaces

## 1. Nombre del Space

* **Nombre:** NLLB (No Language Left Behind) — UNESCO Language Translator
* **Enlace:** https://huggingface.co/spaces/UNESCO/nllb

## 2. ¿Qué hace el agente?

Este Space funciona como un traductor de textos. Permite traducir entre más de 200 idiomas, incluyendo algunos que normalmente no aparecen en traductores comerciales.

Para usarlo, la persona selecciona el idioma original, el idioma al que quiere traducir, escribe el texto y presiona el botón de traducción. El sistema utiliza el modelo NLLB de Meta para generar el resultado.

## 3. Análisis PEAS

| Elemento    | Respuesta                                                                                                                                                       |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Performance | Se puede evaluar revisando si la traducción conserva el significado original, si está bien escrita, cuánto tarda en responder y cuántos idiomas puede traducir. |
| Environment | Está formado por la página web, el texto escrito por el usuario, los idiomas disponibles y el modelo NLLB que realiza la traducción.                            |
| Actuators   | Su acción principal es mostrar el texto traducido en el campo de resultado. También actualiza los idiomas seleccionados en la interfaz.                         |
| Sensors     | Recibe información por medio del texto ingresado y de los menús donde se seleccionan el idioma de origen y el idioma de destino.                                |

## 4. Clasificación del entorno

| Propiedad    | Clasificación | Justificación                                                                                                                                    |
| ------------ | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Observable   | Parcial       | El usuario puede ver el texto de entrada, los idiomas seleccionados y la traducción, pero no puede observar cómo trabaja el modelo internamente. |
| Determinista | Sí            | Se ingresó el mismo texto varias veces con los mismos idiomas y la traducción obtenida fue exactamente igual.                                    |
| Episódico    | Sí            | Cada traducción se realiza por separado. El sistema no necesita recordar las traducciones anteriores para generar una nueva.                     |
| Estático     | Sí            | Mientras el sistema traduce, el texto y los idiomas no cambian, a menos que el usuario haga una nueva modificación.                              |
| Discreto     | Sí            | Los idiomas disponibles y las acciones que puede realizar el usuario, como escribir, elegir idiomas y traducir, están claramente definidas.      |
| Conocido     | Sí            | Se conoce de manera general cómo funciona el modelo NLLB, ya que fue desarrollado y documentado públicamente por Meta.                           |

## 5. ¿Qué tipo de programa de agente creemos que es?

**Agente de reflejo simple**

Consideramos que es un agente de reflejo simple porque recibe una entrada y genera una respuesta directa.

El usuario escribe un texto, selecciona los idiomas y el sistema entrega la traducción. No guarda información de traducciones anteriores ni realiza una planificación de varios pasos. Su función principal es relacionar una entrada con una salida.

# Reto adicional

Encontrar un Space que pueda clasificarse como:

* Totalmente observable, determinista y episódico.
* Parcialmente observable, estocástico y secuencial.

## 1. Totalmente observable, determinista y episódico

**Space:** NLLB — UNESCO Language Translator
**Enlace:** https://huggingface.co/spaces/UNESCO/nllb

### Justificación

* **Totalmente observable:** Para realizar la traducción, el agente recibe toda la información necesaria: el texto, el idioma original y el idioma de destino. No necesita buscar información adicional.

* **Determinista:** Se probó el mismo texto dos veces, usando los mismos idiomas, y la traducción fue igual en ambos intentos. Por eso se concluyó que la misma entrada genera la misma salida.

* **Episódico:** Cada traducción funciona como una tarea independiente. El resultado actual no depende de los textos traducidos anteriormente.

## 2. Parcialmente observable, estocástico y secuencial

**Space:** Hy3 Chat Demo (Tencent)
**Enlace:** https://huggingface.co/spaces/tencent/Hy3

### Justificación

* **Parcialmente observable:** El agente solo conoce la información que el usuario escribe, no puede saber completamente qué está pensando la persona o cuál es su intención real.

* **Estocástico:** La interfaz tiene una opción llamada **Temperature**, que controla qué tan variadas o aleatorias pueden ser las respuestas, por eso, una misma pregunta puede generar respuestas diferentes.

* **Secuencial:** El agente recuerda los mensajes anteriores de la conversación, para comprobarlo, primero se le pidió un dato curioso y respondió mencionando al astronauta Stuart Roosa. Después se le preguntó: “¿Qué astronauta acabas de mencionar?” y respondió correctamente, esto demuestra que utiliza el contexto anterior para contestar.
