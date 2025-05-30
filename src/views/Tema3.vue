<template lang="pug">
.curso-main-container.pb-3
  BannerInterno
  .container.tarjeta.tarjeta--blanca.p-4.p-md-5.mb-5
    .titulo-principal.color-acento-contenido
      .titulo-principal__numero
        span 3
      h1 Integración y almacenamiento de datos
    .row.justify-content-center.align-items-center.mb-5
      .col-lg-3
        figure
          img(src="@/assets/curso/temas/tema3/img1.svg", alt="alt")

      .col-lg-9
        p La integración de datos consiste en combinar información proveniente de diversas fuentes heterogéneas en un conjunto de datos unificado y coherente. Este proceso busca ofrecer una visión completa y consistente de la información para su análisis y posterior explotación en modelos de inteligencia artificial o sistemas de apoyo a decisiones. Una de las tareas fundamentales en la integración es resolver las discrepancias en los nombres de atributos, estructuras y dimensiones, evitando duplicidades y conflictos que puedan comprometer la calidad del conjunto final (Wang, 2017).
        p Las herramientas ETL (#[i Extract, Transform, Load]) y ELT (#[i Extract, Load, Transform]) son estrategias ampliamente utilizadas en los procesos de integración. En el enfoque ETL, los datos son extraídos de sus fuentes, transformados para adecuarlos a los requisitos de destino “lo que puede incluir tareas de limpieza, normalización, enriquecimiento y catalogación” y, posteriormente, cargados en un repositorio, como un #[i Data Warehouse] o un #[i Data Lake]. En cambio, el enfoque ELT invierte parte del proceso: los datos son primero extraídos y cargados en el destino para luego ser transformados, aprovechando las capacidades de procesamiento de los sistemas modernos (Elgendy, 2014).
    p.mb-4 La integración de datos también puede incorporar técnicas como la reconciliación de entidades (#[i entity resolution]), el mapeo semántico y el uso de #[i middlewares] o plataformas de integración, como los #[i Enterprise Service Bus] (ESB) o los sistemas basados en API. Estos enfoques permiten gestionar no solo bases de datos estructuradas, sino también fuentes de datos semiestructuradas o no estructuradas.

    .bloque-texto-g.bloque-texto-g--inverso.color-primario.p-3.p-sm-4.p-md-5.mb-5(data-aos="fade-right").mb-5
      .bloque-texto-g__img(
        :style="{'background-image':`url(${require('@/assets/curso/temas/tema3/img2.png')})`}"
      )
      .bloque-texto-g__texto.p-4
        p.mb-0 El almacenamiento de los datos integrados depende de las necesidades específicas del proyecto y puede organizarse en estructuras tradicionales como bases de datos relacionales, en almacenes optimizados para el análisis (#[i Data Warehouses]) o en repositorios flexibles diseñados para manejar grandes volúmenes y variedad de datos (#[i Data Lakes]). La elección adecuada de la estrategia de almacenamiento resulta crucial para garantizar que los datos puedan ser accedidos, consultados y procesados de manera eficiente y segura.
    p En definitiva, la integración y almacenamiento de datos constituyen pasos estratégicos que aseguran la disponibilidad de información fiable, consistente y de calidad para su posterior análisis, modelado y toma de decisiones basada en datos.

    separador
    #t_3_1.titulo-segundo.color-acento-contenido(data-aos="flip-up")
      h2 3.1 Proceso ETL
    p.mb-5 El proceso ETL (extracción, transformación y carga) constituye un componente esencial en el tratamiento de grandes volúmenes de datos y en la construcción de #[i Data Warehouses]. Según Almeida (2013), este proceso se compone de tres etapas principales que operan de forma secuencial:
    .row.justify-content-center.align-items-center.mb-3
      .col-lg-10
        LineaTiempoD.color-acento-botones
          .row(numero="A" titulo="Extracción").p-3
            .col-md-12.mb-4.mb-md-0
              p Es el primer paso del proceso ETL y consiste en obtener datos relevantes de múltiples fuentes, que pueden incluir sistemas OLTP (Online Transaction Processing), hojas de cálculo, archivos de texto, bases de datos no estructuradas o contenido web. Para optimizar el tiempo de procesamiento, no siempre se extraen todos los datos, sino únicamente aquellos que han cambiado desde la última ejecución, principalmente registros nuevos o actualizados. La detección de cambios suele realizarse mediante la comparación entre dos instantáneas de los datos: una correspondiente a la última extracción y otra actual. Para este fin, las herramientas ETL emplean conectividad directa con las fuentes mediante conectores, APIs (Application Programming Interfaces) o servicios de datos, asegurando un acceso eficiente y seguro.
              figure
                img(src='@/assets/curso/temas/tema3/img3.png', alt='Texto que describa la imagen')
          .row(numero="B" titulo="Transformación").p-3
            .col-md-12.mb-4.mb-md-0
              p Una vez extraídos los datos, estos se someten a una serie de rutinas de transformación que los adaptan, corrigen y estructuran para que sean compatibles con el esquema del Data Warehouse. Esta etapa contempla diversas operaciones, como reformatear atributos, recalcular valores, modificar estructuras clave, agregar elementos temporales, asignar valores por defecto, seleccionar información relevante y consolidar datos dispersos. Durante la transformación, también se aplican procesos de limpieza de datos para corregir errores, inconsistencias y valores atípicos. Esto puede implicar traducir esquemas, filtrar información no deseada, agregar datos resumidos o utilizar herramientas de limpieza especializadas. La transformación no solo prepara los datos para su almacenamiento, sino que también garantiza su calidad y uniformidad.
              figure
                img(src='@/assets/curso/temas/tema3/img4.png', alt='Texto que describa la imagen')
          .row(numero="C" titulo="Carga").p-3
            .col-md-12.mb-4.mb-md-0
              p Representa la etapa final del proceso ETL y tiene como objetivo incorporar los datos transformados en el repositorio de destino, generalmente un Data Warehouse. Uno de los principales retos durante esta fase es identificar correctamente los datos nuevos y los actualizados, para evitar duplicaciones o pérdidas de información. Los registros se clasifican entre filas nuevas, que deben insertarse, y filas existentes, que requieren actualización. Muchas herramientas ETL modernas facilitan esta tarea mediante predicados de lenguaje o reglas de integración específicas. Durante la carga, también se gestionan aspectos técnicos como los segmentos de rollback y los archivos de registro, para mantener la integridad de los datos ante posibles fallos o interrupciones. Habitualmente, antes de su carga definitiva en el Data Warehouse, los datos pasan por un área de staging, donde se realizan validaciones finales y preparaciones específicas.
              figure
                img(src='@/assets/curso/temas/tema3/img5.png', alt='Texto que describa la imagen')
    separador

    #t_3_2.titulo-segundo.color-acento-contenido(data-aos="flip-up")
      h2 3.2 Preparación de datos para modelos de aprendizaje automático
    .row.justify-content-center.align-items-center.mb-5
      .col-lg-5
        figure
          img(src='@/assets/curso/temas/tema3/img6.png', alt='Texto que describa la imagen')
      .col-lg-7
        .cajon.color-primario.p-4.mb-4
          p El aprendizaje automático se define como un subcampo de la informática que se centra en el diseño y desarrollo de algoritmos capaces de aprender patrones a partir de datos, sin necesidad de ser programados de manera explícita (Maltby, 2011). Para que los modelos de aprendizaje automático sean efectivos, precisos y logren generalizar adecuadamente a datos no vistos, resulta esencial realizar una preparación cuidadosa de los datos.
        p El objetivo principal de la preparación de datos es facilitar el trabajo de los algoritmos de modelado, eliminando inconsistencias, reduciendo el ruido y destacando la información relevante. Este proceso implica la aplicación de diversas metodologías y técnicas, como Data Assay, PIE (#[i Prepared Information Environment]), PIE-O (#[i Prepared Information Environment Output]) y métodos de consistencia de datos, ya abordados en este programa de formación complementaria.
    p La preparación de datos es un proceso meticuloso que incluye comprender a fondo las características del conjunto de datos, evaluar su calidad, aplicar transformaciones específicas que se adecuen al algoritmo de modelado seleccionado y garantizar la coherencia en todos los subconjuntos de datos (entrenamiento, validación y prueba). El resultado esperado es obtener datos limpios, relevantes y en un formato óptimo para el desarrollo de modelos predictivos sólidos.
    p.mb-4 En términos generales, la preparación de datos para el aprendizaje automático sigue los siguientes pasos:
    .row.justify-content-center.align-items-center.mb-5
      .col-lg-12
        SlyderF.mb-5(columnas="col-lg-6 col-xl-4")
          .tarjeta.tarjeta--BG01.color-primario.p-4
            .row.justify-content-center.mb-3
              .col-6
                img(src='@/assets/curso/temas/tema3/img7.svg' alt='AvatarTop')
            h5.text-center Análisis del problema
            p Comprender el objetivo del proyecto, los tipos de predicciones requeridas y las características de los datos disponibles.
          .tarjeta.tarjeta--BG01.color-primario.p-4
            .row.justify-content-center.mb-3
              .col-6
                img(src='@/assets/curso/temas/tema3/img8.svg' alt='AvatarTop')
            h5.text-center Selección del modelo de IA
            p Elegir el algoritmo más adecuado (como regresión, clasificación, clustering, redes neuronales o árboles de decisión) de acuerdo con la naturaleza del problema y la estructura de los datos.
          .tarjeta.tarjeta--BG01.color-primario.p-4
            .row.justify-content-center.mb-3
              .col-6
                img(src='@/assets/curso/temas/tema3/img9.svg' alt='AvatarTop')
            h5.text-center Ingeniería de características
            p Crear o seleccionar variables relevantes que representen adecuadamente el problema para mejorar el desempeño del algoritmo.
          .tarjeta.tarjeta--BG01.color-primario.p-4
            .row.justify-content-center.mb-3
              .col-6
                img(src='@/assets/curso/temas/tema3/img10.svg' alt='AvatarTop')
            h5.text-center Entrenamiento del modelo
            p Ajustar los parámetros internos del modelo utilizando el conjunto de entrenamiento, buscando que el modelo aprenda patrones útiles.
          .tarjeta.tarjeta--BG01.color-primario.p-4
            .row.justify-content-center.mb-3
              .col-6
                img(src='@/assets/curso/temas/tema3/img11.svg' alt='AvatarTop')
            h5.text-center Evaluación del modelo
            p Medir el desempeño utilizando conjuntos de validación o prueba mediante métricas específicas como precisión, recall, F1-score o AUC.
          .tarjeta.tarjeta--BG01.color-primario.p-4
            .row.justify-content-center.mb-3
              .col-6
                img(src='@/assets/curso/temas/tema3/img12.svg' alt='AvatarTop')
            h5.text-center Ajuste de hiperparámetros (#[I Hyperparameter Tuning])
            p Optimizar configuraciones como la tasa de aprendizaje, la profundidad de árboles o el número de capas en redes neuronales, con el fin de maximizar el rendimiento del modelo.
  

    p La preparación de datos resulta particularmente crítica en aplicaciones de analítica predictiva, donde se utilizan modelos estadísticos y algoritmos de aprendizaje automático para detectar patrones en datos históricos y anticipar comportamientos y tendencias futuras (Zakir, 2015).
    p Una adecuada preparación de los datos no solo mejora el desempeño de los modelos, sino que también minimiza el riesgo de sobreajuste y maximiza la capacidad del modelo para ofrecer predicciones precisas en escenarios reales.



    separador
    #t_3_3.titulo-segundo.color-acento-contenido(data-aos="flip-up")
      h2 3.3 Diseño de modelos de datos para algoritmos de inteligencia artificial y aprendizaje automático
    p Posteriormente, es posible incorporar técnicas de automatización, como el AutoML, que permiten automatizar fases específicas del diseño, tales como la selección de modelos, el ajuste de hiperparámetros y la evaluación, acelerando el proceso de desarrollo de soluciones de IA.
    p A pesar de la existencia de herramientas que automatizan muchas de estas etapas, la intervención y supervisión de expertos sigue siendo indispensable para interpretar adecuadamente los resultados y garantizar la validez y aplicabilidad del modelo en contextos reales.

    .BG_02.p-5
      .row.justify-content-center.align-items-center
        .col-lg-10
          PasosA.color-acento-contenido.mb-5(tipo="l")
            .row(titulo="")
              .col-md-6.mb-4.mb-md-0
                h4 Análisis del problema
                p Comprender el objetivo del proyecto, los tipos de predicciones requeridas y las características de los datos disponibles.
              .col-md-6
                figure
                  img(src='@/assets/curso/temas/tema3/img13.png', alt='Texto que describa la imagen')

            .row(titulo="")
              .col-md-6
                figure
                  img(src='@/assets/curso/temas/tema3/img14.png', alt='Texto que describa la imagen')
              .col-md-6.mb-4.mb-md-0
                h4 Selección del modelo de IA
                p Elegir el algoritmo más adecuado (como regresión, clasificación, clustering, redes neuronales o árboles de decisión) de acuerdo con la naturaleza del problema y la estructura de los datos.
            .row(titulo="")
              .col-md-6.mb-4.mb-md-0
                h4 Ingeniería de características
                p Crear o seleccionar variables relevantes que representen adecuadamente el problema para mejorar el desempeño del algoritmo.
              .col-md-6
                figure
                  img(src='@/assets/curso/temas/tema3/img15.png', alt='Texto que describa la imagen')
            .row(titulo="")
              .col-md-6
                figure
                  img(src='@/assets/curso/temas/tema3/img16.png', alt='Texto que describa la imagen')
              .col-md-6.mb-4.mb-md-0
                h4 Entrenamiento del modelo
                p Ajustar los parámetros internos del modelo utilizando el conjunto de entrenamiento, buscando que el modelo aprenda patrones útiles.
            .row(titulo="")
              .col-md-6.mb-4.mb-md-0
                h4 Evaluación del modelo
                p Medir el desempeño utilizando conjuntos de validación o prueba mediante métricas específicas como precisión, recall, F1-score o AUC.
              .col-md-6
                figure
                  img(src='@/assets/curso/temas/tema3/img17.png', alt='Texto que describa la imagen')
            .row(titulo="")
              .col-md-6
                figure
                  img(src='@/assets/curso/temas/tema3/img18.png', alt='Texto que describa la imagen')
              .col-md-6.mb-4.mb-md-0
                h4 Ajuste de hiperparámetros (#[i Hyperparameter Tuning])
                p Optimizar configuraciones como la tasa de aprendizaje, la profundidad de árboles o el número de capas en redes neuronales, con el fin de maximizar el rendimiento del modelo.
    p Posteriormente, es posible incorporar técnicas de automatización, como el AutoML, que permiten automatizar fases específicas del diseño, tales como la selección de modelos, el ajuste de hiperparámetros y la evaluación, acelerando el proceso de desarrollo de soluciones de IA.
    p A pesar de la existencia de herramientas que automatizan muchas de estas etapas, la intervención y supervisión de expertos sigue siendo indispensable para interpretar adecuadamente los resultados y garantizar la validez y aplicabilidad del modelo en contextos reales.

    separador
    #t_3_4.titulo-segundo.color-acento-contenido(data-aos="flip-up")
      h2 3.4 #[i Pipelines] de procesamiento de datos
    p.mb-4 En el ámbito del procesamiento de datos, un pipeline es un flujo organizado que transporta los datos a través de varias etapas de procesamiento, transformando datos sin procesar en información valiosa o conocimientos útiles. Cada fase cumple una tarea específica, utilizando el resultado de la etapa anterior como entrada. Se podría afirmar que son una serie de procesos interconectados que transportan y transforman datos desde sus fuentes originales hasta un destino final, como un almacén de datos, un sistema de análisis o una aplicación de inteligencia artificial (Almeida, 2013).
    .row.justify-content-center.align-items-center.mb-5
      .col-lg-4
        figure
          img(src='@/assets/curso/temas/tema3/img19.svg', alt='Texto que describa la imagen')
      .col-lg-6
        p La implementación de un #[i pipeline] generalmente involucra los siguientes pasos:
        ul.lista-ul--color
          li
            i.fas.fa-angle-right
            | Identificación de fuentes de datos.
          li
            i.fas.fa-angle-right
            | Selección de datos relevantes.
          li
            i.fas.fa-angle-right
            | Extracción de los datos.
          li
            i.fas.fa-angle-right
            | Preparación de los datos.
          li
            i.fas.fa-angle-right
            | Carga de los datos.
          li
            i.fas.fa-angle-right
            | Modelado y análisis de los datos.
          li
            i.fas.fa-angle-right
            | Evaluación e interpretación.
          li
            i.fas.fa-angle-right
            | Automatización y monitoreo.
    
    .tarjeta.tarjeta--BG03.p-4.mb-5(data-aos="zoom-in")
      SlyderA(tipo="b" data-aos="zoom-in")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Recolección de datos (#[i Data Collection])
            p Obtener información sobre el comportamiento y perfil de los aprendices. A continuación, se presentan las fuentes típicas:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Logs de interacción de la plataforma (Moodle, Canvas, etc.).
              li
                i.fas.fa-angle-right
                | Tiempo de conexión y actividad en la plataforma.
              li
                i.fas.fa-angle-right
                | Participación en foros, chats, videollamadas.
              li
                i.fas.fa-angle-right
                | Envío de evidencias y resultados de evaluaciones.
              li
                i.fas.fa-angle-right
                | Datos demográficos (edad, género, país y nivel educativo).
              li
                i.fas.fa-angle-right
                | Encuestas iniciales o de satisfacción.
              li
                i.fas.fa-angle-right
                | Datos de navegación (rutas de clics, páginas visitadas, etc.).

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img20.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Ingesta y almacenamiento (#[i Data Ingestion & Storage])
            p consolidar y almacenar los datos para su posterior análisis. A continuación, se presentan las herramientas:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Extracción mediante API o exportación de logs (CSV y JSON).
              li
                i.fas.fa-angle-right
                | Bases de datos SQL (PostgreSQL y MySQL) o NoSQL (MongoDB).
              li
                i.fas.fa-angle-right
                | Sistemas de almacenamiento en la nube (Google BigQuery, AWS S3 y Azure).

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img21.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Limpieza de datos (#[i Data Cleaning])
            p Eliminar inconsistencias y preparar datos confiables. A continuación, se presentan los procesos clave:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Imputación de valores nulos o ausentes.
              li
                i.fas.fa-angle-right
                | Eliminación de registros duplicados.
              li
                i.fas.fa-angle-right
                | Homogeneización de formatos de fecha, texto y numeración.
              li
                i.fas.fa-angle-right
                | Corrección de etiquetas o errores ortográficos.
              li
                i.fas.fa-angle-right
                | Identificación y manejo de outliers (por ejemplo, sesiones extremadamente largas).

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img22.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Integración de datos (#[i Data Integration])
            p Unir datos desde diversas fuentes. A continuación, se presentan las acciones típicas:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Unión por identificador único (ID de aprendiz o correo institucional).
              li
                i.fas.fa-angle-right
                | Alineación temporal de eventos de aprendizaje.
              li
                i.fas.fa-angle-right
                | Integración de datos históricos y contextuales (por ejemplo, historial académico).

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img23.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Transformación y enriquecimiento #[i (Data Transformation & Enrichment)]
            p Crear variables significativas para el modelo. A continuación, se presentan las variables derivadas útiles:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Número de días sin conexión.
              li
                i.fas.fa-angle-right
                | Porcentaje de actividades completadas.
              li
                i.fas.fa-angle-right
                | Participación en foros (% de mensajes enviados respecto al total).
              li
                i.fas.fa-angle-right
                | Tendencia de calificaciones (ascendente o descendente).
              li
                i.fas.fa-angle-right
                | Ratio de abandono previo.
              li
                i.fas.fa-angle-right
                | Tiempo promedio de sesión.

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img24.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Selección de características (#[i Feature Selection])
            p Identificar las variables más predictivas del abandono. A continuación, se presentan los métodos aplicados:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Análisis de correlación (Pearson o Spearman).
              li
                i.fas.fa-angle-right
                | Pruebas estadísticas (Chi-cuadrado para variables categóricas).
              li
                i.fas.fa-angle-right
                | Importancia de variables mediante modelos de árbol ([i Random Forest o XGBoost]).
              li
                i.fas.fa-angle-right
                | Eliminación de variables redundantes o poco informativas.

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img25.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  División del dataset (#[i Train/Test Split])
            p Preparar los datos para el entrenamiento y validación del modelo. A continuación, se presentan las estrategias:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | División típica: 70 % entrenamiento / 30 % prueba.
              li
                i.fas.fa-angle-right
                | Validación cruzada (K-Fold) para mayor robustez.
              li
                i.fas.fa-angle-right
                | Estratificación para mantener la proporción de clases (abandono vs. no abandono).

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img26.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Entrenamiento del modelo: aplicar algoritmos de clasificación supervisada
            p A continuación, se presentan los modelos recomendados:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Regresión Logística (modelo base).
              li
                i.fas.fa-angle-right
                | #[I Random Forest].
              li
                i.fas.fa-angle-right
                | #[i Gradient Boosting (XGBoost y LightGBM)].
              li
                i.fas.fa-angle-right
                | Redes neuronales simples (si existe suficiente volumen de datos).

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img27.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Evaluación del modelo (#[i Model Evaluation])
            p Verificar el desempeño predictivo del modelo. A continuación, se presentan las métricas clave:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | Accuracy: porcentaje de predicciones correctas.
              li
                i.fas.fa-angle-right
                | Precision: proporción de predicciones positivas correctas.
              li
                i.fas.fa-angle-right
                | Recall: proporción de casos reales positivos correctamente detectados.
              li
                i.fas.fa-angle-right
                | F1-Score: balance entre precisión y recall.
              li
                i.fas.fa-angle-right
                | ROC-AUC: capacidad del modelo para diferenciar entre abandono y no abandono (especialmente relevante cuando las clases están desbalanceadas).
              li
                i.fas.fa-angle-right
                | Matriz de confusión para visualización de errores.

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img28.png' alt="Imagen decorativa")
        .row.justify-content-center
          .col-lg-7.order-lg-1.order-2
            h4  Despliegue y monitoreo
            p Usar el modelo en producción para alertas tempranas de riesgo. A continuación, se presentan las opciones de despliegue:
            ul.lista-ul
              li
                i.fas.fa-angle-right
                | API REST con Flask o FastAPI para integración con el LMS.
              li
                i.fas.fa-angle-right
                | Dashboard de visualización (Power BI, Streamlit o Dash).
              li
                i.fas.fa-angle-right
                | Automatización del reentrenamiento periódico (por cohorte o semestre).
              li
                i.fas.fa-angle-right
                | Generación de alertas automáticas para instructores.
              li
                i.fas.fa-angle-right
                | Monitoreo de drift de datos: detección de cambios en los patrones de los datos para actualizar el modelo cuando sea necesario.

          .col-lg-5.col-10.order-lg-2.order-1.mb-lg-0.mb-4
            img(src='@/assets/curso/temas/tema3/img29.png' alt="Imagen decorativa")

    p.mb-4 A continuación, se presenta un caso de uso de un proyecto en el cual se pretende diseñar un modelo de aprendizaje automático para la predicción de abandono de aprendices en plataformas de educación virtual:
    p En resumen, un pipeline de datos es un camino establecido para el movimiento y transformación de datos, desde su origen hasta un punto de destino donde pueden ser utilizados para análisis, generación de informes o aplicaciones de IA. Su implementación incluye fases de extracción, preparación, carga y análisis, con un enfoque creciente en la automatización para mejorar la eficiencia y garantizar la adaptabilidad de los modelos a cambios futuros en los datos.

</template>

<script>
export default {
  name: 'Tema3',
  data: () => ({
    // variables de vue
  }),
  mounted() {
    this.$nextTick(() => {
      this.$aosRefresh()
    })
  },
  updated() {
    this.$aosRefresh()
  },
}
</script>

<style lang="sass"></style>
