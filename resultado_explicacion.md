# Pruebas de usabilidad y velocidad con herramientas automáticas

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

## PageSpeed Insights

- **Home**
![Screenshot from 2025-01-16 19-14-21](https://github.com/user-attachments/assets/c80e940f-22c9-43fe-9aa2-df743620765b)
*Móvil*

En la versión móvil, los tiempos de carga también son aceptables, pero todavía hay áreas que necesitan optimización para mejorar la experiencia del usuario. El puntaje de rendimiento es bajo, principalmente debido a algunos recursos que bloquean el renderizado inicial, como los archivos de fuentes de Google desde el CDN, que afectan negativamente al First Contentful Paint (FCP) y Largest Contentful Paint (LCP).

A pesar de tener buenos puntajes en SEO y Buenas Prácticas, se recomienda optimizar el uso de las fuentes, así como revisar el tamaño y formato de las imágenes, para evitar tiempos de carga innecesarios. También es importante trabajar en la reducción de JavaScript no utilizado y mejorar la política de caché de los recursos estáticos, lo que podría resultar en una experiencia móvil mucho más rápida y fluida.

![Screenshot from 2025-01-16 19-13-53](https://github.com/user-attachments/assets/6710fe4a-b784-45ce-b0c7-17f2486593ab)
*Escritorio*

Según el informe de PageSpeed Insights, los tiempos en la versión de escritorio son bastante buenos, con calificaciones muy altas, aunque hay margen de mejora en algunas áreas. El principal problema identificado es el uso de un CDN para importar las fuentes de Google, lo que bloquea el primer renderizado de la página y provoca un retraso considerable.

Para mejorar el rendimiento, se recomienda trabajar en la optimización de estos recursos que afectan el renderizado inicial, como el uso de fuentes, imágenes y JavaScript. Además, hay otros aspectos menores, como el tamaño de las imágenes, que podrían reducirse, y se podría mejorar la política de caché para los recursos estáticos.


- **Listado**

![Screenshot from 2025-01-16 19-23-12](https://github.com/user-attachments/assets/a3699f2e-83d5-4316-b797-d14ed9238cbb)
*Móvil*


![Screenshot from 2025-01-16 19-22-52](https://github.com/user-attachments/assets/d0b52a2f-a34a-47a2-8e1a-1ce6bebfb803)
*Escritorio*

