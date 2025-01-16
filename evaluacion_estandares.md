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
