# Children-propen (Utmaning)

## Mål

Öva på att bygga en wrapper-component med `children` och förstå komposition.

## Förkunskaper

- [Components och props](../../documents/02-components-props.md)
- [Props](05-props.md)

## Instruktioner

1. Skapa en component `Card` i `src/Card.jsx` som tar emot `children`.
2. Componenten ska rendera `children` inuti en `<div className="card">`.
3. Skapa en CSS-fil `src/Card.css` med styling för `.card` (t.ex. border, padding, border-radius, box-shadow).
4. Importera CSS-filen i `Card.jsx`.
5. I `App.jsx`, använd `Card` med olika innehåll:

```jsx
<Card>
  <h2>Rubrik</h2>
  <p>Lite text i kortet.</p>
</Card>

<Card>
  <img src="https://i.pravatar.cc/150" alt="Avatar" />
  <p>En bild i ett kort.</p>
</Card>
```

6. Skapa en till wrapper-component `Section` som tar emot `title` (som prop) och `children`. Den ska rendera en `<section>` med titeln i en `<h2>` och `children` under.

## Förväntat resultat

Flera kort med olika innehåll, alla med samma styling. `Card` bryr sig inte om vad den omsluter — det bestäms av anroparen.

## Tips

<details>
<summary>Ledtråd 1</summary>

```jsx
function Card({ children }) {
  return <div className="card">{children}</div>;
}
```

</details>
