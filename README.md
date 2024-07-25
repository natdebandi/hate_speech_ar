# hate_speech_ar

## Este proyecto forma parte del Trabajo Final para la especialización en ciencias de datos del ITBA
Junio 2024

Este trabajo parte de los hallazgos obtenidos en la investigación realizada por Juan Manuel Pérez, Viviana Cotik y un equipo de ocho investigadores de distintas disciplinas que conformaban el proyecto PIUBAMAS Big Data y del cual se formó parte [Pérez et al., 2023](https://ieeexplore.ieee.org/document/10076443) . Se tomó como base el dataset construido en el marco de dicho proyecto, el cual consiste en un conjunto de más de 300 mil tweets, publicados por las cuentas de los principales diarios, relacionados con noticias y notas periodísticas y las  respuestas a estos tweets, cerca de 5 millones de Tweets. Su recolección se realizó a partir de una API de Twitter de Stream entre el 1º de marzo de 2020 y el 31 de mayo de 2021.
Data set disponible en: https://huggingface.co/piuba-bigdata

El trabajo consiste en entrenar dos modelos BERT y GPT, evaluar el performance y aplciar el mejor modelo para caracterizar los discrusos de odio en X en Argentina durante la pandemia.

Para ello se entrenaron 4 modelos:
(1) BETO (Bert en español) binario

[1_finetunning_BETO_bin.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/5731ca1052f45a7e10dfcacf717acf1a71be03b8/1_finetunning_BETO_bin.ipynb)

(2) BETO (BERT en español) multietietiqueta

[1_finetunning_BETO_multiclass.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/1201a73795c613602254fe37b200d9440f0c8987/1_finetuning_BETO_multiclass.ipynb)

(3) GPT (modelo GPT 4 mini) binario

(4) GPT (modelo GPT 4 mini) multietiqueta


**Pruebas de los modelos**

Para usar los modelos BETO se puede usar la siguiente notebook:

La siguiente notebook, contempla las pruebas iniciales de GPT:




