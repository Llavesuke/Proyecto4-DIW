# EVALUACIÓN ESTANDARES WEB

El proyecto que analizare sera Shibuya Station de mi propia autoría

## ESTANDARES UTILIZADOS

Los estandares usados para este proyecto son:

> [!NOTE]
> HTML
> 
> CSS
> 
> JavaScript

## INDICE
---

    1. EVALUACIÓN ESTÁNDARES WEB
       1.1. ESTÁNDARES UTILIZADOS
           HTML
           CSS
           JavaScript
    2. FACILIDAD DE NAVEGACIÓN
       2.1. Ratón
       2.2. Teclado
       2.3. Pantalla táctil
    3. WebPageTest
       3.1. Navegación - WebPageTest
           Listado
           Producto
    4. PageSpeed Insights
       4.1. Home
       4.2. Listado
       4.3. Producto
    5. Optimización con LightHouse
    6. Ghost Inspector
    7. REFLEXIONES FINALES

### HTML

1. Estructura semántica

```HTML
<main className="notfound">
      <section className="notfound__images">
        <img src="tren.png" alt="Tren" className="notfound__image notfound__image--tren" />
        <img src="inosuke.png" alt="Inosuke" className="notfound__image notfound__image--inosuke" />
        <img src="shibuya-text.png" alt="Shibuya Text" className="notfound__image notfound__image--shibuya" />
      </section>
      <section className="notfound__overlay">
        <h1 className="notfound__title">404</h1>
        <p className="notfound__subtitle">You are doomed</p>
        <button className="notfound__button" onClick={handleGoHome}>GO HOME</button>
      </section>
</main>
```
Como se puede ver en el ejemplo del código, utiliza etiquetas semánticas facilitando asi la compresión de la estructura de la web.

2. Atributos accesibles

```HTML
<nav className="navbar">
      <ul>
        <li>
          <NavLink to="/" className="navbar__link">
            <img alt="Train logo" className="link__logo" src="/Train-icon.svg"/>
            <span className="link__vector"></span>
            <p className="link__title">SHIBUYA STATION</p>
          </NavLink>
 </li>
```

Aquí se ve perfectamente como las imágenes tienen su correspondiente atributo alt para que sean descritas con facilidad.

```HTML
<fieldset className="register__group">
              <label htmlFor="username" className="register__label" id="usernameInput">Username:</label>
              <input
                type="text"
                name="username"
                className="register__input"
                value={formData.username}
                onChange={(e) => setFormData({ ...formData, username: e.target.value })}
              />
</fieldset>
```
Se utiliza label y el atributo htmlFor vinculadolo al input mejorando asi la accesibilidad para usuarios con tecnologías de asistencia como lectores de pantalla.


---

### CSS

1. Separación de estilos y contenido

```CSS
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "K2D", sans-serif;
}
```
Todo el CSS de la aplicación se encuentra en un index.css

2. Diseño responsive

```CSS
@media (max-width: 1174px) {
  .search-results {
    width: 90%;
    margin-left: 0.4rem;
  }
}
```
Se puede ver la utilización de media queries y unidades relativas como rem, vh aunque no siempre, en algunas partes se recae en el uso de unidades absolutas como px.

3. Contraste de color

Por ejemplo el color-text: #e2e2b6 cumple el WCAG con el color-background: #2d3748 en 8.25:1 tanto como para textos normales como grandes aunque no todos los colores lo cumplen ya que --color-text-dark: #363636 y
--color-background-darker: #444 no cumplen con el estandar WCAG para textos normales, pero si con textos grandes.

---

### JavaScript

1. Separación entre lógica y presentación


```JS
const handleSubmit = async (e) => {
    e.preventDefault();

    const emailError = checkEmail(formData.email);

    if (emailError) {
      toast.error('Valid email is required', {
        style: {
          backgroundColor: '#003366',
          color: '#E2E2B6',
        },
      });
      return; // Prevents further execution if there is an error
    }

    try {
      await login({
        email: formData.email,
        password: formData.password,
      });

      toast.success('Login successful!', {
        style: {
          backgroundColor: '#003366',
          color: '#E2E2B6',
        },
      });

      console.log("User logged in");

      isUsserLogged(); // Check if the user is logged in

    } catch (error) {
      if (error.code === "auth/invalid-credential") {
        toast.error('Invalid email or password. Please try again', {
          style: {
            backgroundColor: '#003366',
            color: '#E2E2B6',
          },
        });
      }

      console.log(error.code);
      console.log(error.message);
    }
  };

  return (
    <main className="login">
      <section className="login__container">
        <header className="login__header">
          <h2 className="login__title">Welcome Back!</h2>
          <p className="login__subtitle">Please login to your account</p>
...
```
Aunque se utiliza hooks y validaciones, deberían extraerse todas estas funciones a custom hooks y dejar en el componente solo la presentación visual, lo cual no ocurre en casi ningún componente.

