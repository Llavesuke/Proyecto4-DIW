# EVALUACIÓN ESTANDARES WEB

El proyecto que analizare sera Shibuya Station de mi propia autoría

## ESTANDARES UTILIZADOS

Los estandares usados para este proyecto son:

> [!NOTE]
> HTML
> CSS

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

### JavaScript

1. Separación entre lógica y presentación


