# Fixa JSX-felen (Grund)

## Mål

Öva på att identifiera och fixa vanliga JSX-fel.

## Förkunskaper

- [Introduktion till React och JSX](../../documents/01-introduktion-react-jsx.md)

## Instruktioner

Kopiera in följande kod i din `App.jsx`. Den innehåller flera JSX-fel. Hitta och fixa alla.

```jsx
function App() {
  const title = "Min sida"
  const imageUrl = "https://i.pravatar.cc/150"

  return (
    <h1 class="title">{title}</h1>
    <img src={imageUrl} alt="Profilbild">
    <p>Välkommen till min sida.</p>
    <br>
    <label for="name">Namn:</label>
    <input type="text" id="name">
  )
}

export default App
```

1. Försök rendera komponenten — du ska se ett felmeddelande.
2. Läs felmeddelandet och fixa det första felet.
3. Fortsätt tills alla fel är fixade och sidan renderas korrekt.

## Förväntat resultat

En sida som visar en rubrik, en bild, en välkomsttext, och ett input-fält — allt utan fel i konsolen.

## Tips

<details>
<summary>Ledtråd 1</summary>
Det finns sex fel att hitta. Tänk på: rot-element, HTML-attribut som heter annorlunda i JSX, och self-closing tags.
</details>

<details>
<summary>Ledtråd 2</summary>
I JSX: `class` → `className`, `for` → `htmlFor`. Taggar som `img`, `br`, `input` måste sluta med `/>`.
</details>