2. Manejo de errores

```JS
  useEffect(() => {
    const fetchChapterDetails = async () => {
      try {
        // Fetch chapter details
        const chapterResponse = await axios.get(`https://api.mangadex.org/chapter/${chapterId}`);
        const chapterData = chapterResponse.data.data;
        const title = chapterData.attributes.title || null;
        setChapterTitle(title);

        // Fetch related manga title
        const mangaId = chapterData.relationships.find((rel) => rel.type === 'manga')?.id;
        if (mangaId) {
          const mangaResponse = await axios.get(`https://api.mangadex.org/manga/${mangaId}`);
          const mangaData = mangaResponse.data.data;
          setMangaTitle(mangaData.attributes.title.en || 'Unknown Title');
        }

        // Fetch chapter pages
        const pagesResponse = await axios.get(`https://api.mangadex.org/at-home/server/${chapterId}`);
        const { baseUrl, chapter } = pagesResponse.data;
        const imageUrls = chapter.data.map(
          (filename) => `${baseUrl}/data/${chapter.hash}/${filename}`
        );

        setPages(imageUrls);
      } catch (err) {
        console.error('Error fetching chapter details or pages:', err);
        setError('Failed to load chapter.');
      } finally {
        setLoading(false);
      }
    };
```
Se utiliza try-catch para controlar los errores

---

## Facilidad de navegación

### Ratón
No se encuentran problemas al navegar utilizando el ratón. Los elementos son lo suficientemente grandes y fáciles de clicar. La navegación es clara y directa.

### Teclado
En esta ocasión hay varios problemas al navegar con el teclado entre los que encontramos

> [!WARNING]
> La web no funciona si realizas un zoom pronunciado, se rompe y no es posible navegar por ella.
> 
> Al usar el focus para seleccionar (utilizando el tab) elementos, nos encontramos que no es posible seleccionar los items de los mangas ni se puede acceder de manera correcta a los elementos de la navbar
> 
> Los toasts no son accesibles tampoco, ya que no se puede seleccionar el elemento usando el teclado


### Pantalla táctil

Algunos elementos son difíciles de acceder a través de pantallas táctiles, especialmente en dispositivos con resoluciones más pequeñas. Esto puede mejorar con un diseño más adaptado.


## WebPageTest


![Screenshot from 2025-01-16 18-34-35](https://github.com/user-attachments/assets/215c3f0a-2806-4b37-b56b-e95530718eaa)
*Chrome*

![Screenshot from 2025-01-16 18-38-56](https://github.com/user-attachments/assets/0d462adb-1dd2-4b22-b139-012804273046)
*Edge*

Como se puede ver los dos tienen rendimientos muy similares ya que al fin y al cabo Edge esta basado en una versión de código libre de Chrome (Chromium), lo más destacable es en la diferencia de 
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

1. **First Contentful Paint (FCP) - 0.7s**

    **Análisis:** El tiempo que tarda en mostrar el primer contenido visual es muy rápido (0.7 segundos).
    **Recomendación:** Eliminar los recursos que bloquean el renderizado, como los scripts CSS o JavaScript no esenciales, que podrían retrasar aún más la visualización inicial. Lo que podría ahorrar hasta 310 ms.

2. **Largest Contentful Paint (LCP) - 1.0s**

    **Análisis:** El LCP mide el tiempo que tarda en renderizarse el elemento más grande visible, en este caso son 1.0 segundos. 
    **Recomendación:** Minimizar el tamaño de las imágenes, optimizar la codificación de las mismas, y usa formatos como WebP o AVIF para reducir su tamaño. Este cambio puede ahorrar hasta 10,874 KiB en la carga de imágenes.

3. **Total Blocking Time (TBT) - 0ms**

    **Análisis:** No se ha detectado ningun bloqueo durante la carga de la página. La página responde rápidamente a las interacciones del usuario.
    **Recomendación:** Manténer el código JavaScript optimizado y dividido adecuadamente para seguir teniendo estos buenos resultados

4. **Cumulative Layout Shift (CLS) - 0.018**

    **Análisis:** El CLS mide la estabilidad visual del sitio durante la carga. El valor es de 0.018. 
    **Recomendación:** Asegurarse de que todos los elementos de la página tengan un tamaño de contenedor especificado para evitar cualquier cambio inesperado en el diseño.

5. **Speed Index (SI) - 0.8s**

    **Análisis:** El Speed Index es basicamente la rapidez con la que se renderiza todo el contenido visible. En la página de Shibuya Station es de 0.8 segundos.
    **Recomendación:** Estar atento de que ningun script bloquee el hilo principal

### Áreas de Mejora:

  **Eliminar Recursos que Bloquean el Renderizado:**
    Mover los scripts y recursos no esenciales al final de la carga o de usar los atributos async o defer en las etiquetas <script>, lo que puede ahorrar hasta 310 ms.

  **Reducir JavaScript No Utilizado:**
    Revisar los archivos JavaScript y elimina cualquier código no utilizado que se esté cargando, ya que se puede ahorrar hasta 56 KiB.

  **Servir Imágenes en Formatos de Próxima Generación:**
    Cambiar a formatos de imágenes como WebP puede reducir el tamaño de las imágenes hasta 10,874 KiB, lo que acelerará la carga de la página

  **Tamaño Adecuado de Imágenes:**
    Revisar el tamaño de las imágenes para que coincidan con las dimensiones necesarias en la página. Este ajuste puede ahorrar hasta 17,584 KiB.

  **Optimizar la Codificación de Imágenes:**
    Comprimir las imágenes de manera eficiente usando herramientas como TinyPNG o ImageOptim para reducir el tamaño sin perder calidad. Esto podría ahorrar hasta 5,612 KiB.


Ahora probare con la versión movil 


## Evaluación con Ghost Inspector

Para realizar esta evaluación deberemos registrarnos en [Ghost Inspector](https://ghostinspector.com/) e instalar la [extensión](https://chromewebstore.google.com/detail/ghost-inspector-web-test/aicdiabnghjnejfempeinmnphllefehc) oficial del servicio en nuestro navegador.

Luego de esto, nos vamos a la página que en este caso es Shibuya Station y ejecutamos un nuevo test 
![image](https://github.com/user-attachments/assets/1af90310-d253-4c51-a190-98e3b9d6e2c1)

Ya con esto, solo debemos realizar el flujo crítico de la aplicación, el cual es un usuario que empieza en el home y decide leer un capítulo de un manga.

https://github.com/user-attachments/assets/ef2a5b19-e1f6-4614-a5b7-149648608c25

Y vemos los resultados luego en el dashboard del servicio.
![image](https://github.com/user-attachments/assets/e25301f5-df77-4144-9d24-6469dcb81013)

Como se ve en la captura, no hay ningun error aparente lo que nos conlleva a pensar a que la aplicación al menos en la base de la misma es 100% funcional

Tambien probare esta herramienta con resolución móvil (Iphone X) para ver si encuentra algun problema que no estaba previsto en la versión de escritorio

https://github.com/user-attachments/assets/19ad714b-9b95-45d8-a1a5-12a393a454f5

Ahora mirare los resultados de este test:
![image](https://github.com/user-attachments/assets/f97c5ec1-9273-4197-b501-c93465157688)

Como se ve en la captura, no hay ningún problema aparente en el flujo crítico de los dispositivos móviles.

## Reflexiones finales sobre la usabilidad y navegación del sitio web

Después de analizar la página web "Shibuya Station", puedo destacar varios puntos positivos, aunque también encontré áreas importantes a mejorar. A continuación, detallo mis observaciones divididas por categorías:

### 1. Accesibilidad

   Aspectos positivos:
      Se utilizan etiquetas semánticas como <header>, <main> y <footer>, lo que mejora la comprensión del contenido para tecnologías de asistencia.
        Las imágenes incluyen atributos alt, y los formularios tienen label, lo que es esencial para usuarios con discapacidades visuales.

   Aspectos a mejorar:
      No todos los elementos de la página son navegables con el teclado, como los toasts y algunos menús desplegables.
        Falta optimizar el contraste de colores, ya que algunos textos no cumplen los estándares WCAG, dificultando la lectura en ciertos casos.

### 2. Diseño y experiencia en dispositivos

   Aspectos positivos:
      La página utiliza un diseño responsive basado en media queries y unidades relativas como rem y vh.
        En pantallas grandes, los elementos se ajustan bien y ofrecen una experiencia agradable.

   Aspectos a mejorar:
      En pantallas pequeñas (móviles o tablets), algunos botones y enlaces son difíciles de pulsar.
        Sería ideal simplificar la interfaz en dispositivos táctiles para mejorar la navegación y la usabilidad.

### 3. Rendimiento técnico

   Aspectos positivos:
      En escritorio, la carga de la página es rápida y las métricas como el First Contentful Paint (FCP) y el Largest Contentful Paint (LCP) son aceptables.
        El uso de try-catch en el código JavaScript asegura que la página no se rompa si ocurre algún error.

   Aspectos a mejorar:
      En móviles, el tiempo de carga es demasiado alto, llegando a 11 segundos para cargar el contenido principal. Esto afecta negativamente la experiencia del usuario.
        El código JavaScript podría organizarse mejor, utilizando funciones más pequeñas y específicas, o incluso implementando custom hooks para simplificar la lógica.

### 4. Conclusión

En general, la página web tiene una buena base técnica, pero para ser más inclusiva y eficiente es importante:

   Mejorar la accesibilidad, haciendo que todos los elementos sean navegables con teclado.
   Ajustar el diseño para dispositivos táctiles pequeños y asegurar un mejor contraste de colores.
   Optimizar el rendimiento móvil para reducir los tiempos de carga.
