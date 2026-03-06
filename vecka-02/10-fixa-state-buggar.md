# Fixa state-buggar (Utmaning)

## Mål

Öva på att identifiera och fixa vanliga state-fel i React.

## Förkunskaper

- [State och events](../../documents/03-state-events.md)
- [useState — räknare](01-usestate-raknare.md)
- [Uppdatera objekt i state](09-uppdatera-objekt-i-state.md)

## Instruktioner

Koden nedan innehåller fyra components med vanliga state-buggar. Kopiera in dem i ditt projekt och fixa buggarna en i taget.

```jsx
import { useState } from "react";

// Bugg 1: Räknaren ökar inte korrekt vid snabba klick
function FastCounter() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
    setCount(count + 1);
    setCount(count + 1);
  }

  return (
    <div>
      <p>Räknare: {count}</p>
      <button onClick={handleClick}>+3</button>
    </div>
  );
}

// Bugg 2: Listan uppdateras inte i gränssnittet
function BrokenList() {
  const [items, setItems] = useState(["Äpple", "Banan"]);

  function addItem() {
    items.push("Citron");
    setItems(items);
  }

  return (
    <div>
      <p>Antal: {items.length}</p>
      <button onClick={addItem}>Lägg till Citron</button>
      <ul>
        {items.map((item, i) => (
          <li key={i}>{item}</li>
        ))}
      </ul>
    </div>
  );
}

// Bugg 3: Profilen tappar egenskaper vid uppdatering
function BrokenProfile() {
  const [profile, setProfile] = useState({
    name: "Anna",
    age: 25,
    city: "Stockholm",
  });

  return (
    <div>
      <p>
        {profile.name}, {profile.age} år, {profile.city}
      </p>
      <button onClick={() => setProfile({ name: "Erik" })}>Byt till Erik</button>
    </div>
  );
}

// Bugg 4: Input-fältet uppdateras inte
function BrokenInput() {
  const [text, setText] = useState("Hej");

  return (
    <div>
      <input value={text} />
      <p>Du skrev: {text}</p>
    </div>
  );
}

function App() {
  return (
    <div>
      <h2>Bugg 1: FastCounter</h2>
      <FastCounter />
      <h2>Bugg 2: BrokenList</h2>
      <BrokenList />
      <h2>Bugg 3: BrokenProfile</h2>
      <BrokenProfile />
      <h2>Bugg 4: BrokenInput</h2>
      <BrokenInput />
    </div>
  );
}

export default App;
```

1. Kopiera koden till `App.jsx` och starta appen.
2. Testa varje component och se vad som går fel.
3. Fixa buggarna en i taget. Testa efter varje fix.

## Förväntat resultat

- **FastCounter:** Klick på "+3" ökar räknaren med 3 varje gång.
- **BrokenList:** Knappen lägger till "Citron" och listan uppdateras i gränssnittet.
- **BrokenProfile:** Att byta till Erik behåller ålder och stad.
- **BrokenInput:** Man kan skriva i input-fältet och texten uppdateras.

## Tips

<details>
<summary>Ledtråd 1</summary>

Bugg 1 handlar om att `count` har samma värde i alla tre anrop — React batchar uppdateringar. Bugg 2 handlar om mutation. Bugg 3 handlar om att skriva över hela objektet. Bugg 4 handlar om saknad `onChange`.

</details>

<details>
<summary>Ledtråd 2</summary>

Lösningar:

1. Använd funktionsformen: `setCount(prev => prev + 1)` tre gånger
2. Skapa en ny array: `setItems([...items, "Citron"])`
3. Sprid befintliga värden: `setProfile({ ...profile, name: "Erik" })`
4. Lägg till `onChange`: `<input value={text} onChange={(e) => setText(e.target.value)} />`

</details>
