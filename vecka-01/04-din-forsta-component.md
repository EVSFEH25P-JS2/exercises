# Din första component (Grund)

## Mål

Öva på att skapa, exportera och importera en egen component.

## Förkunskaper

- [Components och props](../../documents/02-components-props.md)
- [Skapa en React-app](01-skapa-react-app.md)

## Instruktioner

1. Skapa en ny fil `src/Greeting.jsx`.
2. Skriv en component `Greeting` som returnerar `<h2>Hej från min component!</h2>`.
3. Exportera componenten med `export default`.
4. Öppna `App.jsx`, importera `Greeting` och rendera den.
5. Rendera `Greeting` tre gånger i `App.jsx` och kontrollera att alla tre visas.
6. Skapa ytterligare en component `Footer` i en ny fil `src/Footer.jsx` som renderar `<footer>© 2026</footer>`.
7. Importera och rendera `Footer` i `App.jsx` under dina `Greeting`-components.

## Förväntat resultat

En sida med tre "Hej från min component!"-texter och en footer med copyright-text.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
// Greeting.jsx
function Greeting() {
  return <h2>Hej från min component!</h2>;
}

export default Greeting;
```

</details>
