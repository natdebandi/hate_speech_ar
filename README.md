# hate_speech_ar

## Este proyecto forma parte del Trabajo Final para la especialización en ciencias de datos del ITBA
Junio 2024

Este trabajo parte de los hallazgos obtenidos en la investigación realizada por Juan Manuel Pérez, Viviana Cotik y un equipo de ocho investigadores de distintas disciplinas que conformaban el proyecto PIUBAMAS Big Data y del cual se formó parte [Pérez et al., 2023](https://ieeexplore.ieee.org/document/10076443) . Se tomó como base el dataset construido en el marco de dicho proyecto, el cual consiste en un conjunto de más de 300 mil tweets, publicados por las cuentas de los principales diarios, relacionados con noticias y notas periodísticas y las  respuestas a estos tweets, cerca de 5 millones de Tweets. Su recolección se realizó a partir de una API de Twitter de Stream entre el 1º de marzo de 2020 y el 31 de mayo de 2021.
Data set disponible en: https://huggingface.co/piuba-bigdata

El trabajo consiste en entrenar dos modelos BERT y GPT, evaluar el performance y aplicar el mejor modelo para caracterizar los discrusos de odio en X en Argentina durante la pandemia.

**Indice de notebooks**

**(1) Finetuning de BETO**
En las siguientes notebooks se encuentra en finetuning de BETO y las métricas resultantes:

BETO (Bert en español) binario  (hateful / not hateful)
[1_finetunning_BETO_bin.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/5731ca1052f45a7e10dfcacf717acf1a71be03b8/1_finetunning_BETO_bin.ipynb)

BETO (BERT en español) multietietiqueta (hateful, WOMEN, RACISM, etc.)

[1_finetunning_BETO_multiclass2.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/97221e5efae9ebfe0ad9e52142fe3b270ac1d3bd/1_finetuning_BETO_multiclass2.ipynb)

Cuaderno de pruebas de los moelo BETO
[prueba_modelos.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/a03a6a396c0741589779d9ba91031ca328ab25d8/prueba_modelos.ipynb)

**(2) GPT 4 mini sin finetuning**

Esta notebook se uso para probar el funcionamiento y la forma de utilizar GPT para clasificación:

[Pruebas_GPT.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/a03a6a396c0741589779d9ba91031ca328ab25d8/Pruebas_GPT.ipynb)

Lo que se realizó con GPT fue primero utilizar GPT 4 mini para clasificar el conjunto de test en formato binario (hATEFUL/NOT HATEFUL) y también con las etiquetas múltiples.
Para ello se preparar archivos BATCH que se envía a GPT que luego devuelve un archivo con el resultado, sobre ese se calculan las métricas. Esta clasificación se realizó sobre el cojunto de test para tener comparabilidad con los otros modelos

A continuación se encuentran las 4 notebooks, para cada caso (binario y multietiqueta) el proceso de preparación del archivo BATCH y luego la recuperación de la clasificación y el cálculo de métricas.

*Clasificación binaria (hateful / not hateful)*

Para aplicar el GPT mediante batch:

[2_GPT_bin_batch2.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/a03a6a396c0741589779d9ba91031ca328ab25d8/2_GPT_bin_batch2.ipynb)

Para evaluarlo desde Batch:

[2_GPT_evaluate_batch2.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/a03a6a396c0741589779d9ba91031ca328ab25d8/2_GPT_evaluate_batch2.ipynb)

*Multietiqueta (hateful, WOMEN, RACISM, etc.)*

Para aplicar el GPT mediante batch:

[2_GPT_multiclass_batch.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/a03a6a396c0741589779d9ba91031ca328ab25d8/2_GPT_multiclass_batch.ipynb)

Para evaluarlo desde Batch:

[2_GPT_evaluate_batch_multi.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/a03a6a396c0741589779d9ba91031ca328ab25d8/2_GPT_evaluate_batch_multi.ipynb)

**(3) Finetuning de GPT 3.5**

Este último proceso consiste en realizar un finetuning de GPT 3.5 (GPT 4 no está disponible para realizar finetuning en nuestro caso) tanto para una clsificación binaria como multiclase.

Para ello se preparó el archivo de finetunning (similar al esquema de BATCH) y se envía a GPT para entrenamiento. Luego se recupera el resultado (GET) y se envía el archivo de TEST para clasificación con el nuevo modelo (nuevamente medinte batch) y finalmente se obtiene el resultado y se envalua. Es decir que hay tres notebooks involucradas:

*Finetunning GPT 3.5 BINARIO:*

Preparación archivo para fine tunning:

[3_GPT_finetuning_bin.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/ffbf927fec6207eace6612ee0c148967862a588e/3_GPT_finetuning_bin.ipynb)

Recuperacón del modelo, evaluación inicial del modelo y preparación de archivo para usar el claisificador nuevo (vía BATCH):

[3_GPT_evaluate_bin_finetunning.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/5f998b23eb9b1f4edccea7c4ba6dbf8deb7b1cc0/3_GPT_evaluate_bin_finetunning.ipynb)

Recupero la clasificación realizada con el modelo binario con FINETUNING al conjunto de test y aplico las métricas:

[3_GPT_evaluate_bin_finetuning_2.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/2da1dfac5d7ad5e20c43f5a5838a3bc6a5edde6c/3_GPT_evaluate_bin_finetuning_2.ipynb)

*Finetunning GPT 3.5 Multietiqueta (hateful, WOMEN, RACISM, etc.)*
Preparación archivo para fine tunning:

[3_GPT_finetuning_multiclass.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/990cde5d2f511aa7707fb6fca91ea4da732965fd/3_GPT_finetuning_multiclass.ipynb)

Recuperacón del modelo, evaluación inicial del modelo y preparación de archivo para usar el claisificador nuevo (vía BATCH):

[3_GPT_evaluate_finetuning_multi.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/990cde5d2f511aa7707fb6fca91ea4da732965fd/3_GPT_evaluate_finetuning_multi.ipynb)

Recupero la clasificación realizada con el modelo MULTI-ETIQUETA con FINETUNING al conjunto de test y aplico las métricas:

[3_GPT_evaluate_finetuning_multi_2.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/990cde5d2f511aa7707fb6fca91ea4da732965fd/3_GPT_evaluate_finetuning_multi_2.ipynb)


** comparacion de modelos **
Para finalizar se realizaron dos Notebooks que simplifican la comparación de los modelos

[4_model_comparison_bin.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/30ef848846eb50bdbffbada1a194204e19f20ee3/4_model_comparison_bin.ipynb)


[4_model_comparison_multilabel.ipynb](https://github.com/natdebandi/hate_speech_ar/blob/30ef848846eb50bdbffbada1a194204e19f20ee3/4_model_comparison_multilabel.ipynb)





