# Fixa komponenten (Utmaning)

## Mål

Öva på att hitta och fixa vanliga fel med components, props och importer.

## Förkunskaper

- [Components och props](../../documents/02-components-props.md)
- [Props](05-props.md)

## Instruktioner

Koden nedan har flera fel. Kopiera in filerna i ditt projekt, läs felmeddelandena i terminalen och webbläsaren, och fixa ett fel i taget.

**`src/App.jsx`:**

```jsx
import greeting from "./Greeting"
import UserCard from "./userCard"

function App() {
  return (
    <div>
      <greeting name="Anna" />
      <UserCard name="Erik" age="30" />
      <UserCard name="Sara" />
    </div>
  )
}

export default App
```

**`src/Greeting.jsx`:**

```jsx
function Greeting(name) {
  return <h1>Hej, {name}!</h1>
}
```

**`src/UserCard.jsx`:**

```jsx
import React from "react"

function UserCard({ name, age }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Ålder: {age}</p>
    </div>
  )
}
```

1. Kopiera in de tre filerna i `src/`.
2. Starta appen — du kommer se fel.
3. Fixa ett fel i taget. Det finns minst **5 fel** att hitta.
4. Verifiera att appen renderar korrekt: en hälsning och två användarkort (Sara ska visa "Ålder: Ej angiven").

## Förväntat resultat

En sida som visar "Hej, Anna!", ett kort för Erik (ålder 30) och ett kort för Sara (ålder "Ej angiven"). Inga fel i konsolen.

## Tips

<details>
<summary>Ledtråd 1</summary>

Tänk på: default export vs named export, filnamn i importer (skiftlägeskänsligt), att props är ett objekt, och att components måste börja med stor bokstav i JSX.

</details>

<details>
<summary>Ledtråd 2</summary>

Felen:

1. `Greeting` saknar `export default`
2. `greeting` ska vara `Greeting` i JSX (stor bokstav) och i importen
3. Importen `"./userCard"` matchar inte filnamnet `UserCard.jsx` (skiftläge)
4. `Greeting` tar emot `name` direkt istället för `{ name }` (destrukturering)
5. `UserCard` saknar default-värde för `age`

</details>
