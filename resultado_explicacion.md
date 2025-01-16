![image](https://github.com/user-attachments/assets/e3a65f6a-0a7f-4152-ad62-9de9e14e34f3)# Pruebas de usabilidad y velocidad con herramientas automáticas

# WebPageTest


![Screenshot from 2025-01-16 18-34-35](https://github.com/user-attachments/assets/215c3f0a-2806-4b37-b56b-e95530718eaa)
*Chrome*

![Screenshot from 2025-01-16 18-38-56](https://github.com/user-attachments/assets/0d462adb-1dd2-4b22-b139-012804273046)
*Edge*

Como se puede ver los dos tienen rendimientos muy parecido ya que al fin y al cabo Edge esta basado en una versión de código libre de Chrome (Chromium), lo más destacable es en la diferencia de 
Total Blocking Time donde en la versión de Chrome tarda 0.41 segundos mientras que en Edge ha tardado 0 segundos

## Navegacion - WebPageTest

- **Listado**

![Screenshot from 2025-01-16 18-59-12](https://github.com/user-attachments/assets/ff64b670-7fbf-4410-bf2f-2e1ccab4940b)
*Móvil*

![Screenshot from 2025-01-16 19-02-53](https://github.com/user-attachments/assets/9bce2349-f455-461b-a923-fccad34e5bbf)
*Escritorio*

La diferencia más notable es que en la versión de móvil hay algunos apartados que tienen un rendimiento mejorable, marcandolo con colores amarillos y rojos mientras que en la versión de escritorio todo se puede ver con buenos tiempos representandolo con el color verde. Para ser más concreto esta gran diferencia se ha analizado en los apartados de Largest Contentful Paint y Total Blocking Time.

- **Producto**

![Screenshot from 2025-01-16 19-11-11](https://github.com/user-attachments/assets/eaa29faf-c6df-4e6d-bbcf-89c747e99552)
*Móvil*

![Screenshot from 2025-01-16 19-09-19](https://github.com/user-attachments/assets/af279aa4-db90-4ebf-b25a-5ea262ad86fc)
*Escritorio*

La diferencia entre ambos dispositivos es abismal. Mientras que en escritorio goza de un rendimiento decente en el dispositivo móvil el rendimiento es paupérrimo, teniendo tres apartados en color rojo para dar el aviso de que son marcas malas. Lo más llamativo es que el Largest Contentful Paint ha tardado 11 segundos mientras que en escritorio solo tardo algo menos de 1 segundo en cargarlo.

---

## PageSpeed Insights

- **Home**
![Screenshot from 2025-01-16 19-14-21](https://github.com/user-attachments/assets/c80e940f-22c9-43fe-9aa2-df743620765b)
*Móvil*

En la versión móvil, los tiempos de carga también son aceptables, pero todavía hay áreas que necesitan optimización para mejorar la experiencia del usuario. El puntaje de rendimiento es bajo, principalmente debido a algunos recursos que bloquean el renderizado inicial, como los archivos de fuentes de Google desde el CDN, que afectan negativamente al First Contentful Paint (FCP) y Largest Contentful Paint (LCP).

A pesar de tener buenos puntajes en SEO y Buenas Prácticas, se recomienda optimizar el uso de las fuentes, así como revisar el tamaño y formato de las imágenes, para evitar tiempos de carga innecesarios. También es importante trabajar en la reducción de JavaScript no utilizado y mejorar la política de caché de los recursos estáticos, lo que podría resultar en una experiencia móvil mucho más rápida y fluida.

![Screenshot from 2025-01-16 19-13-53](https://github.com/user-attachments/assets/6710fe4a-b784-45ce-b0c7-17f2486593ab)
*Escritorio*

Según el informe de PageSpeed Insights, los tiempos en la versión de escritorio son bastante buenos, con notas muy altas, aunque hay margen de mejora en algunas áreas. El principal problema identificado es el uso de un CDN para importar las fuentes de Google, lo que bloquea el primer renderizado de la página y provoca un retraso considerable.

Para mejorar el rendimiento, es recomendable trabajar en la optimización de estos recursos que afectan el renderizado inicial, como el uso de fuentes, imágenes y JavaScript. Además, hay otros aspectos menores, como el tamaño de las imágenes, que podrían reducirse, y se podría mejorar la política de caché para los recursos estáticos.


- **Listado**

![Screenshot from 2025-01-16 19-23-12](https://github.com/user-attachments/assets/a3699f2e-83d5-4316-b797-d14ed9238cbb)
*Móvil*
En la versión móvil, el rendimiento presenta algunas áreas de mejora, con tiempos como el First Contentful Paint (FCP) en 5.0 segundos y el Largest Contentful Paint (LCP) en 14.4 segundos, lo que sugiere que la página puede beneficiarse de optimizaciones para acelerar la carga. Aunque la puntuación de SEO y Buenas Prácticas es decente, la puntuación de Accesibilidad y Rendimiento muestran que aún se puede mejorar la experiencia del usuario.

Uno de los problemas más graves se encuentra en el bloqueo del renderizado inicial debido a recursos como JavaScript y CSS, lo que retrasa la carga en más de 1 segundo. Optimizar estos recursos, por ejemplo, eliminando los que no son esenciales para el primer renderizado, puede ahorrar bastatante tiempo.

Además, las imágenes tienen un papel importante en el rendimiento. Utilizar formatos más eficientes como WebP podría reducir el tamaño de las imágenes en unos 18,069 KiB, mientras que definir un tamaño adecuado y optimizar la codificación podría ahorrar aún más. También es recomendable reducir el JavaScript no utilizado y minificar los archivos para reducir el tamaño general de los recursos y acelerar la carga.

![Screenshot from 2025-01-16 19-22-52](https://github.com/user-attachments/assets/d0b52a2f-a34a-47a2-8e1a-1ce6bebfb803)
*Escritorio*

En la versión de escritorio, el rendimiento es bastante sólido, con un First Contentful Paint (FCP) rápido de 0.7 segundos y un Largest Contentful Paint (LCP) de 2.7 segundos. Pero, existen áreas clave donde se puede mejorar aún más la velocidad y la eficiencia.

Uno de los aspectos a optimizar es el uso de imágenes, ya que se podrían servir en formatos más modernos, lo que podría ahorrar hasta 17,730 KiB de datos. Además, se recomienda eliminar recursos que bloquean el renderizado inicial, lo cual podría mejorar el tiempo de carga en unos 260 ms.

Otro punto a revisar es el JavaScript: reducir el código no utilizado y minificar los archivos podría generar una mejora en el rendimiento, al ahorrar alrededor de 67 KiB y 20 KiB respectivamente. También sería útil definir explícitamente el tamaño de las imágenes, lo que evitaría posibles problemas de rendimiento y layout.

- **Producto**

![Screenshot from 2025-01-16 19-27-40](https://github.com/user-attachments/assets/6cc2bc23-1d7b-4af4-b0a1-b146e0d0d576)
*Móvil*

En la versión móvil, el rendimiento de la página es bastante bajo, lo que impacta negativamente en la experiencia del usuario. El First Contentful Paint (FCP), que mide el tiempo hasta que se muestra el primer contenido visual, es de 2.5 segundos, lo que es relativamente lento. Por otro lado, el Largest Contentful Paint (LCP), que mide el tiempo hasta que se carga el elemento más grande visible, es aún más lento, con 13.2 segundos. Esto indica que la página tarda mucho en cargarse, lo que puede generar frustración en los usuarios.

Además, la Total Blocking Time (TBT) es de 1,550 ms, lo que significa que hay una cantidad significativa de tiempo en el que los usuarios no pueden interactuar con la página debido a procesos bloqueantes. Esto, junto con un Cumulative Layout Shift (CLS) de 0.227, que indica que los elementos de la página se mueven de manera inesperada durante la carga, empeora aún más la experiencia, ya que los usuarios pueden sentir que la página es inestable.

Uno de los problemas principales es que el trabajo en el hilo principal está tomando 7.1 segundos, lo que retrasa aún más la carga y hace que la página responda más lentamente cuando el usuario intenta interactuar con ella. También se han detectado varios layout shifts, lo que contribuye a que el diseño de la página se mueva mientras se carga, creando una experiencia poco agradable.

![Screenshot from 2025-01-16 19-27-11](https://github.com/user-attachments/assets/2f4e84d6-17fc-4114-96ce-ea2260a0a141)
*Escritorio*

En la versión de escritorio, el rendimiento no es el mejor posible, aunque el First Contentful Paint (FCP) de 0.7 segundos es bastante bueno, el Largest Contentful Paint (LCP) de 3.0 segundos y un Total Blocking Time (TBT) de 3,250 ms indican que aún hay áreas importantes por mejorar. Estos valores sugieren que, aunque el contenido inicial carga relativamente rápido, la página tarda más en completarse y el hilo principal está muy bloqueado, lo que afecta la interactividad de la página. El Speed Index (SI) de 4.2 segundos también indica que el tiempo total de carga podría mejorar considerablemente.

Un problema principal es el tiempo que se está utilizando el hilo principal, que llega a 8.6 segundos. Este retraso afecta tanto a la carga como a la interactividad de la página. Además, hay recursos que bloquean el renderizado (como ciertos scripts) que podrían optimizarse, lo que permitiría reducir el tiempo de carga en aproximadamente 300 ms.

Otro punto importante son las imágenes, que no están optimizadas para los formatos más modernos. Al cambiar a formatos de próxima generación, como WebP, se podrían reducir hasta 1,613 KiB. También se detectaron oportunidades para mejorar el código JavaScript, ya que se puede eliminar código no utilizado (lo que ahorraría hasta 65 KiB) y realizar una minificación de los archivos JavaScript para reducirlos en 19 KiB.

---

## Optimización con LightHouse

![image](https://github.com/user-attachments/assets/6c7b30af-4be0-4eed-a4c2-bc5cf0eeedda)

El informe de Lighthouse muestra que aunque el rendimiento en general es bastante bueno con una puntuación de 98 en rendimiento hay algunas áreas que podrían optimizarse para mejorar aún más la velocidad y la experiencia del usuario. A continuación, se detallan los resultados de los parámetros evaluados y las recomendaciones para optimizar cada uno:
1. First Contentful Paint (FCP) - 0.7s

    Análisis: El tiempo que tarda en mostrar el primer contenido visual es muy rápido (0.7 segundos).
    Recomendación: Eliminar los recursos que bloquean el renderizado, como los scripts CSS o JavaScript no esenciales, que podrían retrasar aún más la visualización inicial. Lo que podría ahorrar hasta 310 ms.

2. Largest Contentful Paint (LCP) - 1.0s

    Análisis: El LCP mide el tiempo que tarda en renderizarse el elemento más grande visible, en este caso son 1.0 segundos. 
    Recomendación: Minimizar el tamaño de las imágenes, optimizar la codificación de las mismas, y usa formatos como WebP o AVIF para reducir su tamaño. Este cambio puede ahorrar hasta 10,874 KiB en la carga de imágenes.

3. Total Blocking Time (TBT) - 0ms

    Análisis: No se ha detectado ningun bloqueo durante la carga de la página. La página responde rápidamente a las interacciones del usuario.
    Recomendación: Manténer el código JavaScript optimizado y dividido adecuadamente para seguir teniendo estos buenos resultados

4. Cumulative Layout Shift (CLS) - 0.018

    Análisis: El CLS mide la estabilidad visual del sitio durante la carga. El valor es de 0.018. 
    Recomendación: Asegurarse de que todos los elementos de la página tengan un tamaño de contenedor especificado para evitar cualquier cambio inesperado en el diseño.

5. Speed Index (SI) - 0.8s

    Análisis: El Speed Index es basicamente la rapidez con la que se renderiza todo el contenido visible. En la página de Shibuya Station es de 0.8 segundos.
    Recomendación: Estar atento de que ningun script bloquee el hilo principal

Áreas de Mejora:

  Eliminar Recursos que Bloquean el Renderizado:
    Mover los scripts y recursos no esenciales al final de la carga o de usar los atributos async o defer en las etiquetas <script>, lo que puede ahorrar hasta 310 ms.

  Reducir JavaScript No Utilizado:
    Revisar los archivos JavaScript y elimina cualquier código no utilizado que se esté cargando, ya que se puede ahorrar hasta 56 KiB.

  Servir Imágenes en Formatos de Próxima Generación:
    Cambiar a formatos de imágenes como WebP puede reducir el tamaño de las imágenes hasta 10,874 KiB, lo que acelerará la carga de la página

  Tamaño Adecuado de Imágenes:
    Revisar el tamaño de las imágenes para que coincidan con las dimensiones necesarias en la página. Este ajuste puede ahorrar hasta 17,584 KiB.

  Optimizar la Codificación de Imágenes:
    Comprimir las imágenes de manera eficiente usando herramientas como TinyPNG o ImageOptim para reducir el tamaño sin perder calidad. Esto podría ahorrar hasta 5,612 KiB.
